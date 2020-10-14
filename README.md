# mod17Challenge

<!-- You will:

1. Oversample the data using the RandomOverSampler and SMOTE algorithms.
2. Undersample the data using the cluster centroids algorithm.
3. Use a combination approach with the SMOTEENN algorithm.
For each of the above, you’ll:

Train a logistic regression classifier (from Scikit-learn) using the resampled data.
Calculate the balanced accuracy score using balanced_accuracy_score from sklearn.metrics.
Generate a confusion_matrix.
Print the classification report (classification_report_imbalanced from imblearn.metrics).
Lastly, you’ll write a brief summary and analysis of the models’ performance. Describe the precision and recall scores, as well as the balanced accuracy score. Additionally, include a final recommendation on the model to use, if any. If you do not recommend any of the models, justify your reasoning. -->

### Analysis results

### 1. Oversample the data using the RandomOverSampler and SMOTE algorithms.
These methods gave almost identical results.  For these methods, the precision and the F1 score for predicting fraud were very different in the two groups.  Of transactions predicted to be fraudulent, the precision was only 0.01, meaning that only 1% of transactions that are predicted to be fraudulent actually are.  This measure also drove a very low F1 score of 0.03.

The balanced accuracy score for both models was 0.77, which is similar to the macro average recall of 0.74.  This indicates that the recall was similar within and across groups.

### RandomOverSampler
balanced accuracy score: 0.7719640846512104
confusion_matrix: array([[17705,  6343],
                        [   20,    84]], dtype=int64)
classification_report:
                   pre       rec       spe        f1       geo       iba       sup

        0.0       1.00      0.74      0.81      0.85      0.77      0.59     24048
        1.0       0.01      0.81      0.74      0.03      0.77      0.60       104

avg / total       0.99      0.74      0.81      0.84      0.77      0.59     24152

### SMOTE
balanced accuracy score: 0.7726038307999386
confusion_matrix: array([[17967,  6081],
                         [   21,    83]], dtype=int64)
classification_report:
                   pre       rec       spe        f1       geo       iba       sup

        0.0       1.00      0.75      0.80      0.85      0.77      0.59     24048
        1.0       0.01      0.80      0.75      0.03      0.77      0.60       104

avg / total       0.99      0.75      0.80      0.85      0.77      0.59     24152

### 2. Undersample the data using the cluster centroids algorithm.
The cluster centroids algorithm yielded the same precision and F1 scores that the first two models did, with a precision and F1 score for predicting fraud that were very different for the two groups (precision, 0: 1.0, 1: 0.01; F1, 0:0.85, 1:0.03).  

The balanced accuracy score for this model was 0.67, compared to the macro average recall of 0.51.  This indicates that this algorithm had somewhat different recalls for the two groups. 

balanced accuracy score: 0.6770897307948206
confusion_matrix:
array([[12217, 11831],
       [   16,    88]], dtype=int64)
classification_report:
                   pre       rec       spe        f1       geo       iba       sup

        0.0       1.00      0.51      0.85      0.67      0.66      0.42     24048
        1.0       0.01      0.85      0.51      0.01      0.66      0.44       104

avg / total       0.99      0.51      0.84      0.67      0.66      0.42     24152


### 3. Use a combination approach with the SMOTEENN algorithm.
The SMOTEEN algorithm yielded the same precision and nearly the same F1 scores that the first three models did, with a precision and F1 score for predicting fraud that were very different for the two groups (precision, 0: 1.0, 1: 0.01; F1, 0:0.86, 1:0.03).  

The balanced accuracy score for this model was 0.79, compared to the macro average recall of 0.75.  This indicates that the SMOTEEN algorithm had similar recalls for the two groups. 


balanced accuracy score: 0.7871724499718511
confusion_matrix:
array([[17974,  6074],
       [   18,    86]], dtype=int64)
classification_report:
                   pre       rec       spe        f1       geo       iba       sup

        0.0       1.00      0.75      0.83      0.86      0.79      0.61     24048
        1.0       0.01      0.83      0.75      0.03      0.79      0.62       104

avg / total       0.99      0.75      0.83      0.85      0.79      0.61     24152


### Final Model Recommendation
Although the models yielded very similar results, the SMOTEEN algorithm was the same or marginally better on both the balanced accuracy score and the macro average recall.  If I were to use this model, I would want to do a second round of modelling on the positive predicted results only, to try to increase the precision of this prediction.