# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
## EXPLANATION

An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out).Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.Most machine learning algorithms do not work well in the presence of outlier. So it is desirable to detect and remove outliers.Outliers are highly useful in anomaly detection like fraud detection where the fraud transactions are very different from normal transactions.

## ALGORITHM

## STEP 1
Read the given Data

## STEP 2
Get the information about the data

## STEP 3
Detect the Outliers using IQR method and Z score

## STEP 4
Remove the outliers

## STEP 5
Plot the datas using Box Plot

## CODE
(1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

```
import pandas as pd import numpy as np import seaborn as sns

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/bhp.csv") df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df) q1 = df['price_per_sqft'].quantile(0.25) q3 = df['price_Aper_sqft'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))] df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)`

(3) Examine price_per_sqft column and use zscore of 3 to remove outliers. from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft'])) df2 = df[(z<3)] df2

print(df2.shape) sns.boxplot(x="price_per_sqft",data=df2)

(4)(i) For the data set height_weight.csv detect weight outliers using IQR method df3 = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/height_weight.csv") df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25) q3 = df3['weight'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))] df4

df4.shape

<img width="276" alt="2 10" src="https://user-images.githubusercontent.com/93427345/191421710-aad50409-e824-4ad5-8c87-665de18fdbbb.png">
sns.boxplot(x="weight",data=df4) (4)(ii) For the data set height_weight.csv detect height outliers using IQR method sns.boxplot(x="height",data=df3)

q1 = df3['height'].quantile(0.25) q3 = df3['height'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))] df5

df5.shape

sns.boxplot(x="height",data=df5)
```

## OUTPUT
(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

## Dataset
<img width="448" alt="pra 1" src="https://user-images.githubusercontent.com/128135934/232383051-3b614dc7-54e4-4ee1-811d-bcb86baa0911.png">

## Dataset head
<img width="455" alt="pra2" src="https://user-images.githubusercontent.com/128135934/232383306-fa4bbc03-6dd0-42c4-9b70-7e2ac1744d97.png">

## Dataset info
<img width="272" alt="pra 3" src="https://user-images.githubusercontent.com/128135934/232384146-7a2e476d-800d-4c8b-8473-5d216099c72d.png">

## Data describe
<img width="450" alt="pra4" src="https://user-images.githubusercontent.com/128135934/232384288-8b1bed43-d8ff-4686-b19d-b708eebf05d8.png">

## Null values
<img width="125" alt="pra 5" src="https://user-images.githubusercontent.com/128135934/232384475-33953d5c-081c-4e9d-a12a-4f323c837ae4.png">

## Dataset shape
<img width="63" alt="pra6" src="https://user-images.githubusercontent.com/128135934/232384716-e258b47e-e072-4ed4-b83f-e94cf472583c.png">

## Box plot of price_per_sqft column with outliers
<img width="328" alt="pra7" src="https://user-images.githubusercontent.com/128135934/232385442-152bc443-5386-4dc9-a6ff-9c151b24a804.png">

## price_per_sqft - Dataset after removing outliers
<img width="455" alt="pra8" src="https://user-images.githubusercontent.com/128135934/232385831-6ddd741a-84ff-44d6-b21a-c39c5102a7bc.png">

## price_per_sqft - Shape of Dataset after removing outliers
<img width="67" alt="pra9" src="https://user-images.githubusercontent.com/128135934/232386250-952f7d81-eb69-477d-a3d9-1720d6463f5e.png">

## Box Plot of price_per_sqft column without outliers
<img width="276" alt="pra10" src="https://user-images.githubusercontent.com/128135934/232386717-411f04ec-d9ff-49f2-89cc-3199b9f4932a.png">

## Examine price_per_sqft column and use zscore of 3 to remove outliers. Dataset after removal of outlier using z score
<img width="457" alt="pra11" src="https://user-images.githubusercontent.com/128135934/232387029-323578e8-b3f3-4b9d-8ada-b4c2305b57c3.png">

## Shape of Dataset after removal of outlier using z score
<img width="70" alt="pra12" src="https://user-images.githubusercontent.com/128135934/232387303-4136d2e4-ec5d-495c-8841-5c652267cef2.png">

## price_per_sqft column after removing outliers
<img width="320" alt="pra13" src="https://user-images.githubusercontent.com/128135934/232387562-77dff688-6528-40f5-9075-f53ff309212b.png">

## (4) For the data set height_weight.csv detect weight and height outliers using IQR method Dataset
<img width="211" alt="pra14" src="https://user-images.githubusercontent.com/128135934/232387886-e066676b-7334-4b55-9e52-d89b8826f902.png">

## Datahead
<img width="191" alt="pra15" src="https://user-images.githubusercontent.com/128135934/232388150-8395d874-47ac-44fe-864e-a11bb2fd1177.png">

## Dataset info
<img width="221" alt="pra16" src="https://user-images.githubusercontent.com/128135934/232388523-5c41217b-1501-498e-8e75-334c9bb8349d.png">

## Dataset describe
<img width="197" alt="pra17" src="https://user-images.githubusercontent.com/128135934/232388801-29b2d95e-3b74-4943-817b-37fca0358e92.png">

## Null values
<img width="80" alt="pra18" src="https://user-images.githubusercontent.com/128135934/232389057-8589331b-69ae-4dbe-9898-87609d751c07.png">

## Dataset Shape
<img width="70" alt="pra 19" src="https://user-images.githubusercontent.com/128135934/232389238-8494ed9c-93ad-4fd6-9acb-de294f555e98.png">

## Weight - With outlier
<img width="273" alt="pra 20" src="https://user-images.githubusercontent.com/128135934/232389775-a8af4e22-a412-452d-9d93-4970b6ed773c.png">

## Weight - Dataset after removing Outliers using IQR method
<img width="221" alt="pra21" src="https://user-images.githubusercontent.com/128135934/232390110-11e4f6e6-6e10-4f82-abd3-55f2d55cda17.png">

## Weight - Shape of Dataset after removing Outliers using IQR method
<img width="65" alt="pra 22" src="https://user-images.githubusercontent.com/128135934/232390439-a26529a2-a5d5-4a1d-9a22-c78af43dfb04.png">

## Weight - Without Outliers using IQR method
<img width="341" alt="pra 23" src="https://user-images.githubusercontent.com/128135934/232390874-7d0cdc8c-1282-4019-8ee6-66624b5ea0b9.png">

## Height - With outliers
<img width="282" alt="pra 24" src="https://user-images.githubusercontent.com/128135934/232391291-98463adb-5ac7-4c2e-8a4f-a84bf817f69b.png">

## Height - Dataset after removing Outliers using IQR method
<img width="210" alt="pra 25" src="https://user-images.githubusercontent.com/128135934/232391499-d0da027a-5214-442e-b8e8-c4d44e2b374b.png">

## Height - Shape of Dataset after removing Outliers using IQR method
<img width="80" alt="pra 26" src="https://user-images.githubusercontent.com/128135934/232392014-0e08f28d-1e25-46e6-be48-2cf43e4b3130.png">

## Height - Without Outliers using IQR method
<img width="341" alt="pra 27" src="https://user-images.githubusercontent.com/128135934/232392673-65a19808-303f-4d05-9453-50562c94e233.png">

### RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.






