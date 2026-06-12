---
title: "intalling limewire: java dependency does not satisfy"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by iochinome on 2009-05-09
hey guys, i am trying to download limwire on jaunty, and i have downloaded it from the limewire site (the one that says ubuntu on it) but now when the package installer tries to install it, under the 'status' it says:
Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk

any idea how to fix this? i am not able to install it at the moment. thanks!!

---

### Post by Partyboi2 on 2009-05-09
Hi, it means you need to install the dependencies first. So install the sun-java6-jre package
```
sudo apt-get install sun-java6-jre 
```
then try installing limewire again.

---

### Post by iochinome on 2009-05-10
hmm.... okay, i got that far, and i even downloaded the .deb from the limewire site, and the package installer seemed to take care of it. then, it said it was finished and i closed the package installer down. where is limewire supposed to be on my computer? typing 'limewire' into terminal does nothing. i even did a file search for 'limewire' and there is a folder called limewire at
/usr/lib/limewire
but inside of it there is just a mass of confusingly-named files. what to do?

thanks, much appreciated!

---

### Post by Partyboi2 on 2009-05-10
You should have been able to find it under Applications>Internet.
Another option is to install frostwire which is basically the same thing
[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by crakup on 2009-05-11
i had problems with the limewire and then i intalled frostwire and i've not problems with that.
 like said Partyboi2 frostwire is the same.

---

### Post by bmay82 on 2009-05-24
This is what I get when I try to run Frostwire? Any suggestions?



FrostWire version 4.17
Java version 1.6.0_13 from Sun Microsystems Inc.
Linux v. 2.6.28-11-generic on i386
Free/total memory: 1088480/5308416

java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
    at com.limegroup.gnutella.bugs.LocalClientInfo.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.LocalClientInfoFactoryImpl.createLocalClientInfo(Unknown Source)
    at com.limegroup.gnutella.bugs.FatalBugManager.handleFatalBug(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ExceptionInInitializerError
    at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
    at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
    at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    ... 6 more
Caused by: java.util.MissingResourceException: Resource bundle not found
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
    at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
    ... 15 more

STARTUP ERROR!

---

### Post by 801TomAK on 2010-07-26
i tried puting in the sudo apt-jet java thing and it said this to me   Package sun-java6-jre has no installation candidate

---

### Post by Taviddude on 2010-08-06
> **801TomAK said:**
> i tried puting in the sudo apt-jet java thing and it said this to me   Package sun-java6-jre has no installation candidate
Ditto. I'm stuck. This is a pretty pathetic first post, but this is the exact problem I'm having. Never had a problem, and LOVED Ubuntu until I bought a new harddrive, and installed 10.04. 
Any help on this is Much appreciated.

---

### Post by Mze on 2010-08-07
[How to install Sun Java in Ubuntu 10.04]("http://ubuntuforums.org/showthread.php?t=1517979") - forum thread

---

