GENERAL INFORMATION

1. Title of Dataset: data of all-cause in-hospital mortality among ICU-admitted HF patients which extracted from the MIMIC-III database.

2. Author Information
	A. Principal Investigator Contact Information
		Name: Jingmin Zhou
		Institution: Department of Cardiology, Shanghai Institute of Cardiovascular Diseases, Zhongshan Hospital, Fudan University
		Address: 180 Fenglin Road, 200032 Shanghai, PR China
		Email: zhoujinminzsyy@163.com

	B. Associate or Co-investigator Contact Information
		Name: Fuhai Li
		Institution: Department of Cardiology, Shanghai Institute of Cardiovascular Diseases, Zhongshan Hospital, Fudan University
		Address: 180 Fenglin Road, 200032 Shanghai, PR China
		Email: 454762976@qq.com

3. Date of data collection (single date, range, approximate date) <suggested format YYYY-MM-DD>: between 1 June, 2001 and 31 October, 2012.

4. Geographic location of data collection <latitude, longiute, or city/region, State, Country, as appropriate>: the ICU of the Beth Israel Deaconess Medical Center, Boston, USA

5. Information about funding sources that supported the collection of the data: the Program for the Outstanding Academic Leaders supported by Shanghai Science and Technology Commission (16XD1400700), National Natural Science Foundation of China (81370199),and National Basic Research Program of China (973 350 Program, 2012CB518605).


SHARING/ACCESS INFORMATION

1. Licenses/restrictions placed on the data: no restrictions

2. Links to publications that cite or use the data: Zhou, Jingmin; Li, Fuhai (2021), Prediction model of in-hospital mortality in intensive care unit patients with heart failure: machine learning-based, retrospective analysis of the MIMIC-III database, Dryad, Dataset, https://doi.org/10.5061/dryad.0p2ngf1zd

3. Links to other publicly accessible locations of the data: no

4. Links/relationships to ancillary data sets: no 

5. Was data derived from another source? yes
	A. If yes, list source(s): the Medical Information Mart for Intensive Care (MIMIC-III)  database (version 1.4, 2016)

6. Recommended citation for this dataset: Zhou, Jingmin; Li, Fuhai (2021), Prediction model of in-hospital mortality in intensive care unit patients with heart failure: machine learning-based, retrospective analysis of the MIMIC-III database, Dryad, Dataset, https://doi.org/10.5061/dryad.0p2ngf1zd


DATA & FILE OVERVIEW

1. File List: 
<list all files (or folders, as appropriate for dataset organization) contained in the dataset, with a brief description>Patients with a diagnosis of HF, identified by manual review of ICD-9 codes, and who were >15 years old at the time of ICU admission were included in the study; two researchers conducted the ICD-9 code review. Patients without an ICU record or data missing for left ventricular ejection fraction (LVEF) or N-terminal pro-brain natriuretic peptide (NT-proBNP) were excluded from the study. A total of 13,389 patients with a diagnosis of HF were screened and 1,177 adult patients were included in this study. 


2. Relationship between files, if important: no


3. Additional related data collected that was not included in the current data package: no


4. Are there multiple versions of the dataset? no
	


METHODOLOGICAL INFORMATION

1. Description of methods used for collection/generation of data: 
<Include links or references to publications or other documentation containing experimental design or protocols used in data collection>
Using Structured Query Language queries (PostgreSQL, version 9.6), demographic characteristics, vital signs, and laboratory values data were extracted from the following tables in the MIMIC III dataset: ADMISSIONS, PATIENTS, ICUSTAYS, D_ICD DIAGNOSIS, DIAGNOSIS_ICD, LABEVENTS, D_LABIEVENTS, CHARTEVENTS, D_ITEMS, NOTEEVENTS, and OUTPUTEVENTS. 

2. Methods for processing the data: 
<describe how the submitted data were generated from the raw or collected data>
We present baseline patient characteristics in both samples using a percentage of the total for categorical variables and mean ± standard deviation or median and interquartile range for continuous variables, depending on the normality of distribution. For categorical variables, we used a two-sided Pearson’s χ2 test or Fisher’s exact tests to assess differences in proportions between the two groups. For all continuous variables, we used a two-sided one-way analysis of variance or Wilcoxon rank-sum tests when comparing the two groups. 
 A total of 52 demographic, clinical, and biochemical variables were considered as candidate predictors based on existing literature, expert knowledge, and availability in clinical practice. Table 1 summarizes the predictor variables and summary statistics. Two methods were used to select the most important predictors for the in-hospital mortality prediction model from the derivation group. First, we used XGBoost 12, a supervised machine-learning and data-mining tool, which involves a meta-algorithm, to construct a strong ensemble learner from weak learners, such as regression trees 19. The parameters of a regression tree consist of the tree structures and the weights of the leaf nodes. They are sequentially optimized to minimize an objective function, consisting of a fitting loss term plus a regularization term, using gradient methods. XGBoost retrofits the tree-learning algorithm for handling sparse data by raising a weighted quantile sketch to approximate an optimization calculation and design a column block structure for parallel learning. The XGBoost algorithm can indicate the contributions of each of the predictors, making it possible to choose the most relevant predictors. The 20 top-ranked variables were selected for further analysis. Second, we used the least absolute shrinkage and selection operator (LASSO) method [13], which involves regression analysis to perform both variable selection and regularization. This enhances prediction accuracy and interpretability of a statistical model and is suitable for reduction in high-dimensional data. Variables with non-zero coefficients in the LASSO regression model were selected for further analysis.
