# Early Warning Model for Post-Discharge Follow-Up Failure

## Problem Overview

Failure to complete timely outpatient follow-up after hospitalization is associated with higher readmission risk, missed clinical deterioration, and fragmented care coordination.  
Care teams often have limited capacity and must decide which patients to prioritize for outreach in the immediate post-discharge period.

## Intended Use

This model is designed as decision support for care coordinators, nurses, and social work teams.  
The output is a risk score used to prioritize outreach efforts, not to deny care or replace clinical judgment.

## Example Population
- Post-hospitalized patients
- Dialysis / chronic care used as illustrative case

## Data & Features (Simplified)
- Prior no-show history
- Comorbidity count
- Discharge diagnosis category
- Length of stay
- Recent hospitalizations
- Social risk proxy (e.g., transportation)

## Data Source

This project uses a synthetic dataset designed to approximate post-discharge patient characteristics and follow-up behavior.  
The dataset structure and feature distributions were informed by real-world clinical workflows and common documentation patterns, rather than by a specific proprietary dataset.

Synthetic data was chosen to allow transparent modeling, avoid data leakage, and focus evaluation on clinical tradeoffs rather than dataset artifacts.

The synthetic cohort was designed with an imbalanced outcome distribution (~20–30% follow-up failure) to reflect real-world care coordination challenges and to focus evaluation on clinically meaningful tradeoffs.

## Model Approach

A baseline logistic regression model was selected to prioritize interpretability and transparency.  
Model coefficients allow clinicians and stakeholders to understand which factors contribute to elevated risk and how care processes influence outcomes.

Some access-related features may show counterintuitive associations once care processes are accounted for, highlighting the difference between unmet needs and identified needs.

## Evaluation Considerations

Model evaluation emphasizes sensitivity, false negatives, and threshold tradeoffs rather than overall accuracy.  
Missed high-risk patients represent lost opportunities for early intervention, while false positives increase staff workload and risk of alert fatigue.

## Ethical Considerations
- Supports, does not replace, judgment
- Awareness of data limitations
- Avoids punitive use

## Limitations & Generalizability
- Synthetic data used for demonstration
- Performance not intended to represent real-world accuracy
- Framework applies beyond a single condition or specialty

## Plain-English Explanation for Clinicians

This model helps identify patients who may be at higher risk of missing their post-hospital follow-up appointment.  
Each patient receives a risk score based on information available at the time of discharge, such as recent hospitalizations, prior no-shows, access barriers, and whether follow-up was scheduled.

The model does not make decisions on its own.  
Instead, it helps care teams decide who may benefit most from early outreach when time and staffing are limited.

Risk thresholds can be adjusted based on team capacity and clinical priorities.  
The same model may be used differently depending on whether the goal is to avoid missed deterioration or to limit staff workload.

## What I Would Do Next with Real Data

With access to real-world discharge and follow-up data, next steps would include:
- Validating performance across different patient populations
- Collaborating with care teams to select operational thresholds
- Monitoring for bias and unintended workflow consequences over time
- Implementing a clinician override pathway to capture contextual risk not reflected in structured discharge data

