End-To-End Micronaut + Cloud Build + Cloud Run
========

This repository is intended to be a quickstart and high level overview to creating a simple micronaut [micronaut](https://www.micronaut.io)
application that can be built and deployed automatically to a Google Cloud Run endpoint.
* create simple micronaut controller, bean, and test class
* run locally via gradle and/or intellij
* link a [google source repository](https://cloud.google.com/source-repositories/) to a git repo
* configure [google cloud build](https://cloud.google.com/cloud-build/) to automate our build
* deploy to [google cloud run](https://cloud.google.com/run/) for a severless runtime that can scale up/down in realtime
* demonstrate the automatic build and deploy via commit -> build -> deploy


## Setup steps
* [install sdkman](#installing-sdkman)
* [install micronaut](#install-micronaut)
* install [gcloud sdk](#install-gcloud)
* demonstrate local startup times + filewatch and automatic restart when code changes
* link with google source repo
* create a google build agent
* deploy to google cloud run
* uninstall micronaut
* uninstall micronaut



## <a name="#installing-sdkman">Installing sdkman</a>
[sdkman](https://sdkman.io) bills itself as _"The Software Development Kit Manager."_  Installing is as simple as
>curl -s "https://get.sdkman.io" | bash

and then in a new terminal
>source "$HOME/.sdkman/bin/sdkman-init.sh"

for [more information about installing](https://sdkman.io/install) and sdk

### <a name="install-micronaut">Installing micronaut via sdkman</a>
[Sdkman](https://sdkman.io/) makes installing micronaut simple and quick.

> sdk install micronaut

### <a name="install-gcloud">Install GCloud SDK</a>
There's a few more steps than I want to get into for this tutorial - but to understand how to install and confirgure the gcloud
sdk check [here](https://cloud.google.com/sdk/gcloud/).  Please note you'll need to also install the beta feature to test
the cloud run and cloud build locally

###Creating the simple micronaut
Creating the simple base application from the command line is as simple as:

> mn create-app com.putt.example.micronaut.gdg --features file-watch -i

This will create a project with a single controller and matching test class inside of the current directory  (> -i flag)

demo using the continuous
file-watch for automatic updates when running locally.  _See [File Watch and Server Restart](https://docs.micronaut.io/latest/guide/index.html#types) section of the
main getting started guide or [17.5.1 Automatic Restart](https://docs.micronaut.io/latest/guide/index.html#reloading) for more in depth details about the continuous file watch._

The

> mn create-app com.putt.example.micronaut.gdg --features file-watch

> micronaut:
>     io:
>         watch:
>             paths: src/main
>             restart: true