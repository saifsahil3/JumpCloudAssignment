# JumpCloudAssignment
This repo contains manual test scenarios/test cases identified to validate Password Hashing application.
Please find bugs identified below
**#Bug1:**
Hashing algorithm is not SHA512. Decrypting the output of GET /hash doesnt return same value
Steps to reproduce:
1. Start the hash app
2. Create a password hash using POST to /hash. eg: "angryMonkey"
3. Get the encrypted value using GET request to /hash
4. Validate the value by decrypting the response and comparing with value in step 2

Expected: Both values should be same

Actual: Both values dont match

**#Bug2**
Failed POST requests to /hash are being counted in stats in total number of requests
Steps to reproduce:
1. Start the hash app
2. Send POST request to /hash with blank body
3. Get total requests count using GET /stats 

Expected: Total number of requests should be 0

Actual:  Total number of requests should be 0

NOTE: The above bug is based on assumption that invalid POST requests to /hash should not be counted

**AUTOMATION**
Automation is based on Postman. Import attached json files in Postman.

Configuration:
Update TD Environment values for 'Password' and 'PORT' to desired values

How to Execute:
1. Click on Runner in Postman. THis opens a Collection Runner
2. Select HashApp from collections
3. Select TD as environment from Environment dropdown
4. Click on Start Run
5. Validate test case results
![image](https://user-images.githubusercontent.com/58842419/162562643-12a79a43-68a7-4c9d-943d-6e3ecadb87c8.png)

This automation can also be triggered from Newman command line runner using node.js
