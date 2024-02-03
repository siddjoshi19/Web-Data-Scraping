# Web-Data-Scraping

### Porject Overview
<p>This Project is focus on data web scrpping. Here we are going to pull the data from the website named <b>Wikipedia</b>. 
This is a good practice project for web scraping using pandas librabry in python. Here we are going to pull the the table data from wikipedia page. The table contains the data about the list of millioners in the different country.</p>

### Data Source
<p>URL: https://en.wikipedia.org/wiki/List_of_countries_by_number_of_millionaires</p>

### Tools
<li>Jupyter Notebook</li>
<li>Pandas library</li>
<li>BeatifulSoap </li>
<li>Excel</li>

### Imports library
<p>First we are going to import the BeautifulSoup and requests library in Jupyter Notebook</p>

```python

from bs4 import BeautifulSoup
import requests
```

### Data Read From URL
<p>Now We are  goint to pass the URL and save it in a variable and read all the data</p>

```python

url= 'https://en.wikipedia.org/wiki/List_of_countries_by_number_of_millionaires'
page = requests.get(url)
soup = BeautifulSoup(page.text,'html')

```

### Data Store in Pandas Dataframe
<p>Here we select the data table and put the each raw value respect to column name. 
  For that first we pull the header of the table.  
  After importing pandas we creatd new dataframe and store each raw value in the dataframe.</p>

  ```python

table= soup.find_all('table')[1]
title = table.find_all('th')
title_name =[name.text.strip() for name in title]


import pandas as pd
df = pd.DataFrame(columns = title_name)
df


column_data = table.find_all('tr')


for data in column_data[1:]:
    individual_raw_data = data.find_all('td')
    clean_raw_data = [data.text.strip() for data in individual_raw_data]
    
    length = len(df)
    df.loc[length]= clean_raw_data
df

#to Convert into CSV file
df.to_csv
```




