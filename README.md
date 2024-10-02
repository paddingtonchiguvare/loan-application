# Loan application performance 
## Abstract
A model that predicts the performance of future loan applications was trained and tested. The model was used to predict the performance of 2,000 loans that are currently in Due Diligence (the test data).

## Design specifications
### Performance Evaluation.
The performance of each historical loan application was divided into three categories:
- The companies that paid on time (loan + profit)
- The companies that paid late but before 15 days (loan + profit)
- The companies that did not pay at all or paid part of the loan (loss)

The goal was to use bins to categorize the fraction of loan or profit paid back but there was not enough data to predict the profit.

## Training process

The tain loan data, train payment data and the test loan data were read in a jupyter notebook. We categorized the performance using the criteria mentioned above. However, it was discovered that the dataset was imbalanced. Roughly, 97,1 % of the loan applications in the training dataset were paid on time, 2.8 % were paid late but before 15 days, 0.079 % were not paid at all or part of the loan was paid. We oversampled the data to increase the size of the rare samples.

Identifier columns such as loan_id, business_id and credit_officer_id were not used in the training process. The columns used in the training process are the columns available before the loan is appproved. Numerical coulmns were scaled using a a stand scaler and categorical variables were converted to dummy variables.

## Results

Different models were trained and compared with each other. Hyper-parameter optimization was used to find the best hyper-parametere

### Decision trees

![image](https://github.com/user-attachments/assets/a44a5b4d-1032-4fdd-9dce-384be632c168)

The model predicts a high performance than the actual performance. Some of the cases were clientrs did not pay back the loan were predicted as if the customers paid. A few cases that was paid late but within 15 days were predicted correctly. The percentage of loans written off is closer to 0 %.


### Random forest

![image](https://github.com/user-attachments/assets/7e9ba2f1-eff4-4ffa-ad87-bdba912d5ab3)

Random forest perormed slightly better than decision trees as expected. The precision, recall and f1 score were slightly higher.


