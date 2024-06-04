# WhatsApp for Business

Author: Matthew Teets


# Introduction

You can use the WhatsApp connector to send templated messages to any WhatsApp account.

The WhatsApp connector so far has the single capability that allows the user to fillout WhatsApp templated messages, and send them from the connector to a single users WhatsApp account. The connector cannot receive any messsages or input from the recipient of the templated messages, but takes care of all API requests and variable formatting.

You can use the WhatsApp connector to send: <br>
* Text message templates <br>
   * A message template that uses only text for both the header and body of the message
* Media message templates <br>
   * A message template that uses an image URL for the header of the message and text for the body
* Interactive message templates <br>
   * A message template that reads end user input on interactive buttons attached to the message


# Setup


## Resources

#### For information and setup help, see the following sections of the WhatsApp API documentation:
* WhatsApp API Documentation: <br>
   * [Send Message Template Overview](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-message-templates)
      * [Text-Based Message Template](https://developers.facebook.com/docs/whatsapp/message-templates/creation)
      * [Media-Based Message Template](https://developers.facebook.com/docs/whatsapp/api/messages/message-templates/media-message-templates)
      * [Interactive Message Template](https://developers.facebook.com/docs/whatsapp/api/messages/message-templates/interactive-message-templates)
   * [All API Parameters and Objects](https://developers.facebook.com/docs/whatsapp/on-premises/reference/messages#message-templates)

* DaVinci Documentation: <br>
   * [Login to DaVinci](https://portal.singularkey.com/dashboard)
   * [Import a flow from the Flow Library](https://docs.pingidentity.com/bundle/davinci/page/kaf1643656046958.html)
   * [Add Desired connector](https://docs.pingidentity.com/bundle/davinci/page/srw1637101394177.html)


## Requirements

#### To use WhatsApp connector:
* [Overview of Required Assets](https://developers.facebook.com/docs/whatsapp/business-management-api/get-started#1--acquire-an-access-token-using-a-system-user-or-facebook-login)
   * This will help you generate the required access token.
* [Current Graph API Version](https://developers.facebook.com/docs/graph-api/)
* [Message Template Creation](https://www.facebook.com/business/help/2055875911147364?id=2129163877102343)
   * [Message Template Guidelines](https://developers.facebook.com/docs/whatsapp/message-templates/guidelines) 


## Setting up the connector

#### WhatsApp Connector General Settings:
* Navigate to the WhatsApp connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner
* Search for the desired connector (in this case, WhatsApp).
* Click on the WhatsApp connector.
* From here you will see two text fields: Access Token and Version
   * Access Token:
      * Copy and paste your permanent access token into the corresponding text field.
   * Version:
      * The version will be filled out already.
      * Update the version if necessary.

# Using the connector in a flow

#### You can use the WhatsApp connector in a variety of use cases, such as:
* Sending customers an automated, personal welcome/goodbye message.
* Sending customers a confirmation message regarding a purchased product.
* Sending customers reminders about current or upcoming deals and promotions.
* etc...
---
#### Points to take into account when using the WhatsApp connector:
* The WhatsApp connector must have a trigger block before it will send any messages to the WhatsApp API (e.g. Custom HTML Message).
* The WhatsApp connector does not generate any output on its own.
   * To see the the raw output from the WhatsApp connector you can do the following:
      * Add a Custom HTML Message after your WhatsApp connector.  
      * Click on the HTML block and in the _**Message**_ text field select the circular angel bracket button
      * From the dropdown, select the WhatsApp connector
      * On the same line as the _**output (object)**_ click on the circular plus button
---
#### Pre-requisites to using WhatsApp connector in a flow:
* You must have a working permanent access token.
* You must have the current version of the graph API.
* You must have a valid and approved message template.
* You must have valid _**to**_ and _**from**_ WhatsApp phone numbes in order to send messages.
---

```
Once the WhatsApp connector is properly configured and added to the flow studio sandbox you will be ready to start 
sending templated messsages to your WhatsApp customers (all message use cases directly rely upon the users pre-approved
message templates).
```

## Text Message Template
```
Compatible with templates that use:
- Body variable(s)
```
```
Incompatible with templates that use:
- Text header variable
- Media header
- No body variable(s)
- Call to action buttons
- Quick reply buttons
```

#### Once inside of the flow studio:
1. Add a Custom HTML Messsage connector to the sandbox.
2. Drag the black circular node on the right-side of the HTML connector out and release.
3. Select the WhatsApp connector.
4. Click on the connector and select the **Send Message** capability.
5. In the _**Recipient**_ text field insert the desired WhatsApp phone number (the number of the account that will be receiving the message).
6. In the _**From Phone Number ID**_ enter the phone number ID of the device sending the message.
7. Click on the _**Message Type**_ dropdown menu and select the desired message template type.
   - In this case the type would be _**Text messsage template**_.
8. In the next text field labeled _**Text Message Template Name**_ copy and paste the pre-approved message template name you created in the WhatsApp Facebook Developer Dashboard.
9. Now fill out the variables you except in the template:
   - _**Variable Name**_ = arbitrary user-created, camel-Case name of your variable
      - Example: customerName
   - _**Value**_ = what you want to be inserted in the message
      - Example: Bob Smith
   - _**Data Type**_ = depends on what the value of your variable is
      - Example: String
10. The final _**Add**_ and _**Edit**_ buttons are used to add/manipulate variables.

#### Run the flow:
```
Once you have successfully filled out the necessary connector information you are ready to send.   
In the upper right-hand corner of the Flow Studio click: Save, Deploy, and the blue play button.
```

## Media Message Template
```
Compatible with templates that use:
- Image header
- Body variable(s)
```
```
Incompatible with templates that use:
- No body variable(s)
- Call to action buttons
- Quick reply buttons
```

#### Once inside of the flow studio:
1. Add a Custom HTML Messsage connector to the sandbox.
2. Drag the black circular node on the right-side of the HTML connector out and release.
3. Select the WhatsApp connector.
4. Click on the connector and select the **Send Message** capability.
5. In the _**Recipient**_ text field insert the desired WhatsApp phone number (the number of the account that will be receiving the message).
6. In the _**From Phone Number ID**_ enter the phone number ID of the device sending the message.
7. Click on the _**Message Type**_ dropdown menu and select the desired message template type.
   - In this case the type would be _**Media messsage template**_.
8. In the next text field labeled _**Media Message Template Name**_ copy and paste the pre-approved message template name you created in the WhatsApp Facebook Developer Dashboard.
9. The _**Media Message URL**_ text field is where you copy and paste the header image URL.
   -  Use only HTTP/HTTPS URLs.
11. Now fill out the variables you except in the template:
    - _**Variable Name**_ = arbitrary user-created, camel-Case name of your variable
      - Example: customerName
    - _**Value**_ = what you want to be inserted in the message
      - Example: Bob Smith
    - _**Data Type**_ = depends on what the value of your variable is
      - Example: String
12. The final _**Add**_ and _**Edit**_ buttons are used to add/manipulate variables.

#### Run the flow:
```
Once you have successfully filled out the necessary connector information you are ready to send.   
In the upper right-hand corner of the Flow Studio click: Save, Deploy, and the blue play button.
```

## Interactive Message Template
```
Compatible with templates that use:
- Body variable(s)
- Call to action buttons (either/both)
```
```
Incompatible with templates that use:
- Text header variable
- Media header
- No body variable(s)
- Quick reply buttons
```

#### Once inside of the flow studio:
1. Add a Custom HTML Messsage connector to the sandbox.
2. Drag the black circular node on the right-side of the HTML connector out and release.
3. Select the WhatsApp connector.
4. Click on the connector and select the **Send Message** capability.
5. In the _**Recipient**_ text field insert the desired WhatsApp phone number (the number of the account that will be receiving the message).
6. In the _**From Phone Number ID**_ enter the phone number ID of the device sending the message.
7. Click on the _**Message Type**_ dropdown menu and select the desired message template type.
   - In this case the type would be _**Interactive messsage template**_.
8. In the next text field labeled _**Interactive Message Template Name**_ copy and paste the message template name you created in the Facebook WhatsApp Developer Dashboard.
9. The _**Visit Website**_ button is handled during the creation of the message template, thus no configuration is required within the connector.
   - The same rules apply to the _**Call phone number**_ button, no configuration is required inside of the WhatsApp connector.
10. Now fill out the variables you except in the template:
    - _**Variable Name**_ = arbitrary user-created, camel-Case name of your variable
      - Example: customerName
    - _**Value**_ = what you want to be inserted in the message
      - Example: Bob Smith
    - _**Data Type**_ = depends on what the value of your variable is
      - Example: String
11. The final _**Add**_ and _**Edit**_ buttons are used to add/manipulate variables.

#### Run the flow:
```
Once you have successfully filled out the necessary connector information you are ready to send.   
In the upper right-hand corner of the Flow Studio click: Save, Deploy, and the blue play button.
```

# Capabilities

### Send Message Template (sendMessage)


Sends a WhatsApp message template to a phone number.

#### Recipient `textField` `required`


Recipient of the WhatsApp message.

#### From Phone Number ID `textField` `required`


WhatsApp from phone number ID.

#### Message Type `dropDown` `required`


WhatsApp message type


 - Text message template
 - Media message template
 - Interactive message template

#### Text Message Template Name `textField`


WhatsApp text message template name (from WhatsApp dashboard)

#### Media Message Template Name `textField`


WhatsApp media template name (from WhatsApp dashboard)

#### Media Message URL `textField`


Media URL for the image being sent.

#### Interactive Message Template Name `textField`


WhatsApp interactive template name (from WhatsApp dashboard)

#### Template Variables `variableInputList`


Variables for WhatsApp message template.

---

### Make Custom API Call (makeCustomApiCall)


Define a custom API call to WhatsApp Business.

#### Endpoint `textField` `required`


The WhatsApp Business API endpoint, such as "/messages/register/deregister/media/request_code".

#### From Phone Number ID `textField` `required`


WhatsApp from phone number ID.

#### Method `dropDown` `required`


The HTTP Method.


 - GET
 - POST
 - PUT
 - DELETE
 - PATCH

#### Query Parameters `keyValueList`


Add query parameters and provide their values.

#### Headers `keyValueList`


Add HTTP headers and provide their values.

#### Body `codeEditor`


The raw formatted JSON body.

---

### WhatsApp Message Webhook (webhook)


Webhook triggered when a message is received or message status has changed.

---


