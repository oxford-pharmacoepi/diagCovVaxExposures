
diagCovVaxExposures- CohortDiagnostics package to assess Covid-19 vaccines
========================================================================================================================================================

## Running the analysis
1) Download this entire repository (you can download as a zip folder using Code -> Download ZIP, or you can use GitHub Desktop). If possible, avoid saving to a shared network drive as this can cause issues or in folders with a particularly long path.    
2) Open the project <i>diagCovVaxExposures/diagCovVaxExposures.Rproj</i> in RStudio (when inside the project, you will see its name on the top-right of your RStudio session)
3) Open the <i>diagCovVaxExposures/extras/CodeToRun.R</i> file which should be the only file that you need to interact with <ul>
<li> First, build the package (build -> install and restart)</li> 
<li> Then run <i>renv::activate()</i> and <i>renv::restore()</i> to bring in the required packages to be used</li> 
<li> Next, <ul>
<li> <i>outputFolder <- "...."</i>: Add your database specific information</li> 
<li> <i>options(andromedaTempFolder = "C/andromedaTemp")</i>: To specify andromedaTempFolder location </li> 
<li> <i>maxCores <- parallel::detectCores()</i>: To specify how many cores to use</li> 
<li> <i>connectionDetails <- createConnectionDetails(".........")</i>: These are the connection details for the 
<a href="http://ohdsi.github.io/DatabaseConnector">OHDSI DatabaseConnector</a> package.Note, this is v4.0.0 of DatabaseConnector and so you will need to have downloaded the relevant drivers (see <a href="http://ohdsi.github.io/DatabaseConnector/articles/UsingDatabaseConnector.html">here</a> for more details) and pass the <i>pathToDriver</i> argument to the <i>createConnectionDetails</i> command.</li>
<li><i>cdmDatabaseSchema <-"....."</i>: This is the name of the schema that contains the OMOP CDM with patient-level data </li> 
<li><i>cohortDatabaseSchema <-"....."</i>: This is the name of the schema where a results table will be created </li>
<li><i>cohortTable   <- "diagCovVaxExposuresCohorts"</i>: This is the name of the table that will be created in the results schema (which could be called "diagCovVaxExposuresCohorts" or something else - note, any existing table in your results schema with this name will be overwritten) </li> 
<li><i>databaseId <-"....."</i>: This is the short name/ acronym for your database</li>  
<li><i>databaseName <- "...."</i>: This is the full name of your database</li>  
<li><i>databaseDescription <- "...."</i>: A brief description your database</li>  
<li>After adding these details, you should then be able to run the line <i>diagCovVaxExposures::runCohortDiagnostics(...)</i> line which will run all of the required analyses. Once run, you can view you results by running the lines <i>CohortDiagnostics::preMergeDiagnosticsFiles(file.path(outputFolder, "diagnosticsExport"))</i> and <i>CohortDiagnostics::launchDiagnosticsExplorer(file.path(outputFolder, "diagnosticsExport"))</i></li> </ul>  

 
