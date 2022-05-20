#	Overview of Project 

## Purpose 
To Provide analysis on ride, driver and fare data based on the city types - Rural ,Suburban and Urban.Help in providing visualizations to Pyber so that they can predict trends and see patterns from the data analysis.

## Resources 
Data Source - city_data.csv , ride_data.csv
Software - Python 3.8.5, Jupiter Notebook 6.1.4
Following are the steps to extract data from the csv resources provided to us.
1. We read the city_data.csv and the ride_data.csv files and transform into data frames using Pandas. 
2. city_data_df & ride_data_df contain information about the names of the cities & drivers  and information of the rides in each of the cities respectively.
3. Using the two DataFrame we merge them together on the common column , new DataFrame is named as “pyber_data_df”
4. The columns are “city” , “data”, “fare”, “ride_id”, “driver_count”, and  type i.e [Rural,Urban,Suburban]. 
5. Below is the snippet of DataFrame - 

<img width="389" alt="merged_df" src="https://user-images.githubusercontent.com/98556229/169404579-b7443d16-b900-486c-9c19-cbe95e893d09.png">


## Deliverable #1 
We analyze the dataframe to get a new DataFrame  with columns - 
* Total Rides - pyber_data_df.groupby('type')["ride_id"].count() - groupby on “type” & “ride_id”  to get the count from the pyber_data_df 
* Total Drivers - city_data_df.groupby('type')["driver_count"].sum() - groupby on “type” & “driver_count” to get the sum from the pyber_data_df
* Total Fares - pyber_data_df.groupby("type")["fare"].sum() - groupie on “type” & “fare” to get the sum from pyber_data_df 
* Average Fare per Ride - total_fares / total_ride_ea_city 
* Average Fare per Driver - total_fares/total_drivers
* Indexed on the type of City - Rural , Suburban & Urban.
* Formatting the columns. - pyber_summary_df

<img width="739" alt="pyber_summary_df" src="https://user-images.githubusercontent.com/98556229/169404605-6f20e5c2-0aff-4685-ab9b-4bbf3f801b16.png">
.png

##  Deliverable #2.
* From the summary dataFrame above we create a new DataFrame - using groupby() showing the sum of the fares for each date where the indices are the city type and date.
* We Reset the index on the DataFrame. So that we can create a new pivot table with “Date” as index and “type” as columns. As shown below - 
    * total_fares_city_pivot_table = sum_fare_for_each_date.pivot(columns='type',values='fare',index=['date'])
    * The re-arranged DataFrame was then filtered to contain data between the dates 1st January 2019 through 30th April 2019.



<img width="366" alt="pivot_table" src="https://user-images.githubusercontent.com/98556229/169404637-833ddebb-143f-4734-be5e-ef3e64817639.png">

There are null values in the dataframe because some data is not present due to no rides in some city types during those dates. We create a new DataFrame with using Resample on weeks for each week . 
 

The data from this DataFrame was then used to create the map, using df.plot()


![PyBer_fare_summary](https://user-images.githubusercontent.com/98556229/169404766-76f3f1bc-f475-48f1-ab00-6be25796a1dd.png)

From the above plot we can infer that - 
1. Relations of Ride Fares in different cities for a certain period of time.
2. The maximum Fares for different types of cities 
    1. Urban cities little over $2000.
    2. Suburban cities close to $1000.
    3. Rural cities lose to $250.
Urban cities average is about 2 times more than suburban cities & about 8 times more than Rural cities.
3. Urban cities - peaked in the Fares in the months of maximum in Feb end, March Month and also in April month.
4. Suburban cities - peaked in February , there was a dip in month of April.
5. Rural cities - peaked in Feb  and April and it fairly looks like a flat line.

Below is the summary dataframe - pyber_summary_df

<img width="739" alt="pyber_summary_df" src="https://user-images.githubusercontent.com/98556229/169404675-8f72e11d-6191-4ed4-acc0-46b128e14b16.png">




Observations - 
1. Total Fares earned in “Urban cities” is  $39,854.38 is 2 times that of the “Suburban cities” which is $19,356.33 showing they have the highest demand
2. Similar to total fares there is a huge disparity between the total rides for Rural and Urban cities (almost 9 times ) and Suburban to urban cities (almost 2 times).
3. Comparing Total Drivers in each city - Rural is 78  whereas Urban cities is 2405 which is almost 30 times of Rural cities, & 5 times of Suburban cities.
4. Its also evident that Average Fare per driver is very less in Urban when compare to Rural / Suburban cities. 
5. Rural cities have highest average Fare per ride.
6. The data shows a relationship where Revenue and driver varies high or low with type of city, while average fare per driver is inversely proportional.

## Summary

1. Since "Total Drivers" is fewer in Rural and Suburban may be giving more perks or some kind of incentives to encourage them to take up the Driver post at the PyBer rideshare will help increase the overall totals of Drivers.

2. With #1 as more Drivers take up , the “Total Rides” will also increase and improve in the Rural and Suburban cities and the “Total Fares” will improves cause decreasing the “Average Fare per Ride”, which will be great win for both customer and the company. Less rides could be reason due to longer rides or bad road conditions etc. 

3. Also, “Average Fare per Driver” is pretty low for Urban cities compared to Rural and Suburban cities, so if we provide some extra incentive or extra pay for the extra rides they are doing to increase the Revenue of the company.


