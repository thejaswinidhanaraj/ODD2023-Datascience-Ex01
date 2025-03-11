# Ex-01_DS_Data_Cleansing


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE and OUTPUT
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/25376e42-4833-4534-a428-e4f69ad259a0)
```
df.head(6)
```
![image](https://github.com/user-attachments/assets/25de4adc-74e1-4b80-a9f4-a9e8bf0bc160)
```
df.tail(6)
```
![image](https://github.com/user-attachments/assets/94ae9218-813d-4c53-bb96-a4fac1bb88dd)
```
df.isnull()
```
![image](https://github.com/user-attachments/assets/e0d1e4b6-d8ec-4b63-93ab-3b1b8fb0f6f3)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/970d9347-5a36-4569-b342-73a684a7fb67)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/917a5e69-563f-487e-8845-fd56f1ae4826)
```
df.shape
```
![image](https://github.com/user-attachments/assets/5fe717e3-7807-466f-8239-101868a54158)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/35dc2ca6-86c2-4d30-923f-b1b2e8952c6a)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/dba3c63f-1cd9-48b7-9893-be9b17bbd5b9)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/018b2c7e-35ac-44ac-9836-e34c1198484c)
```
df.fillna({'GENDER' : 'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':'98','M2':'87','M3':'76','M4':'92','TOTAL':'305','AVG':'89'})
```
![image](https://github.com/user-attachments/assets/9be61444-a4d4-4490-8bc3-0c48bd87ab67)

## IQR:
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/eb230589-bdbf-4546-a9ad-dd3f23d8c93e)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/801f35bb-42dc-477f-8954-765ffa72c2f0)
```
ir.shape
```
![image](https://github.com/user-attachments/assets/32c71183-5d18-49d5-a474-9a4fb202a328)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/83fe0d7b-57ff-423f-993a-a6c5c8b9e3a7)
```
Q1=ir.sepal_width.quantile(0.25)
Q2=ir.sepal_width.quantile(0.50)
Q3=ir.sepal_width.quantile(0.75)
iqr=Q3-Q1
iqr
```
![image](https://github.com/user-attachments/assets/d90f0a0e-6200-432b-bd63-0877756d0239)
```
outlier=ir[((ir.sepal_width<(Q1-1.5*iqr))|(ir.sepal_width>(Q3+1.5*iqr)))]
outlier['sepal_width']
```
![image](https://github.com/user-attachments/assets/9145f503-2b34-4f30-8f5a-b8e078dbfafe)
```
values=ir[~((ir.sepal_width<(Q1-1.5*iqr))|(ir.sepal_width>(Q3+1.5*iqr)))]
values['sepal_width']
```
![image](https://github.com/user-attachments/assets/cb9ba319-a96a-494c-80f5-2358ca5363a8)
```
sns.boxplot(x='sepal_width',data=values)
```
![image](https://github.com/user-attachments/assets/d4285a1a-9ee9-40f8-8daa-20d2e3b5764e)

## Z-SCORE:
```
import scipy.stats as stats
import numpy as np
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
![image](https://github.com/user-attachments/assets/90f1184c-02b8-484b-8073-75402d18f64b)
```
ir=ir[z<0.8]
ir
```
![image](https://github.com/user-attachments/assets/6e07376f-7500-4364-9f49-e4fcdb9f1c39)