To investigate independent risk factors of in-hospital mortality, univariate logistic regression analysis was used to assess the significance of variables selected by each method in the derivation group. Variables significantly associated with in-hospital mortality were candidates for multivariate binary logistic regression. Potential non-linearity relationships between candidate continuous variables and in-hospital mortality was explored using a smoothing plot, and nomograms were formulated based on the results of multivariate logistic regression analysis. The nomogram was based on proportionally converting each regression coefficient in multivariate logistic regression to a 0–100-point scale. The prediction models were evaluated in terms of discrimination and calibration. Calibration curves were plotted to assess the calibration of the in-hospital mortality nomogram. Discrimination was assessed by calculating the area under the curve (AUC) of the receiver operating characteristic (ROC) curve and C-statistic testing. The 95% confidence interval (CI) was calculated using 500 bootstrap resamples. Decision curve analysis (DCA) was used to compare the clinical net benefit associated with the use of these models. The model with the highest AUC and highest clinical net benefit was used to develop a nomogram predicting in-hospital mortality.
The American Heart Association Get With The Guidelines–Heart Failure (GWTG-HF) 13 risk score is a well-validated, widely accepted scoring system for risk stratification regarding in-hospital mortality. This prediction model was validated in our study groups and compared with our developed model. Because the final published version was a risk score, the calculated GWTG-HF risk score for each of the study patients was used for further analysis. A non-parametric approach, using generalized U statistical theorizing to generate an estimated covariance matrix, was used to analyze areas under the ROC curves and estimate differences in the discriminatory power between the models. 
A two-tailed P-value of <0.05 indicated statistical significance in all analyses. All analyses were performed using EmpowerStats (version 2.17.8; http://www.empowerstats.com) and R software (Version 3.1.4; https://www.R-project.org).


3. Instrument- or software-specific information needed to interpret the data: 
<include full name and version of software, and any necessary packages or libraries needed to run scripts>
All analyses were performed using EmpowerStats (version 2.17.8; http://www.empowerstats.com) and R software (Version 3.1.4; https://www.R-project.org).

4. Standards and calibration information, if appropriate: no

5. Environmental/experimental conditions:  data of all-cause in-hospital mortality among ICU-admitted HF patients.

6. Describe any quality-assurance procedures performed on the data: the data was checked by all authors.

7. People involved with sample collection, processing, analysis and/or submission: Fuhai Li,Yu Song, Mingqiang Fu,Xueting Han,Jingmin Zhou,Junbo Ge


DATA-SPECIFIC INFORMATION FOR: [FILENAME]
<repeat this section for each dataset, folder or file, as appropriate>

1. Number of variables: 51

2. Number of cases/rows: 1177

3. Variable List: 
<list variable name(s), description(s), unit(s)and value labels as appropriate for each>
group；ID；outcome；age（years）；gendera；BMI；hypertensive；atrialfibrillation；CHD with no MI；diabetes；deficiencyanemias；depression；Hyperlipemia；Renal failure；COPD；heart rate（bpm）；
Systolic blood pressure（mmHg）；Diastolic blood pressure（mmHg）；Respiratory rate（bpm）；temperature（℃）；SP O2（%）；Urine output（ml）；hematocrit（%）；RBC（m/uL）;MCH(pg);MCHC(%);MCV(fL);RDW(%);Leucocyte(K/uL);Platelets(K/uL);Neutrophils(%);Basophils(%);Lymphocyte(%);PT(Seconds);INR;NT-proBNP(pg/mL);Creatine kinase(IU/L);Creatinine(mg/dL);Urea nitrogen(mg/dL);glucose(mEq/L);Blood potassium(mEq/L);
Blood sodium(mEq/L);Blood calcium(mg/dL);Chloride(mEq/L);Anion gap(mEq/L);Magnesium ion(mg/dL);PH;Bicarbonate(mEq/L);Lactic acid(mmol/L);PCO2(mmHg);EF(%)

4. Missing data codes: 
<list code/symbol and definition>n

Variables with missing data are common in the MIMIC-III, however eliminating patients with incomplete data can bias the study. Therefore, imputation is an important step in data preprocessing. All screening variables contained <25% missing values. For normally distributed continuous variables, the missing values were replaced with their mean values. For skewed distributions related to continuous variables, missing values were replaced with their median. There were no missing dichotomous variables in our study.

5. Specialized formats or other abbreviations used: 
