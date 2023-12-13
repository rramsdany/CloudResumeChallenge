# CloudResumeChallenge
My attempt at Forrest Brazeal's Cloud Resume Challenge: https://forrestbrazeal.com/2020/04/23/the-cloud-resume-challenge/

# Link to my resume being hosted on my custom domain:

[My Resume](https://www.ramosdaniel-cloudresume.com/) 

## Challenge Steps:
**2. HTML**    
   Your resume needs to be written in HTML. Not a Word doc, not a PDF. Here is an example of what I mean.  
**3. CSS**    
   Your resume needs to be styled with CSS. No worries if you're not a designer - neither am I. It doesn't have to be fancy. But we need to see something other than raw HTML when we open the webpage.  
**4. Static Website**    
   Your HTML resume should be deployed online as an Azure Storage static website. Services like Netlify and Azure Static Web Apps are great and I would normally recommend them for personal static site deployments, but they make things a little too abstract for our purposes here. Use Azure Storage.  
**5. HTTPS**    
   The Azure Storage website URL should use HTTPS for security. You will need to use Azure CDN to help with this.  
**6. DNS**    
   Point a custom DNS domain name to the Azure CDN endpoint, so your resume can be accessed at something like my-c00l-resume-website.com. You can use Azure DNS or any other DNS provider for this. A domain name usually costs about ten bucks to register.  
**7. Javascript**    
   Your resume webpage should include a visitor counter that displays how many people have accessed the site. You will need to write a bit of Javascript to make this happen. Here is a helpful tutorial to get you started in the right direction.  
**8. Database**    
   The visitor counter will need to retrieve and update its count in a database somewhere. I suggest you use the Table API of Azure’s CosmosDB for this. (Use serverless capacity mode for the database and you’ll pay essentially nothing, unless you store or retrieve much more data than this project requires.)  
**9. API**    
   Do not communicate directly with CosmosDB from your Javascript code. Instead, you will need to create an API that accepts requests from your web app and communicates with the database. I suggest using Azure Functions with an HTTP trigger for this. They will be free or close to free for what we are doing.  
**10. Python**    
    You will need to write a bit of code in the Azure Function; you could use more Javascript, but it would be better for our purposes to explore Python – a common language used in back-end programs and scripts – and its Azure SDK. Here is a good, free Python tutorial.  
**11. Tests**  
    You should also include some tests for your Python code. Here are some resources on writing good Python tests.  
**12. Infrastructure as Code**    
    You should not be configuring your API resources – the Azure Function, the CosmosDB – manually, by clicking around in the Azure console. Instead, define them in an Azure Resource Manager (ARM) template on a Consumption plan. This is called “infrastructure as code” or IaC. It saves you time in the long run.  
**13. Source Control**    
    You do not want to be updating either your back-end API or your front-end website by making calls from your laptop, though. You want them to update automatically whenever you make a change to the code. (This is called continuous integration and deployment, or CI/CD.) Create a GitHub repository for your backend code.  
**14. CI/CD (Back end)**  
    Set up GitHub Actions such that when you push an update to your ARM template or Python code, your Python tests get run. If the tests pass, the ARM application should get packaged and deployed to Azure.  
**15. CI/CD (Front end)**  
    Create a second GitHub repository for your website code. Create GitHub Actions such that when you push new website code, the Azure Storage blob automatically gets updated. (You may need to purge your Azure CDN endpoint in the code as well.) Important note: DO NOT commit Azure credentials to source control! Bad hats will find them and use them against you!  
