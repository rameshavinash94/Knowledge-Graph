**Team:** Data Miners

**Team Members:**
1. Avinash Ramesh
2. Poojashree NS
3. Abraham Kong

**MAIN COLAB TO RUN:** https://github.com/rameshavinash94/cmpe257_final_exam/blob/main/CMPE257_Data_Miners_Final_Exam_All_Sections.ipynb

**Our KG gif:**
!['ke of coinbase'](https://github.com/rameshavinash94/cmpe257_final_exam/blob/main/KE_gif.gif?raw=true)


**Meet with team to discuss what factors you would/should investigate to make an investment decision!! What factors [think about the way you did AlternusVera for factors and microfactors] need to know about the company it's products it's partners and customers and officers ??**

As a team we went through couple of "[articles](https://investinganswers.com/articles/important-factors-before-investing-company)" to get factors and microfactors that helps to decide weather to invest in a company or not.

After discussion, we understanded the requirements and found out few stuff and came up architecture similar to this.

![](https://github.com/rameshavinash94/cmpe257_final_exam/blob/main/image%20(1).jpg?raw=true)

**here instead of wikipedia, user would type in a company and we amalagamated data from multiple sources.**

**API'S**

FINANCIALMODELINGPREP - extract the financial details of the company https://site.financialmodelingprep.com/

PEOPLESDATA - extract the comapany details from peoplesdata api https://www.peopledatalabs.com/

NEWSAPI - extract the news related to company using company name https://newsapi.org/

**SCRAPPER:**

CRUNCHBASE to extract other import info about the company https://www.crunchbase.com/


The below vidoe gave us a broaded picture of what can be done and how to proceed.
https://www.youtube.com/watch?v=nYQLp7itZx8 


**Find people in the news connected with the company. Find product announcements, partnerships, rounds of funding news + crunchbase**

Data to perform the analysis has been scraped from crunchbase and extracted finianial data and company info form the above mentioned api's and get relevant news data from news API. Crunch base also provides the data related people and their relationship with the company, funding, financial model, along with that we have also considered similar companies, technologies and descriptions.
We have amalgamated all the data and performed grammer corrections with coreferencing as a preprocessing to graph.

**Traversal Algorithm : graph sage as an example.Traverse the graph and deposit the textual info in a text file as the output of the research project**

One we have the Amalgamated date, our process goes through various pharases to generate relevant Knowledge graphs.


1. PERFROM NLP PREPROCESSING OPERATIONS USING SPACY
2. ADD SVO TRIPLETS TO GRAPH
3. UPDATE NODE LABES AND PROPERTIES with the help of Google Knowledge graph search api.
4. DEDUP AND CLEAN THE GRAPH
5. BUILD GRAPH
6. GENERATE GRAPH EMEDDING
7. If tIme, Permits some ML

We used neo4j to store the knowledge graph. Neo4j also has abilities to traverse the graph and display the relationship bewteen nodes in any format.
We also stored embeddings of each node as a node property.


**Example KE we generated for firm: Coinbase.**


<img src="https://github.com/rameshavinash94/cmpe257_final_exam/blob/main/graph%20(2).png?raw=true" width="250"></img>

LINK FOR VISUALIZATION: 

<a href="https://9cdc6da62c21d3a11ccc8ec585ee8f47.neo4jsandbox.com/browser/?token=pwfetch:9cdc6da62c21d3a11ccc8ec585ee8f47:eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlFUbENPRVV4UmtJNFJETkROakpETXpBME5EZzBRelV3UWpNek9UVTVNRFF4TlRKRk56STJOZyJ9.eyJlbWFpbCI6ImF2aW5hc2gucmFtZXNoQHNqc3UuZWR1IiwiZmFtaWx5X25hbWUiOiJSYW1lc2giLCJnaXZlbl9uYW1lIjoiQXZpbmFzaCIsImxvY2FsZSI6ImVuIiwibmFtZSI6IkF2aW5hc2ggUmFtZXNoIiwibmlja25hbWUiOiJhdmluYXNoLnJhbWVzaCIsInBpY3R1cmUiOiJodHRwczovL2xoMy5nb29nbGV1c2VyY29udGVudC5jb20vYS9BQVRYQUp3SXNjMDFPQWtzcFRiTnVZM1A5bHBHMkl2RzktY3VGMHVhVzV3PXM5Ni1jIiwidXNlcl9tZXRhZGF0YSI6eyJjb21wYW55IjoiU3R1ZGVudCJ9LCJhcHBfbWV0YWRhdGEiOnsic2FuZGJveHYzIjp7ImNyZWF0ZWRBdCI6MTY1MzMzNzQ1ODIyMiwiYWdyZWVkVG9UZXJtc0F0IjoxNjUzMzM3NDY2NzQ0fX0sInNhbmRib3h2MyI6eyJjcmVhdGVkQXQiOjE2NTMzMzc0NTgyMjIsImFncmVlZFRvVGVybXNBdCI6MTY1MzMzNzQ2Njc0NH0sImZpcmViYXNlX2RhdGEiOnsidWlkIjoiZ29vZ2xlLW9hdXRoMnwxMTgxODc1NDA3MDUxMzcwMzY0MzcifSwic2NvcGVzIjp7InNhbmRib3hlcyI6WyJzYm94MSIsInNib3gyIiwic2JveDMiXX0sImNsaWVudElEIjoiRHhobWlGOFRDZXpuSTdYb2kwOFV5WVNjTEdabms0a2UiLCJjcmVhdGVkX2F0IjoiMjAyMi0wNS0yM1QyMDoyNDoxNi4zNDVaIiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImlkZW50aXRpZXMiOlt7InByb3ZpZGVyIjoiZ29vZ2xlLW9hdXRoMiIsInVzZXJfaWQiOiIxMTgxODc1NDA3MDUxMzcwMzY0MzciLCJjb25uZWN0aW9uIjoiZ29vZ2xlLW9hdXRoMiIsImlzU29jaWFsIjp0cnVlfV0sInVwZGF0ZWRfYXQiOiIyMDIyLTA1LTIzVDIwOjI0OjMyLjYyMVoiLCJ1c2VyX2lkIjoiZ29vZ2xlLW9hdXRoMnwxMTgxODc1NDA3MDUxMzcwMzY0MzciLCJpc3MiOiJodHRwczovL2xvZ2luLm5lbzRqLmNvbS8iLCJzdWIiOiJnb29nbGUtb2F1dGgyfDExODE4NzU0MDcwNTEzNzAzNjQzNyIsImF1ZCI6IkR4aG1pRjhUQ2V6bkk3WG9pMDhVeVlTY0xHWm5rNGtlIiwiaWF0IjoxNjUzMzM5MjA1LCJleHAiOjE2NTM0MjU2MDUsIm5vbmNlIjoiWm01blVISTVZVlp1VWt0d1IyTjFVbVJSYjNWcVExcEtMbEpqUzJsalRscFlkRmxvUW5Wb2IzWmFUZz09In0.fy82GKMn19MU2yZTXZfTVjvP2dxLVMTtsBwsWy4nDriQnF5YBNh3OQEWgOKjvbQEHsKD_04z_gTS0PLabMjbXm7Au0XpkLqlgKOBxJgjil5FtkgJmnu--2EM5gxmZD32RblEiwRrf-qHG9ToLvxxVZgtJwuUHB7PMKMxzEIJPgLc60drCH-lMDbBOILp_Q1CGtO36z-Cp0k9HkZffCLehdXuN7ac155XBFnLltzf3KG9O14jscnFLchsXocJObRlv-8aXAaA8iF-bP38-S_9oUdXQ4gh2sVgzkQbFoodt1ozgmiat5yGsL36hr2SKchMfi-75g6G_9Nt-qlN5PdLUw"> Click here to visualize the graph in Neo4j Browser</a>

RUN THE BELOW CYPHER QUERY to GET GRAPH OUTPUTS

```MATCH (n) RETURN n```

We used Cypher a declarative graph query language that allows for expressive and efficient data querying in a property graph.

**The format of the output should be easily consumable by a HUMAN!!**

For human understandable format we are summarizing the data obtained from graph and displaying it. So the end user can read the summary about the company and decide where to invest or not.
Also, the final source, target and relationship of nodes are traversed from KE and finally stored in text file.

***We have also provided the option for the end user to provide the company name that they are interested in investing and builts knowledge graph dynamically and provides him with all important info and summary about the company.***

**KNOWN ISSUES AND SOLUTION:**

1. Importing Spacy needs a restart of runtime after installaiton.
2. CRUNCHBASE SCRAPPING MAY NOT WORK SOMETIMES AND SOME DATA MAY BE LOST DURING DATA AMALGAMATION
3. NOTE OUR GRAPH DB CONNECTION WILL BE LOST IN ANOTHER 3 DAYS BECAUSE OF FREE TRIAL
