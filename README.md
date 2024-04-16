# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
Developed By: Shaik Sameer Basha
Reg. No: 212222240093
```
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Passenger Details
# Replace 'AirPassengers.csv' with the path to your data file
data = pd.read_csv('AirPassengers.csv')

# Ensure that the 'Month' column is in datetime format
data['Month'] = pd.to_datetime(data['Month'])
data['Year'] = data['Month'].dt.year
# Set the 'Month' column as the index
data.set_index('Month', inplace=True)
data.head()

# Plotting the Data
ar1 = data['Year'].values.reshape(-1, 1)
ma1 = data['#Passengers'].values.reshape(-1, 1)
plt.plot(ar1,ma1,label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

# Perform time series decomposition
period=13
result = seasonal_decompose(data,model='multiplicative', period=period)

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the original time series
plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['#Passengers'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()
```
### OUTPUT:

#### FIRST FIVE ROWS:

![5 1](https://github.com/shaikSameerbasha5404/TSA_EXP5/assets/118707756/3f440bdc-7ae2-4812-8c57-1e92ad87511f)


#### PLOTTING THE DATA:

![5 2](https://github.com/shaikSameerbasha5404/TSA_EXP5/assets/118707756/943352de-4815-4d4a-932c-522d4d76ea74)


#### SEASONAL PLOT REPRESENTATION :

![5 3](https://github.com/shaikSameerbasha5404/TSA_EXP5/assets/118707756/3821cc80-3d0a-4cdf-8bda-ae08b154cd2b)


#### TREND PLOT REPRESENTATION :

![5 4](https://github.com/shaikSameerbasha5404/TSA_EXP5/assets/118707756/9805e60a-fe8b-4cf2-badd-29a9c45f9074)



#### OVERAL REPRESENTATION:

![5 5](https://github.com/shaikSameerbasha5404/TSA_EXP5/assets/118707756/bea20ee5-54dd-4c06-b937-1b28c5fb5636)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
