# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import Required Libraries

2.Load and Explore the Dataset

3.Select Features for Clustering

4.Calculate WCSS (Within-Cluster Sum of Squares)

5.Plot the Elbow Graph

6.Apply K-Means Clustering with Optimal Clusters

7.Segment Data Based on Clusters

8.Visualize the Clusters

9.Analyze and Interpret Results

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SONU S 
RegisterNumber: 212223220107  
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
print(data.head())

data.info()

print(data.isnull().sum())

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
plt.show()
y_pred = km.predict(data.iloc[:, 3:])
print(y_pred)

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
![image](https://github.com/user-attachments/assets/c52fc95d-1983-498c-a3a2-1f46ee25e867)
![image](https://github.com/user-attachments/assets/abfc0670-2064-4532-8400-c4c47af30c3f)
![image](https://github.com/user-attachments/assets/7be21c89-ae71-4465-a93e-a2373d666824)
![image](https://github.com/user-attachments/assets/e4186479-a5ab-4052-8ef6-4d47beac5c87)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
