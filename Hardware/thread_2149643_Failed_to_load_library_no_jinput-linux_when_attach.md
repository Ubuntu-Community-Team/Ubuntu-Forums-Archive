---
title: "Failed to load library: no jinput-linux when attached controller"
date: 2013-05-29
forum: Hardware
---

### Post by indarkness on 2013-05-29
Hello, 

I have a thrustmaster firestorm dual analog 3 with ubuntun 12.04LTS. But when I execute my .jar I get this error

```
Failed to load library: no jinput-linux in java.library.path

java.lang.UnsatisfiedLinkError: no jinput-linux in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1856)
    at java.lang.Runtime.loadLibrary0(Runtime.java:845)
    at java.lang.System.loadLibrary(System.java:1084)
    at net.java.games.input.LinuxEnvironmentPlugin$1.run(LinuxEnvironmentPlugin.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at net.java.games.input.LinuxEnvironmentPlugin.loadLibrary(LinuxEnvironmentPlugin.java:61)
    at net.java.games.input.LinuxEnvironmentPlugin.<clinit>(LinuxEnvironmentPlugin.java:102)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:188)
    at net.java.games.input.DefaultControllerEnvironment.getControllers(DefaultControllerEnvironment.java:159)
    at com.codeminders.ardrone.controllers.ThrustmasterController.initGamepad(ThrustmasterController.java:88)
    at com.codeminders.ardrone.controllers.ThrustmasterController.getGamepad(ThrustmasterController.java:79)
    at com.codeminders.controltower.ControlTower.initController(ControlTower.java:114)
    at com.codeminders.controltower.ControlTower.<init>(ControlTower.java:90)
    at com.codeminders.controltower.ControlTower.main(ControlTower.java:591)
May 29, 2013 4:47:58 PM net.java.games.input.ControllerEnvironment log
INFO: net.java.games.input.LinuxEnvironmentPlugin is not supported

No gamepad found!
No suitable controller found! Control disabled
```

```
I do know that my controller is working in that the module is there 
Bus 001 Device 010: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 002: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 003 Device 002: ID 046a:0010 Cherry GmbH SmartBoard XX44
```

And when I type 

```
jscal /dev/input/js0
jstest /dev/input/js0
```

The controller responds to the calibration.

I have installed the package liblwjgl-java

```
/usr
/usr/share
/usr/share/java
/usr/share/java/lwjgl_util.jar
/usr/share/java/lwjgl_util_applet.jar
/usr/share/java/lwjgl.jar
/usr/share/java/lwjgl_test.jar
/usr/share/doc
/usr/share/doc/liblwjgl-java
/usr/share/doc/liblwjgl-java/copyright
/usr/share/doc/liblwjgl-java/changelog.Debian.gz
```

But, I don't know wwhy I cannot run my .jar due to this library, any tips to install this native java library?

---

