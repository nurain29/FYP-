# Specialized Technology: Natural Language Processing (NLP)

## 1. Introduction to NLP

Natural Language Processing (NLP) is a field of Artificial Intelligence (AI) that enables computers to understand, process, and analyze human language. NLP can be used to analyze text written by customers in complaint messages. In the Customer Complaint Classification and Prioritization System for any website telecommunication , NLP will help analyze customer complaint text and classify complaints into categories such as network problems, billing issues, and customer service problems.

By automating text classification, the system will helps staff to identify urgent problem immediately without manual sorting.

## 2. How NLP Works

The following diagram shows how NLP work in the process of web-based customer complaint system.

Customer Submits Complaint
            |
            v
     Complaint Text
            |
            v
    Text Preprocessing
            |
            v
   NLP-Based Classification
            |
            v
   Predicted Complaint Category
            |
            v
 Display Results to Staff


The basic NLP process includes:

1. **Text Input:** The system receives a customer complaint as raw text.
2. **Text Preprocessing:** The text is cleaned and prepared to standardize words for analysis.
3. **Feature Extraction (TF-IDF):** Words are convert into numerical and weighted based on their frequency and needed
4. **Classification:** The system assigns the complaint to a suitable category.
5. **Output:** The system displays through staff web interface the predicted complaint category.

### 2.1 Worked Example

**Customer complaint:** "My internet has been disconnected for two days, and I cannot attend my online classes."

**Step 1 — Text Processing:** The text is standardize to lowercase and process symbols ("My internet has been disconnected for two days, and I cannot attend my online classes")

**Step 2 — Feature Extraction:** Highlight the importance keyword use such as "internet", "disconnected" are assigned high numerical weight using TF-IDF.

**Step 3 — Classification:** Prediction is made as category Network or Internet Connectivity issue from trained classification model.

**Step 4 — Result:** The categorized complaint are view in the staff web interface dashboard.

This is an illustrative example. The final priority depends on the membership functions and fuzzy rules defined for the system; the example does not represent a tested model result.

## 3. NLP Method and Tools

Natural Language Processing (NLP) is a collection of techniques and tools to process human language and extract useful information from text. 

In the proposed customer complaint classification system, NLP will be used to analyze the text submitted by customers and classify complaints into categories such as billing problems, network issues and poor customer service . Several methods and tools are needed to prepare the text, convert it into a format that can be understood by a machine learning model, classify the complaints, and evaluate the model performance.

### 3.1 Text Preprocessing

Text pre-processing is the first stage in preparing the customer complaints for analysis. The complaints will contain a mixture of upper and lower case, punctuation, various symbols and words which aren't really going to add much in terms of the classification. The text therefore needs to be cleaned and normalised prior to being fed into the NLP model.

Several pre-processing techniques can be employed including lowercasing all the text, removing all the punctuation and any other symbols that aren't relevant and the removal of certain stop words. Stop words are the 'normal' words such as “the”, “is”, 'and' etc which may not be of much use in some classification scenarios. They should be removed with care as some words do carry meaning. For instance 'not' is a crucial word in the complaint 'My internet is not working”.

For this project text pre-processing will be used to make the customer complaints more consistent prior to feature extraction. This will help to reduce some of the unecessary variation between the messages and get the text in a state to be used in the next stage. Pre-processing of the text does not in itself do the classification.

### 3.2 TF-IDF(Term Frequency-Inverse Document Frequency)

TF-IDF is a feature extraction technique which takes text and turns it into numerical values that a machine learning algorithm can work with. A computer model can't understand a complaint in the way a human can so the text has to be represented as numerical features. TF-IDF also looks at two main things. Term Frequency (TF) is a measure of how often a word appears in a particular complaint. Inverse Document Frequency (IDF) is a measure of how informative the word is across the whole dataset of complaints. A word which occurs quite frequently in a particular complaint but not so frequently across the whole dataset may be given a higher weight. The idea is to identify words which are useful in differentiating between complaint types.

For instance "invoice”, “overcharged" and “payment" would be indicative of a billing complaint whereas “signal”, “connection" and “internet” would be indicative of a network complaint. The words themselves don't tell you what the complaint is, they just provide the raw material which the TF-IDF then converts into features that the classifier can learn from.In this project TF-IDF will be used following text pre-processing and prior to the classification stage.The resulting numerical features will be the input to the Multinomial Naive Bayes algorithm. This is a perfectly valid approach to text classification as it provides a straightforward way of converting complaint text into numerical form (Scikit-learn developers, n.d.).

### 3.3 Multinomial Naive Bayes

Multinomial Naive Bayes is a supervised machine learning algorithm which is typically used for text classification. Supervised learning requires a labelled dataset so that each of your training complaints already has a category assigned to it. So you might have a dataset of complaints which have been manually labelled as billing, network or customer service for instance. The model learns the patterns from those examples and then uses those patterns to predict the category of a new complaint.

The algorithm uses probability to work out which category is most likely to be the one that matches the words and numerical features in a complaint. For this project the model will be using the TF-IDF features that were generated from the training data. Once trained it will be able to assign a category to a new complaint based on the patterns it has learned.

If the customer says “I was charged twice for my monthly bill" then the model will likely classify that as a billing complaint (as that's what the billing examples in the training data were all about). Of course that's not guaranteed to be right as it all depends on the quality and breadth of the training data.
Multinomial Naive Bayes is the algorithm we're looking at for this project as it's fairly straightforward to implement, it's computationally cheap and it's a fairly standard choice for a text classification problem. We can evaluate its performance on a separate test set using the usual metrics of accuracy, precision, recall and F1 score. These will tell us how well it's classifying the complaints and how many of the errors it's making between the different categories.

