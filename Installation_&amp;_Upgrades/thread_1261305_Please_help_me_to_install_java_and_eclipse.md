---
title: "Please help me to install java and eclipse"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by isato on 2009-09-08
Hi, I have tried lots of guides but I think I have messed things up. Anyway when I try to start eclipse I get the message that no virtuel machine can be found. 
This is in Swedish but it says that java can be found in some of those packeges. I have installed all these packeges.

```
tarek@ubuntu:~$ java -version 
Programmet "java" kan hittas i följande paket:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Prova: sudo apt-get install <valt paket>
bash: java: kommandot finns inte
tarek@ubuntu:~$ 
```When I try to install java, I get this that says that there is nothing to install and nothing update.


 ```
tarek@ubuntu:~$ sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
sun-java6-jdk är redan den senaste versionen.
sun-java6-jre är redan den senaste versionen.
sun-java6-plugin är redan den senaste versionen.
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libjaxp1.3-java libcommons-pool-java junit4 eclipse-jdt libcommons-modeler-java libxerces2-java openoffice.org-officebean eclipse-pde eclipse-rcp libservlet2.4-java libcommons-beanutils-java libxul-common junit
  libcommons-launcher-java libhsqldb-java libcommons-logging-java libcommons-collections-java openoffice.org-report-builder-bin libxerces2-java-gcj libtomcat5.5-java eclipse-platform-gcj ant gcj-4.3 libjsch-java
  openoffice.org-java-common ant-optional gappletviewer-4.3 libgcj9-dev libcommons-dbcp-java libxul0d openoffice.org-filter-mobiledev openoffice.org-filter-binfilter zlib1g-dev liblucene-java libswt3.2-gtk-java libcommons-el-java
  eclipse-rcp-gcj libservlet2.3-java eclipse-source eclipse-jdt-gcj libmozjs0d openoffice.org-base openoffice.org-writer2latex libgcj9-src ant-optional-gcj libcommons-collections3-java eclipse-platform libswt3.2-gtk-gcj ant-gcj
  libcommons-digester-java java-gcj-compat-dev libswt3.2-gtk-jni liblucene-java-doc eclipse-pde-gcj libjaxp1.3-java-gcj
Använd "apt-get autoremove" för att ta bort dem.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
tarek@ubuntu:~$ 

```The reason I want to have the latest versions of both java and eclipse is that the swing applications did not work. Hope someone can help.

Regards Tarek.

---

### Post by Mighty_Joe on 2009-09-08
Have you tried running update-java-alternatives as recommended [here?]("https://help.ubuntu.com/community/Java")

---

### Post by isato on 2009-09-08
> **Mighty_Joe said:**
> Have you tried running update-java-alternatives as recommended [here?]("https://help.ubuntu.com/community/Java")

This is what I get. Should I choose any of these? 

tarek@ubuntu:~$ sudo update-java-alternatives -l
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj
tarek@ubuntu:~$

Well something happend 

