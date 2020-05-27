## Kaggle - Bluebook for bulldozers
The objective of this project is to create a model to predict the auction sale price for a piece of heavy equipment to create a "blue book" for bulldozers  
I got the dataset from the [Kaggle Competition](https://www.kaggle.com/c/bluebook-for-bulldozers)  
  
### My approach  
I used a Random Forest model to predict the sale price of the equipments. Initially, I changed the dependant variable (SalePrice) to log(SalePrice) to check my performance with that of the top submissions of the leaderboard as the evaluation metric was RMSLE  
I used minimal Exploratory Data Analysis to begin with. For initial feature engineering, I just converted the string type independant variables to category type and replaced the missing values with the median value of the column. I added a new column for every column that had missing values which had a value of 1 when the correspinding original column had a missing value, and 0 otherwise  
After running the model once, I trimmed the number of features based on their feature importances  
Further, I removed the redundant correlated features from the remaining features, and added a new feature 'Age'  
Finally, since Random Forest is not good at extrapolating features which have a time-series componenet, I found out which features were significantly different in the training and validation sets (as the two sets contained data of different time periods) and checked whether removing them one at a time improved the model accuracy, and finally removed the one s which impacted the model negatively  

### Final result
The model had a predictive accuracy of 91.35% and a RMSLE of 0.220, which is better than the Kaggle leaderboard #1 which had a RMSLE of 0.229 (although it should be kept in mind that the competetion is 7 years old)
