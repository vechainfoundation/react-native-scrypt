
# react-native-scrypt

Non blocking and fast scrypt implementation for React Native.

## Introduction

[scrypt](http://www.tarsnap.com/scrypt.html) is a password-based key derivation function designed to make it costly to perform hardware attacks on the derived keys. While there exist scrypt implementations written in javascript they are extremely slow and impractical for use in mobile apps.

This plugin is for use with React Native and allows your application to use scrypt on iOS/Android devices using native C code, achieving orders of magnitude faster calculation. It is based on [libscrypt](https://github.com/technion/libscrypt).

## Getting started

`$ npm install react-native-scrypt --save`

`npx pod-install`

### Mostly automatic installation - Deprecated

`$ react-native link react-native-scrypt`

### Manual installation


#### iOS - Deprecated

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-scrypt` and add `RNScrypt.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNScrypt.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

#### Android

1. Open up `android/app/src/main/java/[...]/MainApplication.java`
  - Add `import com.crypho.scrypt.RNScryptPackage;` to the imports at the top of the file - **Deprecated**
  - Add `new RNScryptPackage()` to the list returned by the `getPackages()` method - **Deprecated**
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-scrypt'
  	project(':react-native-scrypt').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-scrypt/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      implementation project(':react-native-scrypt')
  	```
    
### node_modules - only if not statically loaded

1. Open `node_modules/react-native-scrypt/android/build.gradle` 
  - Change `compile 'com.facebook.react:react-native:+'` in the `dependencies` object to `implementation com.facebook.react:react-native:+`
  - Add `ndkVersion "21.4.7075529"` on the `android` object
  - Add `compileSdkVersion safeExtGet('compileSdkVersion', 23)` to the `defaultConfig` object


## Usage
```javascript
import scrypt from 'react-native-scrypt';

// With 'legacy' encoding (default): passwd must be a string, salt must be an array of bytes integers
// With 'hex' encoding: passwd and salt must be string encoded in hexadecimal
// With 'base64' encoding: passwd and salt must be string encoded in base64
// With 'buffer' encoding: passwd and salt must be Buffers (in the sense of [`buffer`](https://github.com/feross/buffer/) package)
// see example/App.js


const result = await scrypt(passwd, salt[, N=16384, r=8, p=1, dkLen=64, encoding='legacy'])
```

## LICENSE

    The MIT License

    Copyright (c) 2017 Crypho AS.

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.

    libscrypt is Copyright (c) 2013, Joshua Small under the BSD license. See src/libscrypt/LICENSE
