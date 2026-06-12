---
title: "Mercury 1709 won't install on 5.10 Breezy Badger"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Silverstar on 2006-01-04
Hey all,

I have Ubuntu 5.10 Breezy Badger and I want to install Mercury 1709. But when I install the 1709_Linux_VM.bin file, it fail and come with the following error message:

> 
root@pc:/home/user/Desktop# ./1709_Linux_VM.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
./1709_Linux_VM.bin: line 2088: strings: command not found

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. Thi s application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.12305/Linux/resource/jre/lib/i3 86/libawt.so: libXp.so.6: cannot open shared object file: No such file or direct ory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.zerog.ia.installer.Main.d(DashoA8113)
        at com.zerog.ia.installer.Main.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

The version of Mercury without VM doesn't also work, and quit with a error message that looks the same.

Does anyone know how I resolve this?

---

### Post by Silverstar on 2006-01-05
Kick

---

