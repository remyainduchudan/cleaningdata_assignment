Description of run_analysis.R
run_analysis.R takes source data from the UCI Har Dataset directory, imports it into R, and transforms it into a tidy data subset.

The script performs the following operations to import, clean, and transform the data set. These steps are also indicated in comments throughout the .R file.

Read the files from the test and training data and merge the training and test sets to create one data set.
Combine the values from the subject_test and subject_train files to create a single TestSubject column that identifies the study participant.
Combine the values from the Y_test and Y_train data to create a single Activity column that indicates that activity class (for instance, walking or sitting).
Combine the values from the X_test and X_train files to create additional variable columns, one column for each measurement and calculation included in the data set (561 variable columns total, in the initial combined data set; 563 columns including the TestSubject and Activity columns).
Clean up the column names to remove hyphens and parentheses and replace them with periods.
Extract only the measurements on the mean and standard deviation for each measurement.
Use the dplyr select function to create a subset of the data that only includes columns that have ".mean." and ".std." in their column names.
It's not required for the subset, but at this point the script also converts the test subject and activity columns to factors, to facilitate correct calculations later.
Use descriptive activity names to name the activities in the data set.
Use the mapvalues function to map the numeric activity values to descriptive names like "Walking" and "Standing."
Appropriately label the data set with descriptive variable names.
Use the stringr_replace_all function from the stringr library to do a number of find and replace operations on the column names. The details of the resulting descriptive names are included in codebook.md.
From the data set in step 4, create a second, independent tidy data set with the average of each variable for each activity and each subject.
Use split/apply/combine logic. First, split the data by the subject and activity factors using the split method.
Next, use lapply to iterate over each item in the resulting list, and use apply to apply the mean method to calculate the average of each column.
The output of lapply is a list, so combine it back to a data frame.
Use strsplit to break the subject and activity factors back into separate sets, and use cbind to properly bind them as the first columns in the resulting data set.
