# gradle-sourceSets-buildFailure-Windows
https://discuss.gradle.org/t/using-sourcesets-along-with-jar-task-in-gradle-build-causing-build-failure-in-windows-due-to-duplicatestrategy-not-being-set/47034 this disucssion has the required context

Steps to reproduce the error
OS: windows 11 (not reproducible in macOS)
create a new gradle project with following setting
project type: 2 (application)
implementation language: 3 (java)
Split functionality across multiple subprojects?: 1(no)
build script dsl: groovy dsl
test framework: 4

add the following code snippet in the build.gradle file

sourceSets {
    main {
        resources {
            srcDir 'src/main/resources'
        }
    }
}

add a random file in the src/main/resources dir

the following error message is printed, when the following commands are executed

`
gradle clean build
./gradlew clean build
./gradlew.bat clean build
`

> Task :app:processResources FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:processResources'.
> Entry testPurpose.txt is a duplicate but no duplicate handling strategy has been set. Please refer to https://docs.gradle.org/7.6.1/dsl/org.gradle.api.tasks.Copy.html#org.gradle.api.tasks.Copy:duplicatesStrategy for details.