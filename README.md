<font size="6">1. Data Modelling</font>

<font size="4">Congratulations! You have been successfully hired as the new Data Engineering and Management team in the AirBNB Business Intelligence department. 
The organization is undergoing restructuring as the performance of the previous teams was not believed to be satisfactory.

Before leaving their post, the head of the Data Modelling department left this note of identified issues.

Currently a lot of data related to AirBNB listings is all collected in the same document. While this has some advantages it has also caused issues. The query performance is known to be too slow, so some decisions on hybridization of data models are required. The previous team did not have experience in the application of patterns, which has been identified as a key area to improve performance through the enhancement of the data model. Indexes have also not been previously applied.

The AirBNB application use has been growing rapidly, especially the the number of reviews. Because of that we have been overwriting them regularly, but the business intelligence department will benefit from storing all the Reviews and analysing them over time. 

Finally, there are some mistakes in the data collection : for instance, writing the same data multiple times, and assigning wrong timestamps for when transactions occurred. The new team will need to decide how to address these.   

In your new role, you are expected to think about the database use case in each question, analyse all the information you have, how commonly is this query needed, how heavy will it be on reads and write etc. You should modify the database schema, where you deem appropriate, to optimise for the business use cases. To do so you should use all the tools you have learned in the lab and lectures, especially embedding and linking, indexes, and patterns. This can involve creating new fields, documents, and collections. Indicate which pattern you are applying and your reasoning for doing so in comments, remember to identify any duplication that is required and any risks of staleness. 

Remember to think about the relevancy of all data that will be returned in each case and if this is needed or adding excessive time to return:
1. to streamline the data collection system;
2. to clean up the data and optimise what will be returned for each use case;
3. to use correct patterns to improve speed of typical queries;
4. to ensure that all departments receive correct and relevant information from the database;
5. to provide the data model schema to inform other departments of the changes.

Good practices in our company include:
1. all newly created fields have CAPITALIZED names;
2. all new queries function on the most updated version of the database (if you make multiple changes all your queries still work after the final changes);
3. for some of the queries you will likely want to change the database schema in some way. Each database transformation choice is properly documented using format:
    * `TRANSFORMATION APPLIED: <NAME and DESCRIPTION OF TRANSFORMATION>`
    * `REASONING BEHIND: <WHY YOU DID IT>`
    * `EXPECTED RESULT: <WHAT IS THE (EXPECTED) RESULT OF RUNNING QUERIES GIVEN THIS TRANSFORMATION>`

</font>


**Initial data setup:**

Before starting on the queries below review the data and look to adjust the schema for the typical use case described below.

1) The most typical use case for the database is to show information relating to a property listing to a customer. This is done by a query to the database which returns one of the listing documents. Currently a lot of time is spent when a listing is retrieved from the database to show to a customer. Decide what information should be returned in a typical query and optimise the structure for this use case. For example, we typically only want a sample of reviews but not all reviews (although all reviews ), the customer does not need to know past transaction data, etc. Update the document schema for this typical use case. This may involve the creation of new collections and documents.  

2) Review the data for any errors (such as transactions that don’t fit the listing) or inappropriate duplication and clean up as appropriate. 


<font size="6">2. Uses for the database</font>

<font size="4">Different AirBNB departments require different analytics from our common database.
Here are the list of all specific questions from different departments: 

**Standard Dificulty Questions:**

3)	Once per month we like to reward hosts with recognition. Pick three superhosts who have at least two property listings that can accommodate more than four people?

4)	One of employees is thinking of buying a property to rent out. Which bed type is most common in the listings that have waterfront and a dishwasher in New York?

5)	We are thinking of identifying someone to hire to write review for us professionally. What is the name of the reviewer who left the longest review in New York?

6)	We are thinking of trying to assess the security of different areas based on the security deposit required. What is the biggest and smallest difference between the price and deposit for security per number of visitors staying at the property?

7)	We want to identify areas by whether they are typically used for short breaks, like weekend mini breaks, or whether they are more suitable for long trips. We will use this information to target advertising of different customers. It is not expected this information will change much over time so we won’t look to update it we just would like a current view. What is the average duration of stay (in nights) per type of property per city (you can use the maximum_nights to measure length of stays)? For each property type return the city with the highest and lowest average value.

**Advanced Dificulty Questions (Remember to consider how to optimise the database for these queries):**

8)	We want to have a new webpage for hosts when setting up their account. It will list suggested typical amenities. This data will need to be available every time a host registers a property but is not expected to change very much. The starting point for the list will be all unique amenities currently listed in properties (across all documents). Optimise the database for this use case and show how the data should be queried.

9)	We want to start tracking our reviewers better. We want to create a webpage that shows the top 20 reviewers and the count of the number of reviews of each of these reviewers. This webpage should be kept up to date. It should also have a link to return the number of reviews for a given reviewer ID or Name (show how to query for number of reviews by ID or query quickly).


10)	For each property we store review scores across different metrics (accuracy, check-in, cleanliness etc). We are thinking we may soon add more metrics, although we don’t know what these will be. We want to be able to easily query the average score across all of these metrics, including any new metrics that might be added without changing the query. Adjust the data model so this can be done and show the query for an example property.

11)	We wish to be able to have better access to information about transaction, we wish to develop a search engine that can calculate the average value of transactions in a given period of time quickly for a given property.


12)	We wish to have a summary webpage that displays information about our top destinations. This webpage should display for each of the top 10 cities some basic information about our operations in the area (number of properties by type for example, average price by type) but you can choose the metrics. For each of the top 10 cities it should also provide some basic information about the top 3 properties in each city (price, number of review, whatever you think useful) to show an example of the properties available in the area. We would like to keep this webpage up to date as information changes.

**Database updates:**

After you have completed the above tasks and have optimised your database show how you would complete each of the updates below. You can create whatever fictional data you like for the below. Remeber to cosider how to prevent any data you have previously created from becoming stale.

13)	Add a new property, this property should have a new host, and should be located in one of the top 10 cities. The host selects the top 10 most common amenities to be listed for the property.

14)	Add a new review to this property, the review should be from one of our top 20 reviewers.

15)	Add a new review metric called x_factor to the new document and give a score of 10. Show that the average across all metrics is correctly calculated for this listing, with the query you previously developed.
