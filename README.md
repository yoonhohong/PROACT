# Workflow 

## Goals  
- To develop personalized progression/survival prediction models for patients with ALS   
- To develop ML-based subtyping (clustering)/staging of ALS patients  

## Dataset 
PRO-ACT database 

Accessed Sept. 2017 
DB contains 10,723 patients (including all datasets for training, training2, leaderboard, validation)

You can download all datasets here.      
https://www.dropbox.com/sh/3lmi5ii3sgyi7o3/AACeVLTGtSDXSKIaX6P7Hxj2a?dl=0

## preprocess.R

The whole datasets were preprocessed as followings, saving output files as csv for each category.    

1. demographic dataset (n=8,653) 
-> demographic.csv 

2. ALSFRS dataset 
- duplicates excluded   
- separate data into two sets (i.e, original vs. revised)   
- 30,154 records with both ALSFRS original and revised 
-> ALSFRS_original.csv, ALSFRS_revised.csv  

3. ALSFRS and ALSFRS_R total scores meta-features and slope during the first 3 months (>= 0 days & < 92 days)
- min, max, mean, number of measurements, time from enrollment to the first and to the last measurement, time interval between the first and last measurement, slope estimate by linear regression   
-> alsfrs_total_3mo_meta_slope.csv, alsfrs_r_total_3mo_meta_slope.csv

## survival.R
1. survival data (n=9080)   
-> survival.csv 

## datacleaning.R
1. fvc_percent dataset  
- duplicates excluded    
-> fvc.csv   

2. svc_percent dataset 
- duplicates excluded 
-> svc.csv 

3. fvc_percent (and svc_percent) meta-features during the first 3 months (>= 0 days & < 92 days) 
- min, max, mean, number of measurements, time from enrollment to the first and to the last measurement, time interval between the first and last measurement, slope estimates by linear regression   
-> fvc_3mo_meta.csv, svc_3mo_meta.csv   

4. als hx   
- no duplicates   
- excluding records with diag_delta > 0 or onset_delta > 0 (which means that enrollment precedes diagnosis or symptom onset)  
-> als_hx.csv 

5. family hx 
- no duplicates   
-> family_hx.csv 

6. riluzole 
- no duplicates  
-> riluzole.csv

7. treatment group
- no duplicates
-> treatment_group.csv

8. vitals 
- exclude duplicates 
-> bmi.csv, weight.csv, vitals.csv 

9. lab  
- duplicates excluded   
- excluded records without feature_delta  
-> lab.csv 

## Imputation

## Progression prediction (slope of ALSFRS total score)
predict the slope of ALSFRS total scores    
features: Age, Gender, onset_site, onset_delta, ALSFRS total score, FVC     
algorithm: linear regression   
results: Rsquared = 0.099, MAE = 0.45, RMSE = 0.57, r = 0.31   
![scatter_plot_slope_obs_pred_lm](/images/slope_obs_pred_lm.png)   
how to improve the model performance?    


## Survival/stage prediction 

## Clustering (cross-sectional)

## Clustering (longitudinal)  

## ML-based Staging  




