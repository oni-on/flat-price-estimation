# Rent Price Estimation
The goal of this challenge is to come up with the best price for a flat with these characteristics:

* Address: Almstadtstraße 9/11, 10119 Berlin
* Size: 78 sqm
* Floor: 1st
* Rooms: 2
* Built-in kitchen: yes
* Balcony: yes
* Construction year: 1902
* Condition: good
* Quality: good

## Challenge 1
1. Come up with the best possible price for the offered apartment based on the list.

    The predicted *Kaltmiete* for this flat is **1145 Euro**
2. Write down the steps you made to come up with that price (bulletpoints!).
    + Defining what will be predicted. 

        The give dataset contains info on Kaltmiete, Nebenkosten, Heizungkosten and overall rent price. For the sake of simplicity I focused on predicting _Kaltmiete_.
     + Exploratory Analysis and Data Wrangling   
        + Plotting the rent price and features to get insights 
            + For flats built before 1920 the older ones have higher prices, while for flats built after 1970 the newer flats have higher prices. 
            + The relation between the floor of a flat and its price is counterintuitive due to lack of data, therefore the feature **floor** shouldn't be used for building a model. The data shows that the average rent price decreases for flats on the third floor or higher.
        + Converting the features into the correct data types.
        + Imputing missing values. Deciding what to do with flats that don't have data e.g. construction year.
     + Setting up the model validation scheme. 
     
        Splitting data into a training and test set is necessary in order to avoid overfitting (the model memorizes instead of learning).
     + Building a Linear Regression model
     
        This model had an average absolute error of 171 Euro and predicted a price of **1225 Euro** for the given flat.
     + Kth Nearest Neighbor (KNN) Regression
     
        This machine learning algorithm decreased the average (absolute error) to 124 Euro and predicted **1145 Euro** as Kaltmiete.
        
3. How good is your estimate at this point?
    
    The best performance on unseen data comes from KNN Regression with the following error rates:
    
     + Average % Error: 14.5% 
     + Average Overestimation Error (risk of not finding a tenant at this price): 157 Euro
     + Average Underestimation Error (risk of the landlord not being happy with the offer): 90 Euro
     + Average Absolute Error: 124 Euro

## Challenge 2

If you’d have more time and could query the database by yourself

1. What would be your next steps to improve your price estimate (bulletpoints!)?
    + Adding more data! It's impossible to build a decent model with only 50 data points
    + Getting more info on the new flats. I believe that the following features could improve the prediction:
        + Info on the sorroundings (e.g. noisy street or not, nearby facilities)
        + Whether the building is an Altbau or not
        + Whether the flat is on the top floor (relevant in general, not for our 1st floor flat)
        + Whether the flat has been renovated recently
        + Orientation of the windows
        + Info on the heating system
     + Using a more complex *Nonlinear Machine Learning* model. At this stage I used a *Linear Model* and *KNN Regression* due to the low amount of data. Experimenting with *Decision Tree* was a failure due to overfitting and lack of data. If I had more data I would use XGBoost Regression or Random Forests which combine the results of many Decision Trees.
     
2. How good can the estimated price become?

    Sky is the limit ;). It depends on the data

