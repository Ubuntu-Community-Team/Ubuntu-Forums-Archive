---
title: "java.awt.HeadlessException:  No X11 DISPLAY variable was set"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by kas_prasad on 2009-08-08
Hi,
I'm trying to install Zend Studio 7 on my ubuntu 9.04 (32bit) installed PC. But when I'm trying to run the 'ZendStudio7_0_0.bin' file it gave me following message and application exits. 

root@sameera-laptop:/home/sameera/Desktop/Software Packages/Zend Studio 7# ./ZendStudio7_0_0.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

[COLOR=Red]Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.[/COLOR]
    at java.awt.GraphicsEnvironment.checkHeadless(Unknown Source)
    at java.awt.Window.<init>(Unknown Source)
    at java.awt.Frame.<init>(Unknown Source)
    at java.awt.Frame.<init>(Unknown Source)
    at javax.swing.JFrame.<init>(Unknown Source)
    at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
    at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
    at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
    at com.zerog.ia.installer.Main.main(DashoA8113)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at com.zerog.lax.LAX.launch(DashoA8113)
    at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
root@sameera-laptop:/home/sameera/Desktop/Software Packages/Zend Studio 7#

I have being checked and my pc got installed sun-java6-bin, sun-java6-jre,java-commom etc;

Please help me to solve this. 
Thank you!

---

