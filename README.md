  PreRequisites: 
  1.  Sitecore Experience Platform 10.2.0 rev. 006766 
  2.  Install Sitecore ManagementServices 4.1.0 rev. 00492
  3.  Install currect Node version--> "node-v > 14.17.3"
  4.  Install currect Npm version--> "npm -v > 6.14.13"

1. Publish properties in gulp-config config object:
	    webRoot: "C:\\inetpub\\wwwroot\\sitecoreshadessc.dev.local",
        devRoot: "C:\SitecoreShades\SXA-Project\SitecoreShades",
        solutionName: "SitecoreShades",
        buildConfiguration: "Debug",
        MSBuildToolsVersion: 16.0

2.  Run following commands in sequence
		npm init      >>>       to create package.json
        npm install gulp@3.9.1 --save-dev
        npm install gulp-msbuild
        npm install gulp-debug
        npm install gulp-foreach
		    npm install run-sequence
		
3. Open Task Runner Explorer and refresh to see task updated
      -- alternatively from terminal --type the command "gulp" and enter

4. If you see "ReferenceError: Premordials not defined" after running Gulp - 
    1. Create a file at root level named npm-shrinkwrap.json
    2. Copy and paste following lines in that file:
        {
            "dependencies": {
              "graceful-fs": {
                "version": "4.2.2"
                  }
            }
          }
	  3. Run npm install again	

5. Serialization intial setup

      1. cd <project folder>
      2.dotnet new tool-manifest
      3.dotnet nuget add source -n Sitecore https://sitecore.myget.org/F/sc-packages/api/v3/index.json
      4.dotnet tool install -g sitecore.cli --version 4.2.1 --add-source https://sitecore.myget.org/F/sc-packages/api/v3/index.json
      5.sitecore init
      6.sitecore plugin add -n Sitecore.DevEx.Extensibility.Serialization --version 4.2.1
      7.sitecore plugin add -n Sitecore.DevEx.Extensibility.Publishing --version 4.2.1
      8.dotnet sitecore plugin add -n Sitecore.DevEx.Extensibility.Indexing --version 4.2.1
      9.dotnet sitecore plugin add -n Sitecore.DevEx.Extensibility.ResourcePackage --version 4.2.1
      10.dotnet sitecore --version

5.  Serialization steps
   Goto path "~\tools\serialization" and execute the powershell commands,

          > login.ps1  --> to save login details (need to performed first time only)
              >>execute "dotnet tool restore" (need to performed first time only)

          > pull.ps1  --> to serialize the changes from sitecore to git repository

          > push.ps1  --> to update sitecore content tree

          > validate.ps1  --> to fix any error in serialization like to remove orphaned items/folders
		

  