tarek@ubuntu:~$ sudo update-java-alternatives -s java-6-sun
Låter "/usr/lib/jvm/java-6-sun/bin/appletviewer" tillhandahålla "appletviewer".
Låter "/usr/lib/jvm/java-6-sun/bin/apt" tillhandahålla "apt".
Låter "/usr/lib/jvm/java-6-sun/bin/extcheck" tillhandahålla "extcheck".
Låter "/usr/lib/jvm/java-6-sun/bin/HtmlConverter" tillhandahålla "HtmlConverter".
Låter "/usr/lib/jvm/java-6-sun/bin/idlj" tillhandahålla "idlj".
Låter "/usr/lib/jvm/java-6-sun/bin/jarsigner" tillhandahålla "jarsigner".
Låter "/usr/lib/jvm/java-6-sun/bin/jar" tillhandahålla "jar".
Låter "/usr/lib/jvm/java-6-sun/bin/javac" tillhandahålla "javac".
Låter "/usr/lib/jvm/java-6-sun/bin/javadoc" tillhandahålla "javadoc".
Låter "/usr/lib/jvm/java-6-sun/bin/javah" tillhandahålla "javah".
Låter "/usr/lib/jvm/java-6-sun/bin/javap" tillhandahålla "javap".
Låter "/usr/lib/jvm/java-6-sun/bin/jconsole" tillhandahålla "jconsole".
Låter "/usr/lib/jvm/java-6-sun/bin/jdb" tillhandahålla "jdb".
Låter "/usr/lib/jvm/java-6-sun/bin/jhat" tillhandahålla "jhat".
Låter "/usr/lib/jvm/java-6-sun/bin/jinfo" tillhandahålla "jinfo".
Låter "/usr/lib/jvm/java-6-sun/bin/jmap" tillhandahålla "jmap".
Låter "/usr/lib/jvm/java-6-sun/bin/jps" tillhandahålla "jps".
Låter "/usr/lib/jvm/java-6-sun/bin/jrunscript" tillhandahålla "jrunscript".
Låter "/usr/lib/jvm/java-6-sun/bin/jsadebugd" tillhandahålla "jsadebugd".
Låter "/usr/lib/jvm/java-6-sun/bin/jstack" tillhandahålla "jstack".
Låter "/usr/lib/jvm/java-6-sun/bin/jstatd" tillhandahålla "jstatd".
Låter "/usr/lib/jvm/java-6-sun/bin/jstat" tillhandahålla "jstat".
Låter "/usr/lib/jvm/java-6-sun/bin/native2ascii" tillhandahålla "native2ascii".
Låter "/usr/lib/jvm/java-6-sun/bin/rmic" tillhandahålla "rmic".
Låter "/usr/lib/jvm/java-6-sun/bin/schemagen" tillhandahålla "schemagen".
Låter "/usr/lib/jvm/java-6-sun/bin/serialver" tillhandahålla "serialver".
Låter "/usr/lib/jvm/java-6-sun/bin/wsgen" tillhandahålla "wsgen".
Låter "/usr/lib/jvm/java-6-sun/bin/wsimport" tillhandahålla "wsimport".
Låter "/usr/lib/jvm/java-6-sun/bin/xjc" tillhandahålla "xjc".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel" tillhandahålla "ControlPanel".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/java" tillhandahålla "java".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/java_vm" tillhandahålla "java_vm".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/javaws" tillhandahålla "javaws".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/jcontrol" tillhandahålla "jcontrol".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/jexec" tillhandahålla "jexec".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/keytool" tillhandahålla "keytool".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/orbd" tillhandahålla "orbd".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/pack200" tillhandahålla "pack200".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/policytool" tillhandahålla "policytool".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/rmid" tillhandahålla "rmid".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry" tillhandahålla "rmiregistry".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/servertool" tillhandahålla "servertool".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/tnameserv" tillhandahålla "tnameserv".
Låter "/usr/lib/jvm/java-6-sun/jre/bin/unpack200" tillhandahålla "unpack200".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "firefox-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "iceape-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "iceweasel-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "midbrowser-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "mozilla-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "xulrunner-1.9-javaplugin.so".
Låter "/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" tillhandahålla "xulrunner-javaplugin.so".
tarek@ubuntu:~$




tarek@ubuntu:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
tarek@ubuntu:~$

---

### Post by isato on 2009-09-08
Now eclipse is the problem. It starts and asks for workspace. When I click OK. I get an error message that could be find in some log but the the window close it self very fast So I can't see where.

---

### Post by isato on 2009-09-08
I found the log file 

