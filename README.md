# Dynamically Generate Web Tests

[![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Froblohmann%2FAzure-CLI-Scripts%2Fmaster%2FCLI%2FWebtests%2Fazuredeploy.json)

This template will help you quickly spin up any number of [Application Insights](https://azure.microsoft.com/en-us/services/application-insights/) web tests and setup email alerts. The [parameters file](./azuredeploy.parameters.json) takes any number of test descriptor objects. These objects look like the following:

```json
{
    "name": "My Test",
    "url": "http://www.microsoft.com",
    "expected": 200,
    "frequency_secs": 300,
    "timeout_secs": 30,
    "failedLocationCount": 1,
    "description": "a description for test1",
    "guid": "cc1c4b95-0a39-48ce-9c7b-fa41f0fc0bee",
    "locations": [{
        "Id": "emea-nl-ams-azr"
	 }]
}
```

The `guid` field is an arbitrary guid for the test. The `locations` field is a collection of locations to perform the test from. Here is a table of the valid locations, and their corresponding `Id` code. Due to historical reasons, the `Id` code sometimes does not match the actual location where the webtest is occuring.

| Name                  | Id          |
| -------------         | ----------- |
| North Central US      | us-il-ch1-azr |
| West US               | us-ca-sjc-azr |
| South Central US      | us-tx-sn1-azr |
| East US               | us-va-ash-azr |
| Central US            | us-fl-mia-edge |
| Southeast Asia        | apac-sg-sin-azr |
| UK West               | emea-se-sto-edge |
| UK South              | emea-ru-msa-edge |
| West Europe           | emea-nl-ams-azr |
| Japan East            | apac-jp-kaw-edge |
| North Europe          | emea-gb-db3-azr |
| East Asia             | apac-hk-hkn-azr |
| France Central        | emea-fr-pra-edge |
| France Central (Formerly France South)     | emea-ch-zrh-edge |
| Brazil South          | latam-br-gru-edge |
| Australia East        | emea-au-syd-edge |


You can create any number of these test descriptors and pass them in as the parameter for `tests` as shown in the [parameters file](./azuredeploy.parameters.json).