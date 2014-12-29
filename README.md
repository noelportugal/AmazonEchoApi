AmazonEchoApi
=============

UPDATE: Check out an implementation https://github.com/noelportugal/AmazonEchoHomeAutomation

This is a simple way to login to Amazon and retrieve the unnoficial Echo API. I purposely didn't use Amazon SDKs so anyone can see how to simulate a login and implement with any language. The endoint investigation was done by Owen Piettes and can be found here http://www.piettes.com/the-amazon-echo-api/.

Here is a list of some the endpoints that are of particular interest to observe:
- TODOs:    https://pitangui.amazon.com/api/todos?type=TASK&size=1
- Cards:    https://pitangui.amazon.com/api/cards?limit=3
- Notifications:  https://pitangui.amazon.com/api/notifications

Basic Usage
=============
```
  AmazonEchoApi amazonEchoApi = new AmazonEchoApi("https://pitangui.amazon.com","username", "password");
  if (amazonEchoApi.httpLogin()){
    String output = amazonEchoApi.httpGet("/api/todos?type=TASK&size=1");
  }
```  
After getting output you can parse the JSON and do whatever you want. If you look at my AmazonEchoApi.java main, you will see that I check the TODO list every 15 seconds and store the itemId. If there is a new one then I go ahead and trigger whatever I want.

This example was build with Netbeans and runs in a Raspberry Pi. I included the following libs:
* HttpClient
* Simple-JSON
* JSoup
