# Covid-Prediction

The purpose of this project was:
1) Pull covid data from google Big Query (https://console.cloud.google.com/bigquery?project=my-project-75222-gt) from the covid covid_19_open_data database
2) Explore the features
3) Choose an interesting target feature
4) Run regression models on the target feature using other features from the data that highly correlated with the target feature.

After exploring the data, I chose the target feature called new_hospitilized_patients. I think this is useful because people could theoretically use the model to predict how many new patients a hospital could expect on any given day. In the exploratory analysis I was looking at features that correlated with the target feature. The heat map below was generated to see how the pre-selected features (some of this based on the beforehand exploratory analysis) correlated with the target feature:

![Image description](https://github.com/sebastiandifrancesco/Covid-Prediction/blob/main/heatmap_of_features.PNG)

The features I ultimately chose to go into the regression models were:

- 'new_confirmed'
- 'cumulative_tested'
- 'population_age_40_49'
- 'population_age_50_59'
- 'population_age_10_19'
- 'population_male'
- 'population'
- 'population_female'
- 'population_age_00_09'
- 'population_age_60_69'
- 'population_age_30_39'
- 'population_age_20_29'
- 'population_age_70_79'
- 'population_age_80_and_older'
- 'cumulative_deceased'

After running multiple regressors on these features to predict the target feature their respective r2 values were compared to select the model that would be most accurate. This model was the scaled random forest reg model which had an r2 value of 0.944541. This model was then tested, and the results and it came back with an accuracy score of 94.84%. The results are in the table below:

![Image description](https://github.com/sebastiandifrancesco/Covid-Prediction/blob/main/model_performance.PNG)

The main limitation on this model is that the data is only from Florida and New York. The reason for this is that these were the only two states that had enough features to build a model on; however, this model could still be useful to apply to other states even though the model was not built off of data from other states. The features that are fed into the model are mainly population features along with the new_confirmed feature, cumulative_deceased feature, and the cumulative_tested feature. These features should all be available for most people to easily find and plug into the model for use in whichever state they are located.

Useful continuation of this work would include finding a source for pulling these features across a multitude of different states to generate a more generally accurate model. Also, these features could be used to predict new_cases just as easily as it predicts new_hospitalized_patients; however, in my exploratory analysis I found building a model to predict new_ cases was less accurate than building the model to predict new_hospitalized_patients. This was a main factor in why I chose the latter target feature over the former.
