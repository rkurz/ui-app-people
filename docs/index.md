# People App

This is a single page web application that allows a user to manage all of the people in an organization.

## Prerequisites
In order to setup your environment please follow all the setup steps as outlined here.

## Run the app
After you've downloaded the source code, open a terminal, navigate to the root folder and run the following command:
> npm run restore

This will install all of the project dependencies that you need.
After teh restore command was executed successfully, you can run the application with the following command:
> npm run serve

## Architecture
The following container diagram shows how the SPA fits in with the other containers in the system.

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml


!define DEVICONS https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/devicons
!define FONTAWESOME https://raw.githubusercontent.com/tupadr3/plantuml-icon-font-sprites/master/font-awesome-5
!include DEVICONS/angular.puml
!include DEVICONS/java.puml
!include DEVICONS/msql_server.puml
!include FONTAWESOME/users.puml


LAYOUT_WITH_LEGEND()




Person(user, "Customer", "People that need products", $sprite="users")
Container(spa, "SPA", "angular", "The main interface that the customer interacts with", $sprite="angular")
Container(api, "API", "java", "Handles all business logic", $sprite="java")
ContainerDb(db, "Database", "Microsoft SQL", "Holds product, order and invoice information", $sprite="msql_server")


Rel(user, spa, "Uses", "https")
Rel(spa, api, "Uses", "https")
Rel_R(api, db, "Reads/Writes")
@enduml
```
