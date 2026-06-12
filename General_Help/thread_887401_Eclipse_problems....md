---
title: "Eclipse problems..."
date: 2008-08-12
forum: General Help
---

### Post by Crafty Kisses on 2008-08-12
So I was doing some stuff with Eclipse, and then it crashed, so naturally I re-opened it, and when I did, it just wouldn't open, so I ran this in Terminal:

```
eclipse
```
For some reason I got Eclipse to run again, but as soon as I got to the boot screen for Eclipse I get this error:
```
JVM terminated. Exit code=143
/usr/lib/jvm/java-1.5.0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 290011
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
```
I've checked the log files, and I don't see anything out of the ordinary.
Then I uninstalled Eclipse by doing the following:
```
sudo apt-get remove eclipse
```
So I removed it, and then I reinstalled it through Synaptic, and I ran Eclipse through Terminal and it booted up fine, but now I get a different error, here it is:
```
!SESSION 2008-08-12 20:16:07.399 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.720
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.721
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-04-03 20:16:13.080
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
	at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
```
I've tried numerous things, I've looked at every possible log there is, and tried like 4 things, still nothing, any ideas?

---

### Post by Nepherte on 2008-08-12
> **Codename said:**
> ```
eclipse
```
For some reason I got Eclipse to run again, but as soon as I got to the boot screen for Eclipse I get this error:
```
JVM terminated. Exit code=143
/usr/lib/jvm/java-1.5.0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 290011
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
```

When I get those errors on startup, removing ~/.eclipse solves this.

---

### Post by Crafty Kisses on 2008-08-12
> **Nepherte said:**
> When I get those errors on startup, removing ~/.eclipse solves this.

Thanks for your help, it seems the first error has stopped coming up, and I don't see anything in the logs but I still get this one:
```
!SESSION 2008-08-12 20:16:07.399 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.720
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.721
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-03 20:16:12.722
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-04-03 20:16:13.080
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
	at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
```

---

### Post by Crafty Kisses on 2008-08-13
So here's some interesting stuff here I set **java.library.path** via eclipserc, so I did the following:
```
gedit ~/.eclipse/eclipserc
```
I added this line to set the Java path:
```
VMARGS="-Djava.library.path=/usr/lib/jni"
```
Then I obviously installed **libsvn-java:**
```
sudo apt-get install libsvn-java
```
I pretty much did this so JavaHL would not generate this error message and possibly  use Eclipse, but still nothing I, I rebooted Eclipse after I added these lines in the config file, and now I get this when I boot into Eclipse:
```
Failed to load JavaHL Library.
These are the errors that were encountered:
no libsvnjavahl-1 in java.library.path
no svnjavahl-1 in java.library.path
no svnjavahl in java.library.path
java.library.path = /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client::/
usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386::/usr/lib/firefox:/usr/lib/
firefox/:/usr/java/packages/lib/i386:/lib:/usr/lib
```
I'm really stumped, I've took every measure to solve this, but still nothing anyone have any ideas, I really need to use Eclipse but I guess I can wait for now, but this is strange.

---

### Post by kpkeerthi on 2008-08-13
Not sure about the error. But I usually download eclipse off [www.eclipse.org](www.eclipse.org), extract it to a folder (/opt) and run from there. Works a treat.

And btw... Did you try (re)installing sun's JDK 6 and make sure it is set as default JVM for your system

```
sudo aptitude install sun-java6-bin
```
```
sudo update-alternatives --config java
```

---

### Post by Crafty Kisses on 2008-08-13
> **kpkeerthi said:**
> Not sure about the error. But I usually download eclipse off [www.eclipse.org](www.eclipse.org), extract it to a folder (/opt) and run from there. Works a treat.

And btw... Did you try (re)installing sun's JDK 6 and make sure it is set as default JVM for your system

```
sudo aptitude install sun-java6-bin
```
```
sudo update-alternatives --config java
```

Yeah sadly I've tried this before and it didn't work, I really appreciate the help though, I'll retry this method again and hopefully some other outcome can come out of this, and again I appreciate your help man.

---

### Post by NoSugar on 2008-08-13
Well I've finally learned enough to try to help someone else.  Try this:

```

eclipse -vm /usr/lib/jvm/java-6-sun/bin/java

```

That will run eclipse with the appropriate jvm.  Changing config file doesn't seem to help.

Also turn off 'Build Automatically' or it will use too much CPU.

I just installed Adobe Flex Builder for Linux which runs with eclipse - seems to work fine once you use the right jvm.

Hope this helps.

---

