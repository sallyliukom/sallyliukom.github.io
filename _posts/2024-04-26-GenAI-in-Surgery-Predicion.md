---
layout: post
title:  "GenAI Application in Surgery Predicion"
date:   2024-04-26 09:52:29 -0700
categories: GenAI in healthcare
---
### Background
In my previous role, I was involved in a project that focused on predicting whether patients would require MSK surgery within the next 6-9 months. Clinical experts suggest that up to half of such surgeries, often aimed at addressing chronic pain, could potentially be avoided. Our team's goal was to identify patients at high risk of undergoing unnecessary procedures. Once identified, our engagement managers would reach out to these individuals to offer an alternative in the form of digital physical therapy. This service, provided by my previous company in collaboration with our clinicians, featured tailored treatment plans designed to mitigate the need for surgery.
### Algorithm Development
Our project utilized a dataset comprising medical claims data from customers, which included essential diagnosis and procedure information encoded in ICD and CPT codes. To leverage this data, we initially developed a predictive model.

**First Version**: We opted for a tree-based model due to its simplicity and high interpretability. This model was designed to evaluate the likelihood of a patient undergoing MSK surgery based on their medical history.

**Feature Engineering**: One critical aspect was the creation of features based on the number of medical encounters. For example, we quantified how many doctor visits a patient had in the six months leading up to a potential surgery. This approach helped us capture the intensity of medical consultations related to their conditions.

**Incorporating Time-Series Analysis**: As the project evolved, we recognized the need to incorporate time-series characteristics to enhance our model’s accuracy. The timing of certain medical events, such as MRI scans, appeared to have varying levels of importance depending on when they occurred relative to the predicted surgery date. To address this, we segmented the features into different time frames—capturing data such as the number of doctor visits in the past three months or the occurrence of MRI scans between three to six months prior. This method allowed us to fine-tune our understanding of the data’s temporal dynamics and their impact on surgery likelihood.

### Limitations
**Challenges with Sequence Dependency**: A significant limitation of our initial algorithm was its inability to capture the dependencies and sequences of medical events. For instance, consider the typical sequence of a patient's medical interactions: a doctor's visit is coded with an ICD code, followed by an MRI scan indicated by a CPT code. The doctor then reviews the MRI results and possibly prescribes physical therapy leading up to another consultation, where the decision about surgery is made.

Our previous feature engineering approach, while effective in capturing data within specific time frames, failed to recognize the importance of the order and progression of these events. The sequence in which the events occurred — crucial for understanding patient treatment pathways — was not accounted for in the model. This oversight could potentially lead to suboptimal predictive performance, as the contextual relationship between sequential medical events is a critical factor in determining the necessity for surgery.
### Future Work

