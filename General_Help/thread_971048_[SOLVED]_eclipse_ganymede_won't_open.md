---
title: "[SOLVED] eclipse ganymede won't open"
date: 2008-11-04
forum: General Help
---

### Post by suicidejack on 2008-11-04
I use eclipse a lot in school.  I had eclipse ganymede installed previously but it kept closing randomly and without warning about every 10 minutes.  Needless to say I lost a lot of work because of this.  So I decided to reinstall eclipse.  Bad idea as I now can't even open eclipse after having reinstalled it.  Here is the error that I am getting in my .metalog.log file (from what I can tell some temp file can not be created which is prohibiting eclipse from starting). 
> !ENTRY org.eclipse.osgi 4 0 2008-11-04 16:32:09.846
!MESSAGE 
!STACK 0
java.io.IOException: cannot create temporary file
   at java.io.File.createTempFile(libgcj.so.90)
   at org.eclipse.osgi.storagemanager.StorageManager.createTempFile(StorageManager.java:713)
   at org.eclipse.osgi.storagemanager.StorageManager.getOutputStream(StorageManager.java:775)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.saveBundleDatas(BaseStorage.java:535)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.saveAllData(BaseStorage.java:428)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.frameworkStop(BaseStorage.java:828)
   at org.eclipse.osgi.baseadaptor.BaseAdaptor.frameworkStop(BaseAdaptor.java:272)
   at org.eclipse.osgi.framework.internal.core.SystemBundleActivator.stop(SystemBundleActivator.java:66)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1050)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.suspendAllBundles(StartLevelManager.java:685)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.decFWSL(StartLevelManager.java:637)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:312)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.shutdown(StartLevelManager.java:257)
   at org.eclipse.osgi.framework.internal.core.SystemBundle.suspend(SystemBundle.java:236)
   at org.eclipse.osgi.framework.internal.core.Framework.shutdown(Framework.java:678)
   at org.eclipse.osgi.framework.internal.core.Framework.close(Framework.java:576)
   at org.eclipse.osgi.framework.internal.core.OSGi.close(OSGi.java:41)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.shutdown(EclipseStarter.java:424)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:200)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1212)

!ENTRY org.eclipse.osgi 4 0 2008-11-04 16:32:09.866
!MESSAGE 
!STACK 0
java.io.IOException: cannot create temporary file
   at java.io.File.createTempFile(libgcj.so.90)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.saveStateData(BaseStorage.java:590)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.saveAllData(BaseStorage.java:429)
   at org.eclipse.osgi.internal.baseadaptor.BaseStorage.frameworkStop(BaseStorage.java:828)
   at org.eclipse.osgi.baseadaptor.BaseAdaptor.frameworkStop(BaseAdaptor.java:272)
   at org.eclipse.osgi.framework.internal.core.SystemBundleActivator.stop(SystemBundleActivator.java:66)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1050)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.suspendAllBundles(StartLevelManager.java:685)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.decFWSL(StartLevelManager.java:637)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:312)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.shutdown(StartLevelManager.java:257)
   at org.eclipse.osgi.framework.internal.core.SystemBundle.suspend(SystemBundle.java:236)
   at org.eclipse.osgi.framework.internal.core.Framework.shutdown(Framework.java:678)
   at org.eclipse.osgi.framework.internal.core.Framework.close(Framework.java:576)
   at org.eclipse.osgi.framework.internal.core.OSGi.close(OSGi.java:41)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.shutdown(EclipseStarter.java:424)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:200)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1212)
I have looked all over online and can't find a solution so hopefully someone can solve this problem!  Thanks in advance for any help.  I am running Ubuntu 8.10 and can give anyone some more info if you need it.

---

### Post by suicidejack on 2008-11-04
to answer my own thread i ended up reinstalling eclipse (again) using these directions - [http://ubuntuforums.org/showthread.php?t=941461]("http://ubuntuforums.org/showthread.php?t=941461")

eclipse appears to work now - hopefully it won't shutdown every ten minutes...

---

