uch# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

```bash
./gradlew assembleDebug          # Build debug APK
./gradlew assembleRelease        # Build release APK
./gradlew clean                  # Clean build directory
./gradlew test                   # Run unit tests
./gradlew connectedAndroidTest   # Run instrumented tests (requires connected device/emulator)
./gradlew lint                   # Run lint checks
```

## Architecture

This is an educational Android app demonstrating core Android concepts. It uses a simple **Activity-based** architecture with no Fragments, no Dependency Injection, and no MVVM/MVP patterns — intentionally minimal for teaching purposes.

**Navigation flow:**
```
MainActivity (Login) → LoggedUser (Dashboard)
                            ├── WeatherActivity   (OkHttp3 + OpenWeatherMap API)
                            ├── ChangePassword    (input validation demo)
                            └── WebViewActivity   (loads tredgate.cz)
```

**Supporting classes:**
- `MyAppWidgetProvider` — home screen widget that launches MainActivity
- `MyNotificationManager` — encapsulates FCM/local notification logic

**Key details:**
- Package: `com.example.tredgate_learningapp`
- Language: Java (not Kotlin)
- Min SDK 19, Target/Compile SDK 33, MultiDex enabled
- Login credentials are hardcoded (`success_user` / `123456`) — this is intentional for the learning context
- `ChangePassword` back button intentionally throws `RuntimeException` (error handling demo)
- Weather is hardcoded to Prague (lat=50.088, lon=14.4208)
- Brand colors defined in `colors.xml`: Tredgate Blue `#333366`, BlueGreen `#01b1ad`
- UI strings are in Czech
