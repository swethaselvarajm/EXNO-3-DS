## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/b54a2736-390b-43e9-b344-4c93db11a84a)

```
#ORDINAL ENCODER
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/d10d1baa-33cb-4f66-acf6-829b0c8553d5)

```
df['bo_2']=e1.fit_transform(df[['ord_2']])
df
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/a25e1894-112d-426c-92eb-bcb105114a0d)

```
#LABEL ENCODER
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/c42d12e6-a423-490b-9beb-a42e020292b7)

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))

df2=pd.concat([df,enc],axis=1)
df2
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/b2aebd85-aa28-4601-8956-2abe56ca3ab2)

```
pd.get_dummies(df2,columns=['nom_0'])
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/efd67c26-2126-4997-be32-0594ebfcc9c4)

```
from category_encoders import  BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/bb215007-542e-4f12-973a-99f61f691c6c)

```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/1fde8437-1705-422d-bd4a-5db97537c9c3)

```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
cc
```
![image](https://github.com/swethaselvarajm/EXNO-3-DS/assets/119525603/7571dbf0-ef8d-4879-851e-16cea5b978c3)


# RESULT:
Thus, performing Feature Encoding and Transformation process for the given data set is completed.

       
