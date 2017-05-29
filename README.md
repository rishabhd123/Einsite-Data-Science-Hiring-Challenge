# Einsite-Data-Science-Hiring-Challenge

In this Data-Science Competition the task was to predict the fare for taxi rides given the details of rides.

Training data: 

It contains around 1.6M records, where each record has  -- features containing different information for a trip. 
training data comprises of information captures between January'15 to April'16 while test data contains trip information from May'16 to June'16 

Here are the brief description of given features

TID - Unique ID
Vendor_ID - Technology service vendor associated with cab company
New_User - If a new user is taking the ride
toll_price - toll tax amount
tip_amount - tip given to driver (if any)
tax - applicable tax
pickup_timestamp - time at which the ride started
dropoff_timestamp - time at which ride ended
passenger_count - number of passenger during the ride
pickup_longitude - pickup location longitude data
pickup_latitude - pickup location latitude data
rate_category - category assigned to different rates at which a customer is charged
store_and_fwd - if driver stored the data offline and later forwarded
dropoff_longitude - drop off longitude data
dropoff_latitude - drop off latitude data
payment_type - payment mode used by the customer (CRD = Credit Card, CSH - Cash, DIS - dispute, NOC - No Charge, UNK - Unknown)
surcharge - surchage applicable on the trip

fare_amount - trip fare (to be predicted)

Feature Engineering:

Since the task is to predict the fare_amount. Therefore one should focus on the features than has direct/indirect impact on fare_amount.
Existing Features:
  1.  TID: Not important for prediction
  2.  Vendor_ID: Important. Because, differennt vendors have different policies.
  3.  New_User:  Could be. But there very few records in given data for a new user(Variance ~1)
  4.  toll_price, tax: Important. They has direct impact on fare.
  5.  pickup_timestamp, dropoff_timestamp: Important. But it can't be used directly. 
  6.  passenger count: Important.
  7.  pickup-dropoff latitude-logitude: Important. Fare changes according to region.
  8.  rate_category: Important.
  9.  store_and_fwd: Not important
  10. payment_type: Could be. Because some vendor prefers cashless transaction. And for that they provide special discount.
  11. surcharge: Important. Direct Impact on fare.
Features Extracted:
  1. Distance: Using pickup and dropoff location.
  2. Time Elapsed: Using pickup and dropoff timestamp
  3. Speed: Using time and Distance(I didn't do it).
  4. Ride_Importance: using location and tip_amount(I didn't do it).
  
Distance: I have calculated great circle distance using pickup-dropoff latitude-logitude. One can calculate Vincenty Distance also.
Time_elapsed: Easy to calculate using pandas.

How to handle null values and outliers: See my code.
