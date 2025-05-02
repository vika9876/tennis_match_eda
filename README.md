# tennis_match_eda
Class assignment on Exploratory Data Analysis (EDA) of tennis match data to uncover patterns and insights using visualizations and statistical summaries. The instructions for the same and the evaluation results are given 
Instructions:
- Analyze the provided tennis dataset by following the instructions and answering the
questions in each section.
- Use Python for data analysis, machine learning model building, and evaluation.
- Submit your code and answers in a Jupyter notebook along with a brief report
summarizing your findings.
Dataset Column Descriptions
1. rally: Rally number, representing each point or play sequence in a match.
2. serve: Indicator for the serve number (1 or 2), denoting whether it's a first or second
serve.
3. hitpoint: Type of stroke, categorized as values like "B" (backhand), "F" (forehand), etc.
4. speed: Speed of the ball in the hit, measured in appropriate units (e.g., km/h or m/s).
5. net.clearance: The height of the ball above or below the net, measured in meters.
6. distance.from.sideline: Distance from the sideline where the ball landed, in meters.
7. depth: Depth of the shot on the court, measured in meters.
8. outside.sideline: Boolean indicating if the ball landed outside the sideline (True/False).
9. outside.baseline: Boolean indicating if the ball landed outside the baseline (True/False).
10. player.distance.travelled: Distance the player traveled to reach the ball, measured in
meters.
11. player.distance.from.center: Player's distance from the center of the court.
12. time.to.net: Time taken by the ball to reach the net after the hit.
13. y.position and x.position: Court coordinates of the ball's landing position.
14. previous.depth: Depth of the previous shot in the rally.
15. opponent.depth: Opponent's depth on the court when the shot was hit.
16. opponent.distance.from.center: Opponent's lateral position from the court center.
17. same.side: Boolean indicating if the player and opponent are on the same side of the
court (True/False).
18. previous.hitpoint: Type of stroke used in the previous hit.
19. previous.time.to.net: Time taken by the previous shot to reach the net.
20. server.is.impact.player: Boolean indicating if the server is the player making the impact.
21. outcome: Outcome of the rally, with values like "UE" (Unforced Error), "FE" (Forced
Error), or "W" (Winner).
22. gender: Gender of the player, represented as "mens" or "womens".
23. ID: Unique identifier for each rally or shot event.
Assignment Tasks
1. Exploratory Data Analysis (EDA):
- Perform EDA on the dataset, analyzing various aspects of the data.
- Summarize the five most important observations from your analysis, including any
interesting trends, distributions, or correlations between variables.
2. Build and Compare Machine Learning Models:
- Build a variety of machine learning models on the dataset to predict the match outcome
or any other target variable you find relevant.
- Use algorithms from different model types, such as:
- Logistic Regression
- Decision Trees
- Random Forests
- Gradient Boosting
- Support Vector Machines
- K-Nearest Neighbors
- Neural Networks
- Ensemble methods (e.g., Bagging, Boosting, Stacking)
- Ensure to split the data into training and testing sets and use cross-validation for model
validation.
3. Feature Importance Analysis:
- Determine the most important features impacting the model's performance. Use
methods such as feature importance (for tree-based models), coefficients (for linear
models), and permutation importance.
- Summarize the top five features that most significantly affect the model's predictions.
4. Model Evaluation and Comparison:
- Evaluate each model using accuracy, recall, precision, and F1 score.
- Compile the results in a DataFrame to compare each model's performance.

# I. Exploratory Data Analysis (EDA)

1.	Distribution of Rally Outcomes: The outcome variable showed a balanced distribution across the categories, including "Unforced Error" (UE), "Forced Error" (FE), and "Winner" (W), indicating a diverse dataset that can support predictive modeling without significant class imbalance issues.
2.	Shot Speed and Hitpoint Type: The speed of the ball varies depending on the hitpoint type. For instance, forehand (F) shots tend to have higher speeds on average compared to backhand (B) shots, suggesting a potential predictive relationship between these variables.
3.	Net Clearance and Outcome: Successful shots (Winners) tended to have higher net.clearance values, while shots with lower net clearance were more often associated with errors (UE or FE).
4.	Player Movement: The player.distance.travelled metric shows that players generally cover significant ground in each rally, which could impact fatigue and, consequently, shot accuracy or error likelihood.
5.	Court Positioning: Both player.distance.from.center and opponent.distance.from.center showed that positioning closer to the center is associated with successful shots, potentially due to better court coverage and quicker response time.

II. Machine Learning Model Building and Comparison
Eight machine learning models were trained and evaluated on the dataset to predict the outcome of rallies. Below is a summary of the models and their performance metrics:





MODEL	ACCURACY RECALL	PRECISION	F1 SCORE
LOGISTIC REGRESSION	0.821	0.805	0.817	0.809  
DECISION TREE	0.795	0.783	0.787	0.785  
RANDOM FOREST	0.849	0.839	0.843	0.840  
GRADIENT BOOSTING	0.859	0.848	0.854	0.850  
SUPPORT VECTOR MACHINE	0.842	0.833	0.836	0.833  
K-NEAREST NEIGHBORS	0.740	0.724	0.735	0.726  
NEURAL NETWORK	0.851	0.844	0.846	0.845  
BAGGING	0.839	0.833	0.832	0.832  
Best Model: Gradient Boosting achieved the highest accuracy (0.859), recall (0.848), precision (0.854), and F1 score (0.850). This suggests that it captured complex patterns in the data effectively, likely due to its ability to combine weak learners and sequentially minimize error.


III. Feature Importance Analysis
Two methods were used to assess feature importance: feature importances from the Random Forest model and permutation importance.
1.	Top Features Based on Random Forest:
a)	previous.hitpoint
b)	server.is.impact.player
c)	speed
d)	previous.time.to.net
e)	net.clearance
2.	Top Features Based on Permutation Importance:
a)	speed
b)	previous.hitpoint
c)	previous.time.to.net
d)	server.is.impact.player
e)	net.clearance



Insights:
1.	speed and previous.hitpoint appear consistently in the top features, indicating that the type of shot and ball speed significantly affect rally outcomes.
2.	previous.time.to.net and net.clearance reflect aspects of shot trajectory and placement, showing the importance of precision in shot execution.
3.	server.is.impact.player also holds predictive power, likely reflecting the advantages (or disadvantages) associated with serving.

IV. Model Evaluation and Comparison Summary
1.	Model Selection: Gradient Boosting emerged as the best-performing model across all key metrics. Its superior performance can be attributed to its ensemble approach, which effectively combines multiple weak learners to reduce bias and variance.
2.	Interpretation of Feature Importance: The consistent appearance of speed, previous.hitpoint, and net.clearance across both feature importance methods suggests that these features are crucial in determining rally outcomes. This insight aligns with tennis gameplay, where shot speed, type, and trajectory control are key factors for winning points.
