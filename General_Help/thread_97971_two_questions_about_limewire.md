---
title: "two questions about limewire"
date: 2005-12-02
forum: General Help
---

### Post by ubuntu27 on 2005-12-02
Hello folks :) I've installed LimeWire following this: [https://wiki.ubuntu.com/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b](https://wiki.ubuntu.com/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b)

And I see that the only way to start Limewire is to use the command "runLime.sh' in the terminal. ANd if close the terminal, limewire wil also close. 
Since this bugs me out, I want to un-install it and install again with another method.

now my first question, How do I unistall Limewire?

Scond question, is there another method to install Limewire? I wish I could install using the packages that the Limewire's Official website offer.

---

### Post by RAOF on 2005-12-02
You could also make a menu item to launch the runLime.sh script.  Then you wouldn't need to explicitly open a terminal.

Alternatively, just Alt-F2 (which opens the "run application" thingy) and running "runLime.sh" should load it up without a terminal.

---

### Post by ubuntu27 on 2005-12-02
[QUOTE=RAOF]You could also make a menu item to launch the runLime.sh script.  Then you wouldn't need to explicitly open a terminal.

Alternatively, just Alt-F2 (which opens the "run application" thingy) and running "runLime.sh" should load it up without a terminal.[/QUOTE]

Oh! Men. THanks for the tip/trick :D  It sure helps a lot!!
Now I don't need to re-install it :)

I though "Run Application" just didn't exist in Breezy (I saw it on hoary).

---

### Post by RAOF on 2005-12-02
The Application menu option's gone, but the shortcut's still there ;)

---

### Post by Protostar on 2005-12-02
I'm having a problem with Limewire. I have Java installed but when I try and start it from the command line, these are the errors I get:

```
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: /usr/lib/j2se/1.4/jre/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1586)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1503)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1437)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1458)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

I don't get it. I have Java installed. Is Java configured wrong?

---

### Post by astronerd on 2005-12-02
If you want a really really easy way of installing limewire use automatix.  It will install it, make a launch icon under applications and install all the other depend.  that you need.  Plus there are a ton of other useful things there to get as well.  There is a how to from this link:

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

HTH, 
Charles

---

### Post by Protostar on 2005-12-02
I already got Automatix by the time you wrote the post, but thank for your help anyway!!

---

### Post by Qrk on 2005-12-02
Do be sure to try gtk-gnutella... I find it faster than Limewire and it integrates with your gtk theme.

---

