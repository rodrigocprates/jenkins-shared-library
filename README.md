# Jenkins Shared Library

Make use of a shared library to reuse code across multiple jobs.

## Setup instructions

1. In Jenkins, go to Manage Jenkins &rarr; Configure System. Under _Global Pipeline Libraries_, add a library with the following settings:

    - Name: `jenkins-shared-library`
    - Default version: `main` (branch)
    - Retrieval method: _Modern SCM_
    - Select the _Git_ type
    - Project repository: `<git repository url>`
    - Credentials: _select an existing credential_

2. Then create a Jenkins job with the following pipeline:

    ```
    @Library('jenkins-shared-library') _

    stage('Demo') {
      common.sayHello("Rodrigo")
    }
    ```

Whenever a job is triggered, it will:
- clone this shared library repo (with most updated code)
- import the functions
- run whatever function you call in your pipeline