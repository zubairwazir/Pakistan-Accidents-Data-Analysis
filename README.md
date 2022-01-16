<div class="cell code" data-execution_count="1">

``` python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib as mpl
```

</div>

<div class="cell code" data-execution_count="39">

``` python
total_accidents = pd.read_csv('total_accidents.csv', index_col="year", parse_dates=True)
total_accidents.head()
```

<div class="output execute_result" data-execution_count="39">

``` 
         total_accidents  fatal  non_fatal  people_killed  people_injured  \
year                                                                        
2009-10             9747   4378       5369           5280           11173   
2010-11             9723   4280       5443           5271           11383   
2011-12             9140   3966       5174           4758           10145   
2012-13             8988   3884       5104           4719            9710   
2013-14             8359   3500       4859           4348            9777   

         total_vehicles  
year                     
2009-10           10496  
2010-11           10822  
2011-12            9986  
2012-13            9876  
2013-14            9423  
```

</div>

</div>

<div class="cell code" data-execution_count="49">

``` python
provincial_accidents = pd.read_csv('provincial_accidents.csv', index_col="year", parse_dates=True)
provincial_accidents.head()
```

<div class="output execute_result" data-execution_count="49">

``` 
         total_accidents  fatal  non_fatal  people_killed  people_injured  \
year                                                                        
2009-10             5344   2590       2754           3083            5856   
2010-11             5420   2591       2829           3167            5809   
2011-12             4990   2361       2629           2888            5071   
2012-13             4587   2213       2374           2692            4515   
2013-14             3696   1717       1979           2145            3941   

         total_vehicles province  
year                              
2009-10            5344   Punjab  
2010-11            5420   Punjab  
2011-12            4990   Punjab  
2012-13            4587   Punjab  
2013-14            3696   Punjab  
```

</div>

</div>

<div class="cell code" data-execution_count="4">

``` python
provincial_accidents.tail()
```

<div class="output execute_result" data-execution_count="4">

``` 
         total_accidents  fatal  non_fatal  people_killed  people_injured  \
year                                                                        
2015-16              244    120        124            140             209   
2016-17              226    127         99            129             124   
2017-18              259    157        102            167             162   
2018-19              238    127        111            136             134   
2019-20              189    111         78            118             121   

         total_vehicles   province  
year                                
2015-16             244  Islamabad  
2016-17             216  Islamabad  
2017-18             259  Islamabad  
2018-19             239  Islamabad  
2019-20             189  Islamabad  
```

</div>

</div>

<div class="cell code" data-execution_count="36">

``` python
all_accidents = pd.read_csv('all_accidents.csv')
total_accidents = pd.read_csv('total_accidents.csv')
provincial_accidents = pd.read_csv('provincial_accidents.csv')
```

</div>

<div class="cell code" data-execution_count="37">

``` python
plt.figure(figsize=(20,7))
plt.style.use('seaborn-darkgrid')
sns.lineplot(x='year', y='total_accidents', hue='province',  data=provincial_accidents) #style='region'
```

<div class="output execute_result" data-execution_count="37">

    <AxesSubplot:xlabel='year', ylabel='total_accidents'>

</div>

</div>

<div class="cell code" data-execution_count="38">

``` python
plt.figure(figsize=(15, 7))
sns.barplot(x='year', y='total_accidents', data=total_accidents)
plt.show()
```

<div class="output display_data">

![](3456b7185d62a199eead7059c8588a5aeb177f31.png)

</div>

<div class="output display_data">

![](5e79012d3526ee70355b570327b4a80297b35bcf.png)

</div>

</div>

