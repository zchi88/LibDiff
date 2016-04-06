# LibDiff
A tool for computing and maintaining version diffences(diffs) in Android libraries.



## DEPENDENCIES
- Java 1.7+
- Procyon Decompiler version 0.5.30 


## GET THE TOOL
Simply clone this repository to your local machine.


## TRY IT OUT
The easiest way to use this tool is by creating a runnable Jar. To do so:

1. Import this project into Eclipse:

	```Eclipse
	File > Import > General > Existing Projects into Workspace 

	Select the folder where the tool is cloned to

	Click "Finish" to import this project into Eclipse
	```

2. Create a runnable JAR file:

	```Eclipse
	File > Export > Java > Runnable JAR file

	Choose a destination and name for the JAR

	Click "Finish" to create the runnable JAR
	```

## USAGE
This tool works on a directory which is a collection of libraries - the "Libraries Whitelist". 
This Whitelist is a collection of library JAR's or AAR's that must be manually collected and copied to the directory.
When new libraries are added to the directory, the tool will try to compute diffs for the library based on earlier versions of it.
The directory structure of this Libraries Whitelist directory MUST look like the following:

![Whitelist Directory Structure](https://github.com/zchi88/LibDiff/blob/master/LibDiff%20Structure.png?raw=true "Whitelist Directory Structure")

To use the tool to maintain the diffs for the Libraries Whitelist:

1. Open up a command line client
2. Change directory to `PATH/TO/LibDiffTool.jar`
3. Run the tool by typing the following command

	```console
	java -jar LibDiffTool.jar PATH/TO/WHITELIST_LIBRARIES
	```

4. Thats it! The tool will perform a startup scan upon starting up to make sure that diffs for libraries that are already present
have already been computed. Afterwards, it will continue to run and look for new libraries being added to the whitelist.

### NOTES
Every version for a library will have a ```diff.txt``` file create for it to log the files in the version of the library that are new, added, and deleted.
The exception to this is the very first version of the library in the whitelist, since there is no previous version to compare to. The ```diff.txt``` file 
for any JAR can be found in a directory named after its JAR. This directory exists in the same location as the JAR file.
