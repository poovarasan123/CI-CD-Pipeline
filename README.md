CI/CD Pipeline for Native Android and React Native
This repository contains a CI/CD pipeline configured with GitHub Actions for building and releasing Native Android applications and React Native applications. The pipeline is structured to handle both Android and iOS builds, ensuring that your applications are built, tested, and packaged efficiently.
Overview
The CI/CD pipeline is divided into the following main sections:
Native Android Build: This section builds the Android application using Gradle.
React Native Build: This section builds both Android and iOS applications using Flutter and Node.js.
Artifact Management: The pipeline uploads build artifacts for easy access after the build process.
Workflow Triggers
The workflows are triggered under the following conditions:
Push to dev branch: Initiates the build process for the Native Android application.
Push or Pull Request to main branch: Initiates the build process for both React Native and iOS applications.
Pipeline Structure
1. Native Android Build
The workflow for building the Native Android application is defined in a YAML file that includes the following steps:
Checkout Repository: Clones the repository code.
Set up JDK 17: Configures Java Development Kit (JDK) version 17 using Temurin distribution.
Grant Execute Permission: Makes the Gradle wrapper executable.
Build with Gradle: Assembles a debug APK of the application.
Upload Artifact: Uploads the generated APK as an artifact.
2. React Native Build
The workflow for building React Native applications includes:
Android Build Steps:
Checkout Repository: Clones the repository code.
Set up JDK 17: Configures Java Development Kit (JDK) version 17.
Install Node.js: Installs Node.js version 18.
Install Dependencies: Uses Yarn to install project dependencies.
Build Android: Builds the release APK using Gradle.
Upload Android Artifact: Uploads the generated APK as an artifact.
iOS Build Steps:
Checkout Repository: Clones the repository code.
Install Node.js: Installs Node.js version 18 for iOS dependencies.
Install CocoaPods: Installs CocoaPods dependencies for iOS projects.
Build iOS: Uses Xcode to build the iOS application.
Upload iOS Artifact: Uploads the generated iOS archive as an artifact.
3. Versioning and Tagging
The pipeline includes steps to extract version information from pubspec.yaml, check if a corresponding Git tag exists, and modify the version if necessary. This ensures that each build is uniquely identifiable.
4. Optional Steps
There are commented-out sections in the workflow files that allow for additional functionality, such as:
Building an IPA file for iOS applications.
Compressing archives of built applications.
Creating a GitHub release with uploaded artifacts.
Getting Started
To use this CI/CD pipeline in your own project, follow these steps:
Fork or Clone this Repository:
Clone this repository to your local machine or fork it to your own GitHub account.
Configure Secrets:
Set up necessary secrets in your GitHub repository settings (e.g., KEYSTORE_PASSWORD, KEY_PASSWORD, KEY_ALIAS) for signing Android apps.
Modify Workflow Files:
Adjust any paths or configurations in the workflow YAML files according to your project's structure and requirements.
Push Changes:
Push changes to the specified branches (dev or main) to trigger the CI/CD workflows.
Conclusion
This CI/CD pipeline provides a robust framework for automating builds and releases of Native Android and React Native applications. By leveraging GitHub Actions, you can ensure that your applications are consistently built and ready for deployment with minimal manual intervention.