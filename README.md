👋 Hi, I’m Sreee, Here is what I did to complete this assignment.

- Creating Docker and Jmeter Image

1. This is not so complicated, pretty straight forward. Downloaded compatible latest docker, and installed it (I had done this before for Mac, but doing for windows for the first time)
2. Pulled the latest Jmeter image (chose one with highest pulls) from Docker Hub
3. To run the Jmeter Test plan in the container, used the following command - PS C:\Users\rge6551\desktop\JMeter\apache-jmeter-5.1.1\apache-jmeter-5.1.1\bin> .\jmeter -n -t GoogleAPI_JmeterTest_V1.jmx -l JMeterGoogleAPI_Results1.jtl
4. Go to the Jmeter folder, where the above result file .jtl is saved could open in xml to extract the results.
5. Could remove the container (optional though)

- Steps involved in running a googleAPI

1. Go to Google developer console, create an web application with the user name that you will be using to test the API (I used familypixbackup@gmail.com)
2. Activate the APIs that will be involved, I activated "Google Enterprise API". Google provides flexibility to try executing the APIs that we want like swagger. The API in the assignment, is under GMail API Rest Resources -> Users -> getProfile.
3. Outh 2 authorization is needed to run this API. Simple way to do this is using OAuth 2.0 playground. Authorize the APIs with the account you will be using for tests. Get Authentication code, use the code to generate token. Could have made more sophisticated with proper client ID and Secret code, where we could pull dynamically from JMeter script (I believe), but sorry I didn't have much time to finish this assignment.
4. This Bearer Token will later be passed in the JMeter header file. 

- Steps to create JMeter script

1. I have JMeter on my laptop already (its a simple opensource download, where it doesn't need any installation. Just open the .jar file directly)
2. Created a thread group with 2 HTTP requests, one API with valid ID, that would respond with HTTP 200 and the Json with expected user details. Other one with invalid user ID that would respond with Forbidden HTTP 403 error.
3. Added couple of listeners for results. 
4. Tried to add couple of test users through parameter config file, but in the interest of time added the static ID to the URL
5. Each API was run with 10 users for the 5 iterations.


- Executed this Jmeter test plan from the docker as mentioned above and extracted the results thru .jtl file.
- Results are as expected, 50% of them failed with forbidden errors, 50% of them passed with 200 responses.
- Latency had good contribution from the connecton time, could be first buffering as we ran only 5 iterations.
- Created a new github account, though I already have one. Didn't wanna use personal git :).
- Here we go, the result file could have been made look better with the modified the Jmeter config properties to add customized metrics, but again sorry, its a busy month at work. we are working evenings and weekends as well.









