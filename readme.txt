https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-tutorial-basic-deploy?view=azure-bot-service-4.0&tabs=csharp
https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-tutorial-basic-deploy?view=azure-bot-service-4.0&tabs=csharp#option-1-existing-app-service-plan

create an aad app with this command
az ad app create --display-name "QuizBotAPI" --password "newuser@123" --available-to-other-tenants

ID - 94ad2bff-50f3-4d94-a8ae-a6c1e75af53c
Password - newuser@123

- 
az deployment group create --resource-group "quizbotsevice-rg" --template-file "DeploymentTemplates\template-with-preexisting-rg.json" --parameters appId="94ad2bff-50f3-4d94-a8ae-a6c1e75af53c" appSecret="newuser@123" botId="QuizBotService-v6-21" newWebAppName="QuizBotService" newAppServicePlanName="QuizBotService-plan" appServicePlanLocation="West US 2" --name "QuizBotServiceDeployment"

_
az bot prepare-deploy --lang Csharp --code-dir "." --proj-file-path "LearnBot.csproj"

_

alternateively

upload code zup https://quizbotservice.scm.azurewebsites.net/ZipDeployUI

https://docs.microsoft.com/en-us/azure/app-service/deploy-zip


az webapp deployment source config-zip --resource-group "quizbotsevice-rg" --name "QuizBotService" --src ".\LearnBot.zip"