```
!SESSION 2009-01-31 22:55:08.582 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.2
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=sv_SE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2009-01-31 22:55:15.210
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-01-31 22:55:15.210
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-01-31 22:55:15.211
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-01-31 22:55:15.211
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2009-05-19 20:31:40.125 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.2
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=sv_SE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2009-05-19 20:31:45.370
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-19 20:31:45.370
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-19 20:31:45.371
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-19 20:31:45.371
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2009-08-20 19:48:07.985 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=sv_SE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2009-08-20 19:48:18.545
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-20 19:48:18.545
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-20 19:48:18.545
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-20 19:48:18.545
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2009-08-25 22:47:13.384 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=sv_SE
Command-line arguments:  -os linux -ws gtk -arch x86_64
!ENTRY org.eclipse.osgi 4 0 2009-09-02 22:14:03.190
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:182)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
        at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:516)
        at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
        at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:143)
        at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:88)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
        at org.eclipse.equinox.launcher.Main.main(Main.java:1287)
!SESSION 2009-09-02 22:13:40.406 -----------------------------------------------
eclipse.buildId=I20090611-1540
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=sv_SE
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.252
!MESSAGE The installable unit org.eclipse.core.resources.compatibility.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.255
!MESSAGE The installable unit org.eclipse.jdt.compiler.tool.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.256
!MESSAGE The installable unit org.eclipse.core.filesystem.linux.x86.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.257
!MESSAGE The installable unit org.eclipse.ecf.provider.filetransfer.httpclient.ssl.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.257
!MESSAGE The installable unit org.eclipse.ui.workbench.compatibility.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.259
!MESSAGE The installable unit org.eclipse.jdt.compiler.apt.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.directorywatcher 4 0 2009-09-02 22:14:24.264
!MESSAGE The installable unit org.eclipse.equinox.launcher.gtk.linux.x86.translated_host_properties is missing the filename property.
MESSAGE The installable unit org.eclipse.equinox.launcher.gtk.linux.x86.translated_host_properties is missing the filename property.

!ENTRY org.eclipse.equinox.p2.reconciler.dropins 4 0 2009-09-02 22:14:26.632
!MESSAGE
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.equinox.internal.p2.reconciler.dropins.Activator.start() of bundle org.eclipse.equinox.p2.reconciler.dropins.
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:805)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:754)
        at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:352)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:370)
        at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1068)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:557)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:464)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:248)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:445)
        at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:220)
        at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:330)
Caused by: java.lang.IllegalStateException: Profile SDKProfile is not current.
        at org.eclipse.equinox.internal.p2.engine.SimpleProfileRegistry.lockProfile(SimpleProfileRegistry.java:662)
        at org.eclipse.equinox.internal.provisional.p2.engine.Engine.perform(Engine.java:44)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.ProfileSynchronizer.executePlan(ProfileSynchronizer.java:466)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.ProfileSynchronizer.synchronize(ProfileSynchronizer.java:107)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.Activator.synchronize(Activator.java:422)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.Activator.start(Activator.java:171)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:782)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:773)
        ... 10 more
Root exception:
java.lang.IllegalStateException: Profile SDKProfile is not current.
        at org.eclipse.equinox.internal.p2.engine.SimpleProfileRegistry.lockProfile(SimpleProfileRegistry.java:662)
        at org.eclipse.equinox.internal.provisional.p2.engine.Engine.perform(Engine.java:44)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.ProfileSynchronizer.executePlan(ProfileSynchronizer.java:466)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.ProfileSynchronizer.synchronize(ProfileSynchronizer.java:107)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.Activator.synchronize(Activator.java:422)
        at org.eclipse.equinox.internal.p2.reconciler.dropins.Activator.start(Activator.java:171)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:782)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:773)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:754)
        at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:352)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:370)
        at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1068)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:557)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:464)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:248)
        at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:445)
        at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:220)
        at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:330)
................................

```



ohhh it is huge !!

---

### Post by rob-ward on 2009-09-08
I think that your eclipse install may be corrupt, you could try installing it again, try following the instructions at [http://rob-ward.co.uk/thisarticle.php?id=20](http://rob-ward.co.uk/thisarticle.php?id=20) it tells you how to install the newest eclipse.

Hope that helps,

---

### Post by isato on 2009-09-08
> **rob-ward said:**
> I think that your eclipse install may be corrupt, you could try installing it again, try following the instructions at [http://rob-ward.co.uk/thisarticle.php?id=20](http://rob-ward.co.uk/thisarticle.php?id=20) it tells you how to install the newest eclipse.

Hope that helps,

[FONT=Verdana][SIZE=2]
We can now check that eclipse loads by running the following command: 

**./eclipse** 


Thank you very much but it does not load.

[/SIZE][/FONT]

---

### Post by isato on 2009-09-08
> **isato said:**
> [FONT=Verdana][SIZE=2]
We can now check that eclipse loads by running the following command: 

**./eclipse** 


Thank you very much but it does not load.

[/SIZE][/FONT]
  

Well

  PID TTY          TIME CMD
 5873 pts/1    00:00:00 bash
 7532 pts/1    00:00:00 bash
 7533 pts/1    00:00:00 eclipse
 7544 pts/1    00:00:02 java
 7554 pts/1    00:00:00 ps

Maybe its very slow? eclipse does not show up.

This is what is happening without doing anything. I shuts itself down.

tarek@ubuntu:/opt$ ./eclipse
tarek@ubuntu:/opt$ ps
  PID TTY          TIME CMD
 5873 pts/1    00:00:00 bash
 7630 pts/1    00:00:00 bash
 7631 pts/1    00:00:00 eclipse
 7642 pts/1    00:00:01 java
 7652 pts/1    00:00:00 ps
tarek@ubuntu:/opt$ ps
  PID TTY          TIME CMD
 5873 pts/1    00:00:00 bash
 7659 pts/1    00:00:00 ps

---

### Post by rob-ward on 2009-09-09
Can I ask what specifcation your computer is, Eclipse is a bit of a processor/memory hog.

The other thing to sdo is to make sure that eclipse is loading with the correct java implementation, I arn't sure about Eclipse 3.5 but older versions used to ignore the system default and load with the open java anyway which used to give lots of crashes for me. This can be fixed using these instrustions:[http://rob-ward.co.uk/thisarticle.php?id=11](http://rob-ward.co.uk/thisarticle.php?id=11)

I hope that helps, if not see if you can find any debug logs.

---

