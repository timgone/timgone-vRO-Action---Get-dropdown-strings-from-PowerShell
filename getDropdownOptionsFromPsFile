// Create a variable for PowerShell cmdlet Get-Content -Path
var psCmdlet = "Get-Content -Path";

// Grab first PowerShell host
// [0] specifies the first host, [1] would specify the second
var psHosts = Server.findAllForType("PowerShell:PowerShellHost",null);
var psHost = psHosts[0];

// Open a session on the PowerShell host and save the sessionID
var session = psHost.openSession();
var sessionId = session.getSessionId();

// Run the cmdlet on the PowerShell host using the file path input from the workflow
// e.g. filePath syntax should look like c:\folder\file.txt
// Save the output as type PowerShellInvocationResult
var psResult = session.invokeScript(psCmdlet + " " + filePath);

// Close the session on the PowerShell host using the sessionID
psHost.closeSession(sessionId);

// Change output type from PowerShellInvocationResult to string
var psHostOutput = psResult.getHostOutput();

// Split the string into an array using each new line as the separator
// Filter out empty lines
var psList = psHostOutput.split("\n").filter(String);

// Send the variables to vRO log when troubleshooting the action's code in a standlone workflow run
System.log ("The psCmdlet variable is a string type with this value: " + psCmdlet);
System.log ("The psHosts variable is an array of PowerShellHost object type with this value: " + psHosts);
System.log ("The psHost variable is a PowerShellHost object type with this value: " + psHost);
System.log ("The session variable is a PowerShellSession object type with this value: " + session);
System.log ("The sessionId variable is a string type with this value: " + sessionId);
System.log ("The psResult variable is a PowerShellInvocationResult object type with this value: " + psResult);
System.log ("The psHostOutput variable is a string type with this value: " + psHostOutput);
System.log ("The psList variable is an array of string type with these values: " + psList);

// Send the newly created array of strings out of the this action
return psList;
