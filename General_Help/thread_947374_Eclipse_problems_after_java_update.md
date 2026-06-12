---
title: "Eclipse problems after java update??"
date: 2008-10-14
forum: General Help
---

### Post by BareRolig on 2008-10-14
Hello 

Im am using eclipse in the form of IDLDE everyday, and this morning ubuntu automatically update the java engine, and now a cannot start eclipse, could this be because of the java update. The error log reads this 

!SESSION 2008-10-14 13:47:07.661 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_11
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_DK
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-10-14 13:47:11.674
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-10-14 13:47:11.707
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (241).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1018)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:974)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:260)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:417)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:340)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:405)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:369)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:357)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:107)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:153)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:504)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:443)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1169)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1144)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/Default/pxgnarray.pro' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)

java -version gives this 

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)

Any help is apriciated.

Best, Kennet

---

### Post by jespdj on 2008-10-14
Ok, so you got Sun Java 1.6.0_07, but the Eclipse log shows:

java.version=1.5.0_11

Do you still have Java 1.5.0_11 installed also?

Tips to get Eclipse working again:
[LIST=1]
[*]Start Eclipse with the "-clean" option from a command prompt: eclipse -clean
[*]If that doesn't work, delete the ~/.eclipse directory (NOTE! This will delete all your personal settings and updates that you installed with Eclipse's update manager): rm -rf ~/.eclipse
[/LIST]
I also got the Java update, but I don't have this problem. I'm not running Eclipse from the Ubuntu repository, however; I've downloaded Eclipse 3.4.1 from the Eclipse website and installed it manually.

---

### Post by kpkeerthi on 2008-10-14
> 
!SESSION 2008-10-14 13:47:07.661 -----------------------------------------------
eclipse.buildId=unknown
**java.version=1.5.0_11**
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_DK
Command-line arguments: -os linux -ws gtk -arch x86
....
....

For some reason eclipse is still looking for Java 1.5

Can you try running ```
sudo update-alternatives --config java
``` and choose java 1.6 as your default java. 

If that didn't work, try deleting your eclipse workspace folder or reinstall eclipse.

---

### Post by kostkon on 2008-10-14
> **kpkeerthi said:**
> For some reason eclipse is still looking for Java 1.5

Can you try running ```
sudo update-alternatives --config java
``` and choose java 1.6 as your default java. 

If that didn't work, try deleting your eclipse workspace folder or reinstall eclipse.
Indeed. Just do a
```
sudo update-java-alternatives -s java-6-sun
```
and your problems will be solved.

---

### Post by BareRolig on 2008-10-15
Thank you very much, It seems like it fixed it, 

andor@andor-host:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

I got this result and now IDLDE seems to work

---

### Post by jespdj on 2008-10-15
Good. Note that you can thank the people who helped you by clicking the [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] button below their posts. You can also mark this thread as solved by selecting "Mark as Solved" in the "Thread Tools" menu, at the top right part of the page.

---

