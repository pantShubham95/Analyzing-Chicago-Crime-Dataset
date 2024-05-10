# Analyzing-Chicago-Crime-Dataset

Crime is a significant challenge in Chicago, impacting the safety and well-being of its residents. This research project aims to leverage the power of data analysis to gain valuable insights into crime patterns across the city. By understanding how crime varies across different areas, times of year, and even days of the week, we can inform the development of more effective crime prevention strategies.


Research Questions:

This research will address several key questions about crime in Chicago:

- How does the frequency of different types of crimes vary across different districts in Chicago?
    
- What are the most common locations where domestic-related crimes occur?
    
- Are certain types of crimes more likely to result in arrests than others?

- How do crime rates and types vary across different seasons and days of the week?
    
- Can a machine learning model accurately predict the primary type of crime (e.g., theft, assault) based on features like date, location description, community area, and time of day (derived from date)?

Data source:

The data for this project was obtained from the Chicago Crime dataset available on Google BigQuery. This publicly available dataset provides information on reported crime incidents in Chicago.

Although the full dataset contains 8 million of entries, the initial analysis will utilize a subset of 5 million rows due to the aforementioned limitations. After we have the 5 million rows next we are gonna filter the data to only include the data after 2018 as it would be very computationally expensive to train on 5 million rows. **Our final data will contain 7,57,698 rows**.  This provides a representative sample for exploring research questions and developing initial insights.


Data Content: 

The dataset provides information on reported crime incidents in Chicago, including various attributes for each crime record:

- unique_key: A unique identifier for each crime record.
- case_number: A unique identifier for each crime case.
- date: The date and time when the crime occurred.
- block: The block address where the crime occurred.
- iucr: Illinois Uniform Crime Reporting code, a numerical code that represents the crime type.
- primary_type: The primary classification of the crime (e.g., theft, assault, robbery).
- description: A detailed description of the crime.
- location_description: The type of location where the crime occurred (e.g., street, residence, park).
- arrest: Indicates whether an arrest was made for the crime (Yes/No).
- domestic: Indicates whether the crime was domestic-related (Yes/No).
- beat: The police beat where the crime occurred.
- district: The police district where the crime occurred.
- ward: The city ward where the crime occurred.
- community_area: The community area where the crime occurred.
- fbi_code: The FBI's classification for the crime.
- x_coordinate: The X-coordinate of the location where the crime occurred (often in a projected coordinate system like UTM).
- y_coordinate: The Y-coordinate of the location where the crime occurred (often in a projected coordinate system like UTM).
- year: The year when the crime occurred.
- updated_on: The date and time when the record was last updated.
- latitude: The latitude coordinate of the crime location.
- longitude: The longitude coordinate of the crime location.
- location: A combined field of latitude and longitude, often represented as a point on a map.

Approach:

- Data Acquisition and Storage: We'll download the Chicago crime data from BigQuery and store it in a manageable format. This will involve uploading the data to a AWS S3 and then importing it into our Jupyter Notebook.

- Exploratory Data Analysis (EDA): We'll delve into the data to understand its structure, identify any anomalies, and uncover relationships between different factors. Visualization libraries like Matplotlib and Seaborn will be used to create informative charts and graphs. Additionally, we'll leverage the Folium library for geospatial analysis to:

  - Visualize Crime Distribution: Create interactive maps that depict the spatial distribution of various crime types across Chicago.
  - Identify Crime Hotspots: Utilize clustering techniques to pinpoint areas with high concentrations of specific crimes.

- Data Cleaning and Feature Engineering: Based on the initial analysis (EDA), we'll address data quality issues like missing values and inconsistencies. We might also employ feature engineering techniques to improve model performance. This could involve encoding categorical variables or even creating entirely new features based on existing data.

- Model Building and Evaluation:  Our main objective is to predict the type of crime. We'll build and evaluate three distinct machine learning models for this purpose:

  - Logistic Regression: This model will attempt to predict the primary crime type (e.g., theft, assault) based on features like date, location, and community area.
  - Random Forest: Similar to the logistic regression model, this will also predict crime type based on features like date, location, and community area.
  - XGBoost : This model might be explored to predict crime type using historical data on crime types and locations.

We'll then compare the performance of these models using metrics like accuracy, precision, recall, and F1 score. The model with the best performance will be chosen for further analysis.

- Ensemble Model Construction: To potentially achieve even better results, we'll create an ensemble model that combines the predictions from the individual models. This ensemble leverages the strengths of each model while mitigating their weaknesses, potentially leading to superior performance. Python libraries like scikit-learn will be used for this step. We will be using AdaBoost as our ensemble model and our weak learner will consist of Decision Trees.
