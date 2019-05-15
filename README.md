# serverless-survey

Thanks to this application, you will be to quickly generate your own serverless survey. Just fill out configuration file with questions which should be part of the survey and save your app. In just a few seconds, your survey will be available and you will be able to review results in DynamoDB table.

#### How to use it?
To modify the questions in the survey, just open 'config.yaml' file which you will find in your 'Survey' Lambda function. This is standard YAML file which let you you to add new remove questions from your survey.

Example file look like this:
```
Title: Serverless Survey
Author: Tomasz Stachlewski
Image: https://a0.awsstatic.com/main/images/logos/aws_logo_smile_1200x630.png
Theme: 282828
Questions:
    Question1:
        Type: ShortText
        Label: What is your email?
    Question2:
        Type: Text
        Label: What do you think about this survey?
    Question3:
        Type: Radio
        Label: Would you like to do it again?
        Values:
            Value1: Of course :)
            Value2: I don't think so...
            Value3: Maybe
    Question4:
        Type: CheckBox
        Label: What else would you like to see in this survey?
        Values:
            Value1: "Questions about my favourite programming language"
            Value2: "Statistics on tabs vs spaces adoption"
            Value3: "Other stuff"
    Question5:
        Type: Text
        Label: What could be improved?
```

#### How to access my survey?
After you modify the configuration file with your question and you save it, your survey will be available in the Internet. You can find the link in 'Survey' Lambda function in trigger section. Just check details of the "API Gateway" trigger - there should be 'Invoke URL' parameter.

#### Where are my results?
This application will generate two lambda functions and one DynamoDB table. Results of the survey are stored inside DynamoDB table. You can find it's name inside 'SurveySubmit' Lambda function - it will be the 'TABLE_NAME' environment variable.

#### Configuration

The configuration file (config.yaml) consists of following attributes:
| Attribute | Description |
| ------ | ------ |
| Title | The name of your survey |
| Author | Name of the author of the survey |
| Image | Link to the image which will be shown on the survey |
| Theme | Hex color which will be theme of the Survey |
| Questions | The list of the questions which should be included in the survey. |

Allowed questions types:
| Question type | Description |
| ------ | ------ |
| ShortText | Short, one line input area |
| Text | Longer input area |
| Radio | Multiple values options (True/False, etc.) |


Made with ❤️ by Tomasz Stachlewski. Available on the [AWS Serverless Application Repository](https://aws.amazon.com/serverless)

## License

Apache License 2.0 (Apache-2.0)