<div class="cell code" data-execution_count="8">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x='year', y='total_accidents', hue=provincial_accidents.province, data=provincial_accidents)
plt.show()
```

<div class="output display_data">

![](071c1e25be2e022485fc41b8f87fb54a5d5689e4.png)

</div>

</div>

<div class="cell code" data-execution_count="9">

``` python
sns.catplot(x='year', y='total_accidents', data=provincial_accidents, col='province')
```

<div class="output execute_result" data-execution_count="9">

    <seaborn.axisgrid.FacetGrid at 0x1546d42eb80>

</div>

</div>

<div class="cell code" data-execution_count="10">

``` python
total_accidents.hist(bins=20, figsize=(20,20))
plt.show()
```

<div class="output display_data">

![](aed78fd57cc7d05970ba727bf1f2fab76f143645.png)

</div>

<div class="output display_data">

![](8a7fc46ae7df9da8c471a0b16c7bc601ae679faf.png)

</div>

</div>

<div class="cell code" data-execution_count="11">

``` python
plt.figure(figsize=(15,7))
sns.distplot(total_accidents['total_accidents'], bins=5)
plt.show()
```

<div class="output stream stderr">

    C:\Users\zubai\anaconda3\lib\site-packages\seaborn\distributions.py:2557: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)

</div>

<div class="output display_data">

![](fabf1a29df4130f64cb17c57059ac6844675025c.png)

</div>

</div>

<div class="cell code" data-execution_count="12" data-scrolled="false">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.total_accidents, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](071c1e25be2e022485fc41b8f87fb54a5d5689e4.png)

</div>

</div>

<div class="cell code" data-execution_count="13">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.fatal, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](cf86c81c6ebfa23048ba61119dee63bc84df5016.png)

</div>

</div>

<div class="cell code" data-execution_count="14">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.non_fatal, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](19a09f9a391cd8c3a9005937c5cf7a014ba461c1.png)

</div>

</div>

<div class="cell code" data-execution_count="15">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.people_killed, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](df051127f3ed20035104bb43e3a29b4cbca3f4fd.png)

</div>

</div>

<div class="cell code" data-execution_count="16">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.people_injured, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](f49226a12cc157eed031fa639cd3badae375b6c4.png)

</div>

</div>

<div class="cell code" data-execution_count="17">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.year, y=provincial_accidents.total_vehicles, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](c31747066f5e7aa210380d6529bb56cec34aa3d8.png)

</div>

</div>

<div class="cell code" data-execution_count="18">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.total_accidents, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](d71d3295362c5c0988f9a6297241970338e5ad42.png)

</div>

</div>

<div class="cell code" data-execution_count="19">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.fatal, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](eb2031672f5a4d3dc56d5d4693e0cf1880f96318.png)

</div>

</div>

<div class="cell code" data-execution_count="20">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.non_fatal, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](bb5a14dfb655776bd65e10140d62f4ceb87fa08e.png)

</div>

</div>

<div class="cell code" data-execution_count="21">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.people_killed, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](80c9eeff85b62a5d72af42e76a434bccedcd0459.png)

</div>

</div>

<div class="cell code" data-execution_count="22">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.people_injured, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](b3b296cf446cb03c34ceaa6a59096172867e7111.png)

</div>

</div>

<div class="cell code" data-execution_count="23">

``` python
plt.figure(figsize=(15,7))
sns.barplot(x=provincial_accidents.province, y=provincial_accidents.total_vehicles, hue=provincial_accidents.province)
sns.despine()
plt.show()
```

<div class="output display_data">

![](661afb03d01dc3bc3d9c9a29d2750d321352d433.png)

</div>

</div>

<div class="cell code" data-execution_count="24">

``` python
plt.figure(figsize=(20, 10))
sns.catplot('total_accidents', col='province', col_wrap=5, data=provincial_accidents, kind='count', height=5, aspect=1)
plt.show()
```

<div class="output stream stderr">

    C:\Users\zubai\anaconda3\lib\site-packages\seaborn\_decorators.py:36: FutureWarning: Pass the following variable as a keyword arg: x. From version 0.12, the only valid positional argument will be `data`, and passing other arguments without an explicit keyword will result in an error or misinterpretation.
      warnings.warn(

</div>

<div class="output display_data">

    <Figure size 2000x1000 with 0 Axes>

</div>

<div class="output display_data">

![](5ef374ab9519432fbd3af746e903fa38a035ee46.png)

</div>

</div>

<div class="cell code">

``` python
```

</div>
