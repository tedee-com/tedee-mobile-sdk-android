# Tedee Mobile SDK for Android [![](https://jitpack.io/v/tedee-com/tedee-mobile-sdk-android.svg)](https://jitpack.io/#tedee-com/tedee-mobile-sdk-android)

Welcome to the Tedee Mobile SDK for Android! This comprehensive toolkit empowers developers to seamlessly integrate Tedee Lock functionality into their Android applications. Whether you're building a smart home app or enhancing access control features, our SDK provides the necessary tools to communicate with and control Tedee locks with ease, leveraging Bluetooth Low Energy (BLE) communication protocol.

## Documentation

[Mobile SDK Documentation](https://tedee-com.github.io/tedee-mobile-sdk-android/)

## Features

- **Effortless Integration**: Incorporate Tedee lock functionality into your Android applications seamlessly.
- **Full Control**: Communicate with and operate Tedee locks, including [Tedee PRO](https://tedee.com/product-info/tedee-pro/) and [Tedee GO](https://tedee.com/product-info/tedee-go-best-keyless-access/), with comprehensive control options.
- **Efficient Communication**: Utilize Bluetooth Low Energy (BLE) for efficient device interaction, ensuring optimal performance and minimal energy consumption.

## Getting Started

Getting started with the Tedee Mobile SDK is straightforward:

### Installation

Step 1. Add the JitPack repository to your build file.

Add it in your settings.gradle or settings.gradle.kts if you use Kotlin:
```gradle
dependencyResolutionManagement {
  repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
      mavenCentral()
      maven { url 'https://jitpack.io' }
    }
}
```

Or directly in root build.gradle if there will be a problem with sync build gradle:

```gradle
repositories {
    google()
    mavenCentral()
    maven { url 'https://jitpack.io' }
}
```

Step 2. Add the dependency

```gradle
dependencies {
  implementation("com.github.tedee-com:tedee-mobile-sdk-android:1.0.0@aar") { isTransitive = true }
}
```

Or if you are using Groovy instead of Kotlin:

```gradle
dependencies {
  implementation("com.github.tedee-com:tedee-mobile-sdk-android:1.0.0@aar") { transitive = true }
}
```

### Configuration

To properly use sdk for lock already added to account you will need:

- register your app with your app name and mobile public key (https://api.tedee.com/swagger/index.html#/Mobile/PostMobile, mobile public key is generated with `getMobilePublicKey()` See example app)
- provide lock serial number and device name (you can find it in Tedee app "Lock settings" -> "Information")
- get device public key, certificate and certificate expiry date (see example app how to get them from Tedee API - [Documentation](https://github.com/tedee-com/tedee-example-ble-android/blob/master/README.md)

When all required data is provided you can try to secure connect to the lock using
```kotlin
  fun connect(
    serialNumber: String,
    deviceCertificate: DeviceCertificate,
    keepConnection: Boolean = true,
    secureConnectionListener: ILockConnectionListener
  )
``` 
method.

To properly use sdk for lock not added to account you will need:

- provide lock serial number. You can get it from [Tedee API](https://api.tedee.com) based on Activation Code. See example app how to get them from Tedee API - [Add lock documentation](https://github.com/tedee-com/tedee-example-ble-android/blob/master/ADD_LOCK_README.md)

When all required data is provided you can try to connect to the lock using 
```kotlin 
  fun connectForAdding(
    serialNumber: String,
    keepConnection: Boolean = true,
    addLockConnectionListener: IAddLockConnectionListener
  )
```
method.

## Example App

Explore the capabilities of the Tedee Mobile SDK through our [example app](https://github.com/tedee-com/tedee-example-ble-android). This example app demonstrates various use cases and serves as a practical guide for integrating the SDK into your projects.

### Add Lock Documentation

Documentation describing basic steps required to add a lock to your Tedee account and register the lock device. [Add lock documentation](https://github.com/tedee-com/tedee-example-ble-android/blob/master/ADD_LOCK_README.md)

### API Documentation

Documentation describing public API of the Tedee Lock framework is available at [API](https://api.tedee.com/swagger/index.html). Refer to this documentation for in-depth insights into available functionalities and methods.

For more details about Tedee Lock BLE API, available commands, their parameters, notifications and more please refer to our BLE API documentation available at [https://tedee-tedee-lock-ble-api-doc.readthedocs-hosted.com/en/latest/index.html](https://tedee-tedee-lock-ble-api-doc.readthedocs-hosted.com/en/latest/index.html).

### Known issues

Right now there is an issue on Google Pixel 4a device with generating mobile key pair. We are working on it and will fix it soon. As workaround please use other device.

### Support

For any inquiries, feedback, or assistance, our Android team is here to help. Reach out to us at [Discussions](https://github.com/tedee-com/tedee-mobile-sdk-android/discussions) section with any questions or concerns you may have.

We're excited to witness the innovative solutions you create with the Tedee Mobile SDK! Happy coding! 🚀

### Legal Notice

By using the Tedee Mobile SDK, you agree to the terms of the [LICENSE](./LICENSE) and the [Terms of Use Tedee APIs and SDKs](https://tedee.com/terms-of-use-tedee-apis-and-sdks/). Please review these documents before integrating or distributing the SDK.
