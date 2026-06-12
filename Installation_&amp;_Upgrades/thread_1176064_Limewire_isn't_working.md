---
title: "Limewire isn't working"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by lilredcougar07 on 2009-06-01
Hey everyone, I recently downloaded Limewire from their website using the deb, and when I clicked on it, nothing happened. So I went to terminal and typed "limewire" in. This is what I got.

> Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-cacao/jre/lib/i386/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
    at org.limewire.ui.swing.Main.getSplashImage(Main.java:56)
    at org.limewire.ui.swing.Main.main(Main.java:28 )

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.6+)
The version of Java in your PATH is:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu5) Runtime Environment (build 1.6.0_0-b12)
CACAO (build 0.99.3+hg, compiled mode)
I don't know what to do. Is it because I'm not using Sun? If so, how do I switch over to it?

Nevermind! I got it fixed. Thanks anyway!

---

