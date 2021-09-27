[![Buy Me A Coffee](https://img.shields.io/badge/Donate-Buy%20Me%20A%20Coffee-yellow.svg)](https://www.buymeacoffee.com/rodydavis)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=WSH3GVC49GNNJ)

# mobile_popup

A Flutter plugin to show a PopUp Surface on Tablet / Desktop and for Mobile a Full Screen View. It will animate between them for a smooth experience. Check out the example for a demo.

## Usage

``` dart
showMobilePopup(
    context: context,
    builder: (context) => MobilePopUp(
        title: 'App Settings',
        leadingColor: Colors.white,
        builder: Builder(
            builder: (navigator) => Scaffold(
                body: SingleChildScrollView(
                    child: Column(
                    children: <Widget>[
                        ListTile(
                        leading: Icon(Icons.brightness_auto),
                        title: Text('Brightness'),
                        trailing: Switch.adaptive(
                            value: true,
                            onChanged: (value) {},
                        ),
                        ),
                        ListTile(
                        leading: Icon(Icons.fingerprint),
                        title: Text('Fingerprint'),
                        trailing: Switch.adaptive(
                            value: false,
                            onChanged: (value) {},
                        ),
                        ),
                        ListTile(
                        leading: Icon(Icons.map),
                        title: Text('Navigation'),
                        trailing: Switch.adaptive(
                            value: true,
                            onChanged: (value) {},
                        ),
                        ),
                    ],
                    ),
                ),
                ),
        ),
    ),
);
```

## Screenshots

![](https://github.com/rodydavis/plugins/blob/master/packages/mobile_popup/screenshots/1.png)
![](https://github.com/rodydavis/plugins/blob/master/packages/mobile_popup/screenshots/2.png)
![](https://github.com/rodydavis/plugins/blob/master/packages/mobile_popup/screenshots/3.png)

## Example

``` dart
import 'dart:io';

import 'package:flutter/material.dart';

import 'package:flutter/foundation.dart'
    show debugDefaultTargetPlatformOverride;
import 'package:mobile_popup/mobile_popup.dart';

void main() {
  _setTargetPlatformForDesktop();
  runApp(MyApp());
}

/// If the current platform is desktop, override the default platform to
/// a supported platform (iOS for macOS, Android for Linux and Windows).
/// Otherwise, do nothing.
void _setTargetPlatformForDesktop() {
  TargetPlatform targetPlatform;
  if (Platform.isMacOS) {
    targetPlatform = TargetPlatform.iOS;
  } else if (Platform.isLinux || Platform.isWindows) {
    targetPlatform = TargetPlatform.android;
  }
  if (targetPlatform != null) {
    debugDefaultTargetPlatformOverride = targetPlatform;
  }
}

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: HomeScreen(),
    );
  }
}

class HomeScreen extends StatelessWidget {
  const HomeScreen({
    Key key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Popup Example'),
      ),
      body: Center(
        child: RaisedButton(
          child: Text("Show Popup"),
          onPressed: () {
            showMobilePopup(
              context: context,
              builder: (context) => MobilePopUp(
                    title: 'App Settings',
                    leadingColor: Colors.white,
                    builder: Builder(
                      builder: (navigator) => Scaffold(
                            body: SingleChildScrollView(
                              child: Column(
                                children: <Widget>[
                                  ListTile(
                                    leading: Icon(Icons.brightness_auto),
                                    title: Text('Brightness'),
                                    trailing: Switch.adaptive(
                                      value: true,
                                      onChanged: (value) {},
                                    ),
                                  ),
                                  ListTile(
                                    leading: Icon(Icons.fingerprint),
                                    title: Text('Fingerprint'),
                                    trailing: Switch.adaptive(
                                      value: false,
                                      onChanged: (value) {},
                                    ),
                                  ),
                                  ListTile(
                                    leading: Icon(Icons.map),
                                    title: Text('Navigation'),
                                    trailing: Switch.adaptive(
                                      value: true,
                                      onChanged: (value) {},
                                    ),
                                  ),
                                ],
                              ),
                            ),
                          ),
                    ),
                  ),
            );
          },
        ),
      ),
    );
  }
}

```
