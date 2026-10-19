# Missav TV (Android WebView wrapper)

Android TV / Android set-top-box wrapper for `https://missav.ws/dm339`.
Minimum Android version: Android 6.0 (API 23).

## Included
- Android TV launcher entry and normal launcher entry
- Full-screen immersive display
- JavaScript and DOM storage for modern web pages
- HTML5 media playback and WebChromeClient video full-screen callback
- Back/Escape: exit video full-screen, navigate back, or return to the configured home URL
- DPAD events are passed through to WebView/page controls
- HTTPS only; mixed content is blocked and SSL certificate errors are not bypassed

## Build an APK

1. Install **Android Studio** on a Windows, macOS, or Linux computer.
2. In Android Studio, choose **Open** and select this `MissavTV` folder.
3. Allow Gradle sync. Install Android SDK Platform 35 and a compatible JDK (Android Studio's bundled JDK 17 is suitable for AGP 8.6.1).
4. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. The debug APK will be at:
   `app/build/outputs/apk/debug/app-debug.apk`
6. Transfer the APK to the Android box/TV, enable installation from the file manager/source you use, then install it.

Command line (with Android SDK and Gradle installed):

```bash
gradle assembleDebug
```

For a release APK, use **Build > Generate Signed Bundle / APK** and create/use your own signing key. Do not share your private signing key.

## Important compatibility notes
- This project targets Android 9 (API 28) while setting `minSdk 23`; this avoids newer target-SDK behavior that can complicate older boxes. It still compiles against SDK 35.
- Site playback depends on the box's installed Android System WebView/Chromium version, codecs, DRM requirements, site anti-bot checks, and network access. Android 6 WebView is old; some current sites may not work fully even though the app installs.
- Start video playback with the page's own play control. Some sites require a user gesture or use DRM / browser features unsupported by the built-in WebView.
- Remote control behavior depends on the site's focusable controls. If DPAD focus is not exposed by the page, additional site-specific keyboard-navigation logic may be required.
- The app does not bypass age checks, geographic restrictions, access controls, or certificate errors.
- Use only where you are legally permitted to access the content and ensure the device user meets the site's age requirements.

## Configuration
Change `HOME_URL` in `app/src/main/java/tw/missav/tv/MainActivity.java` to change the start page.
