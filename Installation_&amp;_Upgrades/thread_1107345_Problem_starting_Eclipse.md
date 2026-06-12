---
title: "Problem starting Eclipse"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by prady on 2009-03-26
Hi All,

I am having trouble starting Eclipse. It was working fine until last week I tried installing a plug-in. I get following message every time I try to start Eclipse- "An error has occurred. See the log file /home/user/workspace/.metadata/.log." 

Following are contents of the log file.

```
!ENTRY org.eclipse.core.resources 2 10035 2009-03-26 17:20:01.894
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2009-03-26 17:20:01.895
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (112).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.VMClassLoader.defineClass(libgcj.so.90)
   at java.lang.ClassLoader.defineClass(libgcj.so.90)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /HelloWorld/HelloWorld.cpp not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.watson.ElementTree.immutable(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.SaveManager.restore(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.SaveManager.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.Workspace.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.Workspace.open(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...38 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /HelloWorld/HelloWorld.cpp not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.watson.ElementTree.immutable(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.SaveManager.restore(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.SaveManager.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.Workspace.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.resources.Workspace.open(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.VMClassLoader.defineClass(libgcj.so.90)
   at java.lang.ClassLoader.defineClass(libgcj.so.90)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at ,org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2009-03-26 17:20:01.916
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor$2
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...11 more
```

I have already wasted quite a lot of time on this. I have tried apt-get purge to remove all and re install everything. I have tried reinstalling JDK and JRE. I have tried starting eclipse with sudo. Nothing seems to work. Anyone has any suggestions?

Thanks in advance!
Prady

---

### Post by andrewc6l on 2009-03-27
It looks as if Eclipse has lost track of some resources in your existing workspace. Try (from a command line):
  eclipse -clean

If that doesn't work, you might be able to close all open windows, close all perspectives, save & exit and restart.

If that fails, try creating a new workspace and bringing your work in.

---

### Post by prady on 2009-03-27
Thank you for replying.. and well. I am stumped. eclipse -clean worked the first time I tried it. I looked up the command and found this page

[http://www.eclipsezone.com/eclipse/forums/t61566.html]("http://www.eclipsezone.com/eclipse/forums/t61566.html")

I changed my eclipse.ini , eclipse won't start. I decided to revert the changes and provide clean argument every time I want to start the program. Now even that does not work.

I think you have a hang of what is happening here.. Can you think of why the reverted changes won't work? What can be done to correct it?

---

