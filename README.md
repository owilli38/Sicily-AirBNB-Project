# Sicily-AirBNB-Project
Part of the final project for 6211 (Advanced Business Analytics)


Final Report: Analysis of Airbnb Market in Sicily
Group Members: Paul Clark, Ryan Moore, Seth Rabinowitz, and Owen Williamson 


1. Project Summary: Introduction and Objectives 
Introduction

For our final project, we used data from Inside Airbnb, looking at data for 12 months in Sicily. We looked at applying Sicily Airbnb data to represent a real-estate company that is highlighting the potential of owning Airbnb properties. Using data-informed insights, these potential hosts can better understand and navigate the market, optimizing their listing to succeed by having higher levels of occupancy by focusing on certain amenities, price, property type, and location. 

As a residential investment firm, we are looking to optimize our ability to identify future properties that will increase our company’s net income. In order to limit losses related to “unsuccessful” rental properties and identify qualitative attributes of a successful property, we will analyze existing rental properties to understand what characteristics are responsible for their success or failure.
Objectives 

Explore the market structure, including the number of listings and average pricing.
Identify optimal pricing, location, and property characteristics for hosts.
Analyze occupancy trends to determine high-demand neighborhoods.
Develop predictive models to assess factors influencing listing success.
Utilize text mining to understand customer preferences and concerns.

2. Detailed Analyses Processes and Steps
Exploratory Data Analysis (EDA)
Imported and cleaned Airbnb data from Inside Airbnb.
Analyzed distributions of price, availability, and listing characteristics.
Created heatmaps using GeoJSON data to visualize listing density across Sicily.
A large proportion of Airbnb listings are centered in Palermo, Catania, and Syracuse and their surrounding areas. In raw numbers, of the 57,963 listings across Sicily, there are around 3600, 2000, and 1500 listings in these 3 cities, respectively (within the exact neighborhood, not including adjacent neighborhoods). 
After creating a new column using ‘availability_365’ for occupancy rates during the 12 month period, we can also see that these main cities have lower occupancy rates. This could potentially indicate these areas are over-saturated and that for new Airbnb hosts, looking at smaller areas could lead to more success. 

Generated histograms to analyze pricing distribution and occupancy trends.
Removed outliers to make histogram show differences in prices more detailed. 
Occupancy Analysis & Market Segmentation
Defined high-performing listings based on occupancy rates.
Using 70% occupancy rate as our benchmark for a successful property, we found that the average listing had a 35% occupancy rate with a Standard Deviation of 35%. One standard deviation above the mean gave us the 70% threshold.

Segmented listings by neighborhood to identify high-demand areas.
After finding the average occupancy rate based on the listings in each neighborhood, these ones were the top 10 in average occupancy rates across Sicily. 
Examined relationships between availability, price, and listing features.

Predictive Modeling
Segment Vector Model (SVM): Classified listings as high or low performing.
Linear Regression: Determined features affecting pricing.
LDA Topic Modeling: Analyzed guest reviews to extract key preferences.
Model Selection: Evaluated models based on accuracy, AUC, and F1 score.

3. Results and Findings

Market Insights
Majority of listings are concentrated in major tourist hubs such as Palermo and Catania.
Price distribution follows a right-skewed pattern with most listings priced below the median.

Occupancy Trends
Successful listings showed consistent bookings throughout the year, especially after the first quarter of the year (January-March).
SVM Classification Results: The SVM model with a linear kernel successfully separated high- and low-performing listings using PCA projection. The clear decision boundary supports the model’s utility in predicting successful Airbnb properties based on listing attributes.

Correlation Findings: Occupancy rate strongly correlated with listing success (0.86), reinforcing its role as the most predictive feature. In contrast, features like price, bathrooms, and accommodations had weak negative correlations, suggesting that larger or more expensive listings are not necessarily more successful.
Private Room Advantage: Listings offering private rooms demonstrated higher average occupancy rates than entire home/apartment listings, indicating that more affordable and accessible options may attract more consistent bookings, especially in oversaturated areas.

