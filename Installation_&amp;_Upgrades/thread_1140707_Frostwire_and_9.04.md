---
title: "Frostwire and 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by nickyn on 2009-04-27
I upgraded to Jaunty Jackalope, and since the upgrade, Frostwire won't open anymore.  Do I need to wait for Frostwire to release a new version for it to work with the new version of Ubuntu?
Thanks!

---

### Post by Partyboi2 on 2009-04-28
What happens when you try and start it from the terminal (Applications>Accessories>Terminal)
```
frostwire
```

---

### Post by nickyn on 2009-04-28
When I try and start it in the terminal, I get this:
> Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
So, does that mean I need an updated java?  And if so...how do I do that.  I've downloaded the Java...but I don't understand how to install it.  I'm not sure how to install things with the terminal.  Everything I've downloaded and installed so far have been with the extractor that pretty much does it for me.  Thanks!

---

### Post by Partyboi2 on 2009-04-28
Are you able to select an alternative java? Open a terminal and
```
sudo update-alternatives --config java 
```and see if you can change it.

If that does not work then try reconfiguring java
```
sudo update-java-alternatives -s java-6-sun 
```

---

### Post by nickyn on 2009-04-29
Alright, so when I try to find an alternative, it says:
> No alternatives for java.
Then when I try to reconfig, it says:
> sudo: update-java-alternatives: command not found
Sorry to be a bother...thanks.

---

### Post by nickyn on 2009-04-29
Oh, wait.  I downloaded the plug-in from the thing that pops up in Firefox.  Frostwire works fine now, THANKS!

---

### Post by user-max on 2009-05-14
I have a slightly different problem. I did a fresh install of Jaunty. And now I get a startup error when I try to start frostwire. No idea whats wrong. Here's console output:

max@armageddon:~$ frostwire 
HOSTNAME IS armageddon
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./jogg.jar:./ProgressTabs.jar:./log4j.jar:./commons-codec-1.3.jar:./mp3spi.jar:./looks.jar:./vorbisspi.jar:./icu4j.jar:./clink.jar:./httpcore-nio-4.0-beta2.jar:./guice-1.0.jar:./jdic_stub.jar:./messages.jar:./jorbis.jar:./jmdns.jar:./onion-common.jar:./lw-all.jar:./forms.jar:./FrostWire.jar:./jl.jar:./jcraft.jar:./onion-fec.jar:./aopalliance.jar:./commons-logging.jar:./daap.jar:./foxtrot.jar:./jython.jar:./httpcore-4.0-beta2.jar:./jaudiotagger.jar:./jdic.jar:./tritonus.jar:./jflac.jar:./httpcore-niossl-4.0-alpha7.jar:./gettext-commons.jar:./httpclient-4.0-alpha3.jar:./themes.jar:./junit.jar
java.lang.ExceptionInInitializerError
	at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
	at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
	at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
	at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
	at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
	at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
	at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
	at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
	at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.util.MissingResourceException: Resource bundle not found
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
	... 15 more
java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
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
Error: FrostWire version 4.17
Java version 1.6.0_13 from Sun Microsystems Inc.
Linux v. 2.6.28-11-generic on i386
Free/total memory: 33264936/53346304

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

Any ideas ???

---

### Post by KhanTG on 2009-10-11
I'm having the exact same issue with frostwire on two machines... could the .deb installer be messed up?  I have all the java dependencies met, but it is telling me "java.lang.NoClassDefFoundError:" ... Doesn't that mean that the software doesn't see java?  Ah Well... I'm going to attempt to install from the tarball (never had do do this before..), I'll get back here if it works...

---

