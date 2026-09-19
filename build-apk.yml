name: Build Midnight Protocol APK

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Extract Android project
        run: unzip -q Midnight_Protocol_Android_Project.zip -d extracted

      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - name: Set up Android SDK
        uses: android-actions/setup-android@v3

      - name: Set up Gradle
        uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: '8.10'

      - name: Build APK
        working-directory: extracted/midnight_apk_project
        run: gradle --no-daemon assembleDebug

      - name: Upload APK
        uses: actions/upload-artifact@v4
        with:
          name: Midnight-Protocol-APK
          path: extracted/midnight_apk_project/app/build/outputs/apk/debug/app-debug.apk