Class Imbalance: Of the total listings, only 1,718 were classified as successful (≥70% occupancy), compared to 5,627 unsuccessful ones, underscoring the competitive nature of the market and the value of data-informed strategies.
Successful listings, while a smaller group, has significantly fewer daily available listings, meaning they are more booked up throughout the year. For hosts, this would lead to more revenue for their listings. 

Occupancy-Weighted Revenue
Comparing the successful listings above the 0.7 threshold, and unsuccessful listings below that threshold, we can see that the occupancy-weighted average revenue is extremely higher for successful listings.  Successful listings generate higher revenue due to a combination of higher prices and higher occupancy.  The occupancy-weighted average provides an estimate of the average daily revenue potential of a listing or a group of listings, considering both price and occupancy rate.  Average price - Successful: $405.71.  Average price - Unsuccessful: $307.79.  Occupancy-Weighted Revenue - Successful: $381.37.  Occupancy-Weighted Revenue - Unsuccessful: $90.85
Successful Property Correlated Attributes identified via Multi-Linear Regression (Price/Occupancy Rate)
Occupancy Rate Regression:
When using Occupancy Rate as the dependent variable, the regression identifies a few key attributes with a strong positive correlation to occupancy that are statistically significant. These factors include:
Private Room Property Types
Properties in the neighbourhood of “Siracusa”
Properties with bathroom types of “1 Bath” or “1 Private Bath” (distinction likely made at the property owner posting level
Availability identified as a statistically significant variable with a negative coefficient as the more days a property is available, the less it is occupied. It is important to note that the property owner sets the availability, so a property can have 0 availability for the next 90 days and still not be fully occupied.

Price Regression:
To complement the Occupancy Rate Linear Regression, we worked to identify the impact the previously used property attributes have on the Price. Similarly, the following attributes were identified as having a statistically significant impact on the price with a strong positive coefficient:
Property Type of Private Room
Bathroom Text of 1 Bath. It should be noted that “1 private bath” is not statistically significant at the .05 p-value threshold, however if interpreted would have a negative impact on price.
Neighbourhood of Siracusa.

Summary of Regression
Based on the findings from both the Occupancy Rate and Pricing regression models, it is fair to conclude that the attributes for the most successful AirBnB properties in Sicily are Private Room properties with one bathroom in the neighbourhood of Siracusa. As an investment firm, properties matching these specifications should be sought out for additional future investment opportunities.
Customer Insights from Review Analysis
Common themes in higher occupancy (‘successful’ properties) reviews indicate that ‘great location’ and ‘great host’ are two very important factors for successful properties for guests. Guest sentiment indicates desire for an Airbnb that is centrally located and walkable to the city center, beaches/the sea, and restaurants. 
For unsuccessful properties, reviews highlighted having a great stay and nothing too negative, yet the quality of the host and location did not seem to be as significant compared to the successful listings for guests.

4. Suggestions for Additional Work
Sentiment Analysis: After running preprocessing for text mining on the review dataset, the word clouds didn’t provide too much insight into differences between successful and unsuccessful listings. As the review dataset had more than just English reviews, we had to process the reviews to remove non-English reviews. Further LDA and sentiment analysis could be utilized to further derive insights and strategies for why some listings are very successful and others are not. 
More complex models: with how big these files are and how much data is available, there is potential of using other metrics to track other than just price and occupancy rate. If we had access to a longer range of data, running a time series to predict change in price. In addition, there would be more predictive models such as XGBoost. This would enable us to perform predictive modelling and would show the feature importance of different variables, iteratively learning and improving as it runs through the different decision trees. 

5. Conclusions
While these findings will not guarantee a successful listing, these strategies will give a strong chance of standing out in the saturated Airbnb market in Sicily. 
Pricing must be competitive and fair
Location, such as neighborhoods and central location, have a significant impact on both occupancy and price and are important for guest sentiment 
Property types, particularly private room, increase occupancy rates 
Listings with a private bathroom are both more expensive but also have less availability, meaning more booked up 
By leveraging these findings, real estate investors and Airbnb hosts can make informed decisions about pricing, location, and property management to maximize their rental success in Sicily.
