---
title: "FrostWire fails"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by strider22 on 2009-11-01
I have installed Frostwire (and re-installed it too) but I get the following error report.

what should I do?

=======error report===========
FrostWire version 4.17
Java version 1.6.0_16 from Sun Microsystems Inc.
Linux v. 2.6.24-23-generic on i386
Free/total memory: 2557648/5775360

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

### Post by Furry_Fighter_20x66 on 2009-11-01
I posted a fix for the problem here at this thread. Well a fix that worked for me anyway. Hope it helps you too.

[http://ubuntuforums.org/showthread.php?p=8220035](http://ubuntuforums.org/showthread.php?p=8220035)

---

