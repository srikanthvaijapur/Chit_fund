

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```


```python
chit_data = pd.read_excel("chit fund exercise.xlsx")
```


```python
chit_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Contribution</th>
      <th>Amount won by the bidder</th>
      <th>Chit fund organizer commission</th>
      <th>Net amount recd by Bid winner</th>
      <th>Amount returned to everyone in the group</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2000</td>
      <td>42000</td>
      <td>2500</td>
      <td>39500</td>
      <td>320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2000</td>
      <td>45000</td>
      <td>2500</td>
      <td>42500</td>
      <td>200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2000</td>
      <td>48000</td>
      <td>2500</td>
      <td>45500</td>
      <td>80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
    </tr>
  </tbody>
</table>
</div>




```python
print("chit_size:",chit_data.shape)
```

    chit_size: (25, 6)
    

By data,There are 25 unique chit funders and as per the rules only once the money can be borrowed.first thing totol money calculated by each person in each month is given by


```python
chit_data["total Contribution"] = chit_data["Contribution"] - chit_data["Amount returned to everyone in the group"]

```


```python
chit_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Contribution</th>
      <th>Amount won by the bidder</th>
      <th>Chit fund organizer commission</th>
      <th>Net amount recd by Bid winner</th>
      <th>Amount returned to everyone in the group</th>
      <th>total Contribution</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2000</td>
      <td>42000</td>
      <td>2500</td>
      <td>39500</td>
      <td>320</td>
      <td>1680</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2000</td>
      <td>45000</td>
      <td>2500</td>
      <td>42500</td>
      <td>200</td>
      <td>1800</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2000</td>
      <td>48000</td>
      <td>2500</td>
      <td>45500</td>
      <td>80</td>
      <td>1920</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
    </tr>
  </tbody>
</table>
</div>



Calculating overall Contribution contributed by each member of the chit fund throughout 25 months. 
overall amount contributed by each member = Sum of (Contribution of every month(2000) - Amount returned) for 25 months


```python
total =chit_data["total Contribution"].sum()
total
```




    43800



Calculating Return/Net Profit obtained by the Bid Winners for every month 
Return = Net amount received by a participant - total amount contributed by a participant



```python
chit_data["return"] = chit_data["Net amount recd by Bid winner"] - total

```


```python
chit_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Contribution</th>
      <th>Amount won by the bidder</th>
      <th>Chit fund organizer commission</th>
      <th>Net amount recd by Bid winner</th>
      <th>Amount returned to everyone in the group</th>
      <th>total Contribution</th>
      <th>return</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
      <td>-6300</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2000</td>
      <td>42000</td>
      <td>2500</td>
      <td>39500</td>
      <td>320</td>
      <td>1680</td>
      <td>-4300</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2000</td>
      <td>45000</td>
      <td>2500</td>
      <td>42500</td>
      <td>200</td>
      <td>1800</td>
      <td>-1300</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2000</td>
      <td>48000</td>
      <td>2500</td>
      <td>45500</td>
      <td>80</td>
      <td>1920</td>
      <td>1700</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
      <td>-6300</td>
    </tr>
  </tbody>
</table>
</div>



Calculating Return Percentage obtained by the Bid Winners for every month 

Return percentage = (Amount returned to everyone in the group / Total amount invested) X 100



```python
chit_data["ret%"] = (chit_data["return"]/total)*100

```


```python
chit_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Contribution</th>
      <th>Amount won by the bidder</th>
      <th>Chit fund organizer commission</th>
      <th>Net amount recd by Bid winner</th>
      <th>Amount returned to everyone in the group</th>
      <th>total Contribution</th>
      <th>return</th>
      <th>ret%</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
      <td>-6300</td>
      <td>-14.383562</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2000</td>
      <td>42000</td>
      <td>2500</td>
      <td>39500</td>
      <td>320</td>
      <td>1680</td>
      <td>-4300</td>
      <td>-9.817352</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2000</td>
      <td>45000</td>
      <td>2500</td>
      <td>42500</td>
      <td>200</td>
      <td>1800</td>
      <td>-1300</td>
      <td>-2.968037</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2000</td>
      <td>48000</td>
      <td>2500</td>
      <td>45500</td>
      <td>80</td>
      <td>1920</td>
      <td>1700</td>
      <td>3.881279</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2000</td>
      <td>40000</td>
      <td>2500</td>
      <td>37500</td>
      <td>400</td>
      <td>1600</td>
      <td>-6300</td>
      <td>-14.383562</td>
    </tr>
  </tbody>
</table>
</div>



Answers

Q1. What is the Annualized  Return of the person who bids in the last month ?

Formula for Annualized Return which I was able to procure after reading on internet

((1 + return%)^(12/months the chit fund is hold) - 1) * 100 


```python
chit_data.iloc[24]
```




    Month                                          25.000000
    Contribution                                 2000.000000
    Amount won by the bidder                    50000.000000
    Chit fund organizer commission               2500.000000
    Net amount recd by Bid winner               47500.000000
    Amount returned to everyone in the group        0.000000
    total Contribution                           2000.000000
    return                                       3700.000000
    ret%                                            8.447489
    Name: 24, dtype: float64




```python
((((1 + (chit_data["ret%"][24])/100)) ** (12/25)) - 1) * 100
```




    3.969357358648673



Annualized return of the person who bids in last month is: 3.97%

Q2. What is the Annualized Return of the person who bids in the first month ?


```python
chit_data.iloc[0]
```




    Month                                           1.000000
    Contribution                                 2000.000000
    Amount won by the bidder                    40000.000000
    Chit fund organizer commission               2500.000000
    Net amount recd by Bid winner               37500.000000
    Amount returned to everyone in the group      400.000000
    total Contribution                           1600.000000
    return                                      -6300.000000
    ret%                                          -14.383562
    Name: 0, dtype: float64




```python
((((1 + (chit_data["ret%"][0])/100)) ** (12/25)) - 1) * 100
```




    -7.183019602665885



Annualized return of the person who bids in first month is: -7.18%


Q3. Write an Python script which calculates the annualized return of chit fund participant? - Show the Return % for each month's bid winner.


Return percentages of each month's bid winners.



```python
chit_data["ret%"]
```




    0    -14.383562
    1     -9.817352
    2     -2.968037
    3      3.881279
    4    -14.383562
    5     -9.817352
    6     -7.534247
    7     -5.251142
    8    -14.383562
    9     -9.817352
    10    -2.968037
    11     3.881279
    12   -14.383562
    13    -9.817352
    14    -7.534247
    15    -7.534247
    16   -12.100457
    17    -9.817352
    18    -2.968037
    19    -2.968037
    20    -5.251142
    21    -0.684932
    22     1.598174
    23     3.881279
    24     8.447489
    Name: ret%, dtype: float64




```python

```
