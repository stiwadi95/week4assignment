# week4assignment
this is a part of Week 4 Assignment 

# Load the dplyr package
library(dplyr)

# View the top rows of the Titanic dataset
head(titanic_df)

library(dplyr)

# Load the Titanic dataset and convert it to a dataframe
titanic_df <- as.data.frame(Titanic)

# Rename the 'Sex' column to 'Gender'
titanic_df <- rename(titanic_df, Gender = Sex)

# Select the desired columns from the titanic dataset
titanic_select_df <- select(titanic_df, Survived, Gender)

# Remove the 'Gender' column from the titanic dataset
titanic_select_df <- select(titanic_select_df, -Gender)


# Create a new dataset with 'Survived' and 'Gender' columns
titanic_gender_df <- select(titanic_df, Survived, Gender)

# Filter the dataset to only include males
titanic_male_df <- filter(titanic_gender_df, Gender == "male")

# Group the dataset by gender
titanic_gender_grouped <- group_by(titanic_gender_df, Gender)

# Calculate the total number of people in the dataset #Total number of people = 2201
total_people <- sum(titanic_df$Freq)
print(total_people)

# Filter the dataset to only include females
titanic_female_df <- filter(titanic_gender_df, Gender == "female")

# Combine the male and female datasets
titanic_male_female_df <- bind_rows(titanic_male_df, titanic_female_df)