### 3.4 Scikit-learn

Scikit-learn is an open-source, free library for Python which allows creating and testing machine learning models. It can be used for all possible steps in developed NLP classification process, including feature extraction, model training, prediction and evaluation.

In this project, Scikit-learn will use TF-IDF vectorizer for transforming preprocessed complaint text into numeric features and Multinomial Naive Bayes implementation for training the model based on the labeled training dataset to understand the relationship between complaint text and categories of complaints. Once the training is done, the model will make predictions on non-classified complaints.
Scikit-learn library also has tools for evaluating classification results, e.g. confusion matrix to show which categories were predicted correctly and confused. Also, evaluation metrics like accuracy, precision, recall and F1-score provide additional information regarding performance of a model. 

Scikit-learn is appropriate for this project because it includes all the required methods in a single library and provides simple workflow at all stages from text preparation to model evaluation thus allowing reducing implementation complexity (Pedregosa et al., 2011).

### 3.5 How The Method Works Together

The methods mentioned above form a chain of actions in order to apply NLP to customer complaints classification. Firstly, text preprocessing standardizes and cleans the input by making all characters lowercase and deleting any superfluous signs. Secondly, TF-IDF transforms text data into numerical features for the machine learning model to operate with them.

Then, the Multinomial Naive Bayes algorithm uses extracted numerical features to classify complaints based on the patterns learned during model training on a labeled training dataset. The library scikit-learn enables to perform text feature extraction, classification model training, predictions generation, and their evaluation.

As an illustration, consider the case when the customer writes a complaint "My internet connection has been down for two days." After preprocessing, the sentence is transformed into numerical features by the means of TF-IDF, and then, the trained Multinomial Naive Bayes algorithm classifies the complaint in the Network or Internet Connectivity category.

Finally, the obtained prediction is displayed to customer service employees for their further work with the complaint. This solution allows reducing the necessity for manual classification of each complaint by the staff. Nevertheless, the quality of classification depends on the training dataset quality, and mistakes may occur with unfamiliar complaints.


## 4. Suitability of NLP for the Problem

Natural Language Processing (NLP) is suitable for this project because customer complaints are usually written in language. Customer complaints may describe problems using different words and sentences. For example a customer may write "I was charged twice" to report a billing problem while another customer may write "There is an error in my bill." Although the wording is different both customer complaints may belong to the billing category.
Manually reading and categorising a number of customer complaints can take time and effort. Therefore NLP can help automate the classification process by analysing customer complaints text and predicting the suitable category. In this project the system will classify customer complaints into selected categories, such, as billing problems, network or internet issues and poor customer service. The predicted category will help customer service staff identify the type of problem efficiently.

### 4.1 Benefits

**Automated Categorisation:** NLP can automatically classify submitted complaints into predefined categories. This reduces the need for staff to read and sort every complaint manually, helping to make the complaint management process more efficient.
**Consistency:** The classification model applies patterns learned from its training data when predicting complaint categories. This can help reduce differences that may occur when different staff members manually categorise similar complaints. However, the model may still make incorrect predictions.
**Scalability:** An NLP classification system can process many complaint messages without requiring staff to categorise each message individually. This makes the approach useful when the number of customer complaints increases, although processing speed depends on the system and available resources.
**Better Complaint Organisation:** By grouping complaints into categories, the system can make it easier for customer service staff to identify common issues. For example, staff can review complaints classified as network problems to understand the types of connectivity issues reported by customers.

### 4.2 Limitations and Risks

**Ambiguity and Slang:** Customer complaints might have slang, spelling errors, confusing sentences or than one issue in one message. These things can make it hard for the model to figure out the category. For example a complaint that talks about a bill and also an internet connection problem might not fit clearly into just one category.
**Dependence on Training Data:** The way well the classification model works depends on how good and varied the labelled training data's. If the data has few examples or doesn't match the way real customers actually speak the model might give wrong answers. So the data needs to have examples, for every type of complaint and needs to be checked with separate test data.
**Privacy Concerns:** Customer complaints may contain personal information, such as names, account details, or contact information. If this information is included in the dataset, it must be handled carefully. Unnecessary personal information should be removed or anonymised where appropriate, and access to complaint data should be restricted to authorised users.
**Classification Errors:** NLP does not guarantee that every complaint will be assigned to the correct category. Incorrect predictions may occur when a complaint contains unfamiliar words or differs from the examples used during training. Therefore, the model should be evaluated using suitable performance measures, such as accuracy, precision, recall, and F1-score. Staff should also be able to review the predicted category when necessary.

### 4.3 Alternative Approach

An alternative approach is keyword matching. This method uses rules that are set in advance to sort complaints based on words. For example if a complaint has the word "bill" the system might put it in the billing category. This way of doing things is easy to set up. It does not need a set of data that has already been labeled or a machine learning model.

Keyword matching has some problems. Customers might talk about the issue in different ways. For example a complaint that says "I was charged twice" could be about a billing problem. However it does not have the word "bill". A simple rule like this might not catch that complaint. More rules would need to be made for that to happen.

On the hand an NLP classifier that uses TF-IDF and Multinomial Naive Bayes can find patterns from complaints that have already been labeled. It uses these patterns to guess the category of messages. Even though how well it works depends on the quality of the data it is trained on this method is better for the project. It can learn from examples of depending only on rules made by people. So NLP classification is the choice, for the customer complaint classification system.
