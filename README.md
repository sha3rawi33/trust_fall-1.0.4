# trust_fall

A Flutter plugin for detecting the trust fall of the device(Jailbroken, root, emulator and mock location detection).

Uses [RootBeer](https://github.com/scottyab/rootbeer) for Android root detection and [DTTJailbreakDetection](https://github.com/thii/DTTJailbreakDetection) for iOS jailbreak detection.
Inspired by [jail-monkey](https://github.com/GantMan/jail-monkey) and [this blog article](http://blog.geomoby.com/2015/01/25/how-to-avoid-getting-your-location-based-app-spoofed/) 

## Getting Started

In your flutter project add the dependency:

```yml
dependencies:
  ...
  trust_fall: ^1.0.4
```


## Usage
#### Importing package
```
import 'package:trust_fall/trust_fall.dart';
```
#### Using it

Checks whether device JailBroken on iOS/Android?
```
bool isJailBroken = await TrustFall.isJailBroken;
```
Checks whether device is real or emulator
```
bool isRealDevice = await TrustFall.isRealDevice;
```
Can this device mock location - no need to root!
```
bool canMockLocation = await TrustFall.canMockLocation;
```
(ANDROID ONLY) Check if application is running on external storage
```
bool isOnExternalStorage = await TrustFall.isOnExternalStorage;
```
Check if device violates any of the above
```
bool isTrustFall = await TrustFall.isTrustFall;
```

# Note:
#### Mock location detection
* **Android** - Location permission needs to be granted in app in order to detect mock location properly
* **iOS** - For now we are checking if device is Jail Broken or if it's not real device. There is no strong detection of mock location in iOS *(Open the PR if you have better way for mock location detection in iOS)*

## ❗Since emulators are usually rooted, you might want to bypass these checks during development. Unless you're keen on constant false alarms ⏰