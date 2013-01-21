# Ratpack

## A Micro Web Framework for Groovy

This project is the core Ratpack code. It is of interest to developers wanting to extend the Ratpack framework itself—which hopefully means you!

If you just want to use Ratpack to build a small, Groovy-based web app, then you want the [Ratpack Template](https://github.com/tlberglund/ratpack-template). Go clone that, write your code, and come on back here when you want to hack on the framework.

## Running With Groovy

Put some route definitions in `ratpack.groovy` (in any empty directory), e.g.

    get("/") {
        renderString  "Hello World"
    }

and then run this program (after `gradle install` in the root of the ratpack directory)

    #!/usr/bin/env groovy

    @Grab("com.augusttechgroup:ratpack-core:0.7.0-SNAPSHOT")
    @Grab("javax.servlet:javax.servlet-api:3.0.1")
    @GrabExclude("org.eclipse.jetty.orbit:javax.servlet:3.0.0.v201112011016")
    import com.bleedingwolf.ratpack.RatpackMain
    RatpackMain.main()

This program will pick up route definitions in "ratpack.groovy":

## Running with Gradle Plugin

Ratpack can also be run as a gradle task using the plugin.  There is a
test project with `ratpack.groovy` in a sub directory.  To test the
plugin (from the root directory):

    $ gradle -DincTestProject=true :ratpack-gradle-plugin-test:run
    
Then (in a browser) visit http://localhost:5050.

## Release Notes

### 0.6.2 (not released yet)

* The beginning of the release notes.
* Reorganized the build to integrate the ratpack-plugin and ratpack-core modules completely. They are no longer separate modules in Maven Central, nor separate subprojects in the Gradle build. They're just different groups of classes in different packages—all part of Ratpack.
* Moved `src/app/resources/scripts` and `src/app/resources/templates` back to `src/app/scripts` and `src/app/templates`, respectively.
* Revived the `runRatpack` task, which starts its own Jetty container directly and allows for auto-refresh of template files.
* Upgraded to Gradle 1.2.
* Added the ability to have multiple application scripts under `src/app/scripts`. All `.groovy` files recursively under that directory are included as application scripts.
* Progress toward live reloading of application scripts and API code.


