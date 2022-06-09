# Azure-Function-App-calculator

This article provides details about how to use Visual Studio to develop C# class library functions and publish them to Azure.
Here we will Use Http Trigger to call an Azure-Function-App that sums the value of x and y and inputs a result The app is tested locally and later published to Azure and also tested in Azure using http as it's trigger.
These task requres A Visual Studio 2022 and Azure subscribed account 

# Firstly to create the Visual Studio Function App

Visual Studio lets you develop, test, and deploy C# class library functions to Azure.
1. From the Visual Studio menu, select File > "Create a new project".
2. In "Create a new project", search for "Azure Function", choose the Azure Functions template, and then select Next.
3. In Configure your new project, enter a Project name(Calculatortests) for your project, and then select Create. The function app name must be valid as a C# namespace, so don't use underscores, hyphens, or any other nonalphanumeric characters.
4. For the Create a new Azure Functions application settings, use the values: 
    *Function worker- .Net6
    *Function- HTTP Trigger
   *Authorization level- Function (If you choose the default level of Function, you're required to present the function key in requests to access your function endpoint)
 5. Select "Create" to create the function project and HTTP trigger function.
 6. After you create an Azure Functions project, the project template creates a C# project, The class was renamed to "sum" The function attribute was also renamed to "sum" The content of run method was deleted The logger was not deleted 
  
  Lines as shown below were added 
 > 
  int x =int.Parse(req.Query["x"]); 
  
  int y =int.Parse(req.Query["y"]);

int result = x + y;

return new OkobjectResult(result);

The parseInt method parses a value as a string and returns the first integer

more information about partInt can be gotten from this link https://www.w3schools.com/jsref/jsref_parseint.asp

the sum was calculated in the local environment using the link that was thrown to the debugger when pressed "Start Debugging/ctrl+f5"  http://localhost:7136/api/Sum?x=4&y=6
 
 # Secondly Creating Azure Function App
 Azure Functions lets you run your code in a serverless environment without having to first create a virtual machine (VM) or publish a web application.
 1. Sign in to the Azure portal with your Azure account.
 2. In the search bar, enter Function App and Create.
 3. On the Basics page, use the function app settings as specified in the following 
 *Function App name- calculatortests and others at default with your proper Region selected.
 4. On the Hosting page, enter the following settings. *Operating system- Windows *Plan- Consumption (Serverless-In this serverless hosting, you pay only for the time your functions run)
 5. Select "Review + create" to review the app configuration selections.  
 6. On the "Review + create" page, review your settings, and then select "Create" to provision and deploy the function app.
 7. Select "Go to resource" to view your new function app. You can also select Pin to dashboard. Pinning makes it easier to return to this function app resource from your dashboard.
 
 # Lastly deploying from Deploy your code to Azure
 1. Search for "Publish" Select Azure / Right-click on the project in Solution Explorer and select "Publish"
 2. Then select "Azure function App (windows)" Click Next.
 3. Then choose Select Existing. 
 4. "Select Finish", and on the Publish page, select "Publish" to deploy the package containing your project files to your new function app in Azure.
 5. After the deployment completes, the root URL of the function app in Azure is shown in the Publish tab.
 6. From the left menu of the Function App window, select "Functions" 
 7. Select "Get function url" 
 8. The sum was calculated in Azure platform using the link that was gotten from "Get function url" in the function tab of azure function app that was created earlier: https://calculatortests.azurewebsites.net/api/Sum?code=OSpJGrRT9wz8Pcgx3w8SdhM7mY6cGge_Vw1ZRW7tEIVCAzFu-EG8fg==&x=6&y=4

Thank you for Reading.
