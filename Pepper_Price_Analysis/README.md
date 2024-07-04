
# *Pepper _Price_Analysis*

*Analysis objective :*

*To predict and forecast the selling prices of Bell Peppers of different colors (green, red, yellow)*


* [*Data sets*](https://github.com/omars1234/TimeSeries_ML/tree/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/Data_Sets)  

* [*Requirements File*](https://github.com/omars1234/TimeSeries_ML/blob/8c35b7422f5fc24eb85f044333bc4c15bad4d747/Pepper%20_Price_Analysis/requirements.txt)

* [*notebooks*](https://github.com/omars1234/TimeSeries_ML/tree/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/notebooks)

   * [*Data_Preperation_and_expoloration*](https://github.com/omars1234/TimeSeries_ML/blob/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/notebooks/Data_Preperation_and_expoloration.ipynb)

   * [*Stats In Depth-Using R-Programming Language*](https://github.com/omars1234/TimeSeries_ML/blob/22552e6b1989dfe0ff8a590a77aa6f4752b66bab/Pepper%20_Price_Analysis/notebooks/stats.ipynb)

   * [*Features_Engineering*](https://github.com/omars1234/TimeSeries_ML/blob/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/notebooks/Features_Engineering.ipynb)

   * [*Features_Selection*](https://github.com/omars1234/TimeSeries_ML/blob/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/notebooks/Features_Selection.ipynb)

   * [*Data_Modelling*](https://github.com/omars1234/TimeSeries_ML/blob/2c7f7df247af4dafcdfc6b0422cfd3e29db3340b/Pepper%20_Price_Analysis/notebooks/Data_Modelling.ipynb)



# *Brief Project Overview & Objectives of the Capstone Project*

### *Why we are doing this project ?*

  *1. This Project provides the industry with a well reliable analysis that drive the decision making in the industry of Bell Pepper*

  *2. Capstone projects are generally developed to energize students' critical thinking, problem-solving, oral communication, research, and teamwork abilities*

  ### *Problem Statement :*

  *1. Description of the Problem :   To predict and forecast the selling prices of Bell Peppers of different colors (green, red, yellow)*

  *2. Importance of Solving the Problem :  Unveil underlying patterns and contributing factors to the observed price trends for each color of Bell Pepper ,facilitating more informed decision-making*

  *3. ITarget Audience or Beneficiaries : Pepper Pirate Paradise Ltd*

  ### *Objectives and Goals*

  *1. Specific Aims of the Project : Predicting and forecasting prices for the next four weeks*

  *2. Expected Outcomes : Three differen prices one for each Pepper color*

  ### *Methodology*

  *1. Data Exploration*

   * *A. Data Description :*

     * *The historical dataset (actual.csv) ,has the following Features:*
     
       * *Categorical features :  6 Features  [vietnam_season,p_color,brazil_season,indonesia_season,india_season,china_season]*
     
       * *Numerical features : 14 features [price,total_volume,brazil,india,vietnam,indonesia,china,jordan_max_price,jordan_min_price,demand,supply]*

     * *The Projected dataset ,has the following Features:*
     
       * *Categorical features :  4 Features 
           [brazil_season,indonesia_season,india_season,china_season]*
     
       * *Numerical features :  6 Features 
           [total_volume,brazil,india,vietnam,indonesia,china]*  

   * *B. Data Preprocessing :*

     * *Missing Values*

     * *Duplicates Values*

     * *Data types*

     * *Unique values is each column*

     * *Check statistics of data set*


   * *C. Exploratory Data Analysis :*

     * *Mean Price and Mean Price change over years by "p_color" feature*

     * *Mean Price over years by "vietnam_season" feature"*

     * *Mean Price over years "vietnam_season & month" features"*

     * *Mean Price over time "by all countries in all seasons"*

     * *Mean Price over time "by p_color and by all countries in all seasons"*  

   * *D. Feature Engineering :*

     * *Adding new features for Volume percentage for each country ( multiplying price by each country's volume)*

     * *Adding new features for total price by ( multiplying price by each country's volume)*

     * *Creating new 3 datasetes ,each dataset represent a specific color of the pepper*

     * *Features Shifting ,shift[4] with Rolling[4]*



   * *E. Feature Selection :*

     * *SelectKBest method*

   * *F. Modeling :*

     * *Applied RandomizedSearchCV on liest of models and parameters :*





    models = {
                "RandomForestRegressor": RandomForestRegressor(),
                "DecisionTreeRegressor": DecisionTreeRegressor(),
                "LinearRegression": LinearRegression(),
                "XGBRFRegressor": XGBRFRegressor(),
                "GradientBoostingRegressor":GradientBoostingRegressor(),
                "AdaBoostRegressor": AdaBoostRegressor(),
                "BaggingRegressor":BaggingRegressor()
                
                
            }

    params={        
                "RandomForestRegressor":{
                    "n_estimators":[90,100,110], 
                    "min_samples_split":[2,4,6],
                    "min_samples_leaf":[0.8,1],
                    "bootstrap":[True, False],                                                                                                    
                    "max_features":["sqrt","log2","auto"],                                     
                    "max_depth":[2,3,4],
                    "criterion":['poisson', 'squared_error','friedman_mse','absolute_error']
                    },

                "DecisionTreeRegressor": {
                    'criterion':['poisson', 'squared_error','friedman_mse','absolute_error'],
                    'splitter': ['best', 'random'],
                    "max_depth":[2,3,4], 
                    "min_samples_split":[2,4,6],
                    "min_samples_leaf":[0.5,0.8],
                    #'max_features': [1,2,3,4],
                },
                "LinearRegression":{

                },
                "XGBRFRegressor":{
                    'learning_rate': [0.001,0.1,1],
                    'n_estimators': [90, 100, 110], 
                    "booster":["gbtree"],
                    'colsample_bytree': [0.5,0.8], 
                    'colsample_bynode': [0.5,0.8],
                    'random_state':[42]
                },

                
                "GradientBoostingRegressor":{
                    #'loss':['squared_error', 'huber', 'absolute_error', 'quantile'],
                    'learning_rate': [0.01,0.1,1],
                    'n_estimators': [90, 100, 110],
                    'subsample': [0.8,1],
                    #'criterion':['squared_error', 'friedman_mse'],
                    'min_samples_split': [2, 4, 6],
                    'min_samples_leaf': [0.8, 1],
                    'max_depth':[2,3,4],
                    #'max_features': ['sqrt', 'log2', 'auto']
                },
                "AdaBoostRegressor":{
                    'n_estimators': [45,50,55],
                    'learning_rate': [0.0001,0.001,0.01],
                    'loss':['linear','square','exponential'],
                    #'random_state':[42]
                    
                },
                "BaggingRegressor":{},
                
            }



* *F. Visualizations of Outcomes :*

     * *Red_Color*
     * *Green_Color*
     * *Yellow_Color
     
     








 






     

     
     
     
     
     
     
     











     
     



             









  








