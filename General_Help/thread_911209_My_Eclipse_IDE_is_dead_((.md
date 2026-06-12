---
title: "My Eclipse IDE is dead :(("
date: 2008-09-05
forum: General Help
---

### Post by [CPR]-AL.exe on 2008-09-05
Suddenly my Eclipse stopped lunching. And popped up a window, saying that an error occured. Here's the log:

```
!SESSION 2008-09-02 16:49:22.237 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

This is a continuation of log file /home/alexe/eclipse-workspace/.metadata/.bak_0.log
Created Time: 2008-09-02 16:49:31.074

!ENTRY org.eclipse.core.resources 2 10035 2008-09-02 16:49:31.074
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.jface 2 0 2008-09-02 16:50:46.672
!MESSAGE The image could not be loaded: URLImageDescriptor(bundleentry://118/icons/python.gif)
!STACK 0
org.eclipse.jface.resource.DeviceResourceException: Unable to create resource URLImageDescriptor(bundleentry://118/icons/python.gif)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:173)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:83)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:114)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.addActionToMenu(ConsoleDropDownAction.java:105)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.getMenu(ConsoleDropDownAction.java:89)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:514)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
	at org.eclipse.jface.action.ActionContributionItem$6.handleEvent(ActionContributionItem.java:441)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
!SESSION 2008-09-03 13:50:04.591 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-03 13:50:08.577
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-03 13:50:08.577
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-03 13:50:08.577
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-03 13:50:08.577
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.jface 2 0 2008-09-03 18:59:15.111
!MESSAGE The image could not be loaded: URLImageDescriptor(bundleentry://118/icons/python.gif)
!STACK 0
org.eclipse.jface.resource.DeviceResourceException: Unable to create resource URLImageDescriptor(bundleentry://118/icons/python.gif)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:173)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:83)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:114)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.addActionToMenu(ConsoleDropDownAction.java:105)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.getMenu(ConsoleDropDownAction.java:89)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:514)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
	at org.eclipse.jface.action.ActionContributionItem$6.handleEvent(ActionContributionItem.java:441)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.jface 2 0 2008-09-03 20:41:55.126
!MESSAGE The image could not be loaded: URLImageDescriptor(bundleentry://118/icons/python.gif)
!STACK 0
org.eclipse.jface.resource.DeviceResourceException: Unable to create resource URLImageDescriptor(bundleentry://118/icons/python.gif)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:173)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:83)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:114)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.addActionToMenu(ConsoleDropDownAction.java:105)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.getMenu(ConsoleDropDownAction.java:89)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:514)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
	at org.eclipse.jface.action.ActionContributionItem$6.handleEvent(ActionContributionItem.java:441)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
!SESSION 2008-09-05 13:33:38.849 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 13:33:42.576
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 13:33:42.577
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 13:33:42.577
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 13:33:42.577
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 13:33:43.394
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.jface 2 0 2008-09-05 14:25:54.587
!MESSAGE The image could not be loaded: URLImageDescriptor(bundleentry://118/icons/python.gif)
!STACK 0
org.eclipse.jface.resource.DeviceResourceException: Unable to create resource URLImageDescriptor(bundleentry://118/icons/python.gif)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:173)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:83)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:114)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.addActionToMenu(ConsoleDropDownAction.java:105)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.getMenu(ConsoleDropDownAction.java:89)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:514)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
	at org.eclipse.jface.action.ActionContributionItem$6.handleEvent(ActionContributionItem.java:441)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.python.pydev 4 4 2008-09-05 14:43:37.850
!MESSAGE org.eclipse.jface.text.BadLocationException
!STACK 0
java.lang.RuntimeException: org.eclipse.jface.text.BadLocationException
	at com.python.pydev.analysis.tabnanny.TabNannyDocIterator.internalBuildNext(TabNannyDocIterator.java:184)
	at com.python.pydev.analysis.tabnanny.TabNannyDocIterator.buildNext(TabNannyDocIterator.java:50)
	at com.python.pydev.analysis.tabnanny.TabNannyDocIterator.next(TabNannyDocIterator.java:45)
	at com.python.pydev.analysis.tabnanny.TabNanny.analyzeDoc(TabNanny.java:46)
	at com.python.pydev.analysis.OccurrencesAnalyzer.analyzeDocument(OccurrencesAnalyzer.java:57)
	at com.python.pydev.analysis.OccurrencesAnalyzer.analyzeDocument(OccurrencesAnalyzer.java:37)
	at com.python.pydev.analysis.builder.AnalysisBuilderRunnable.doAnalysis(AnalysisBuilderRunnable.java:185)
	at com.python.pydev.analysis.builder.AnalysisBuilderRunnable.run(AnalysisBuilderRunnable.java:130)
	at com.python.pydev.analysis.builder.AnalysisBuilderVisitor$1.run(AnalysisBuilderVisitor.java:103)
	at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
Caused by: org.eclipse.jface.text.BadLocationException
	at org.eclipse.jface.text.AbstractDocument.getChar(AbstractDocument.java:732)
	at org.eclipse.core.internal.filebuffers.SynchronizableDocument.getChar(SynchronizableDocument.java:106)
	at com.python.pydev.analysis.tabnanny.TabNannyDocIterator.internalBuildNext(TabNannyDocIterator.java:86)
	... 9 more
!SESSION 2008-09-05 15:02:11.312 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:02:13.540
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:02:13.541
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:02:13.541
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:02:13.541
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2008-09-05 15:34:22.741 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:34:24.982
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:34:24.982
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:34:24.983
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 15:34:24.983
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 15:34:25.568
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.jface 2 0 2008-09-05 15:56:59.263
!MESSAGE The image could not be loaded: URLImageDescriptor(bundleentry://118/icons/python.gif)
!STACK 0
org.eclipse.jface.resource.DeviceResourceException: Unable to create resource URLImageDescriptor(bundleentry://118/icons/python.gif)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:173)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:83)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:87)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:114)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:997)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:843)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:279)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.addActionToMenu(ConsoleDropDownAction.java:105)
	at org.eclipse.ui.internal.console.ConsoleDropDownAction.getMenu(ConsoleDropDownAction.java:89)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:514)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
	at org.eclipse.jface.action.ActionContributionItem$6.handleEvent(ActionContributionItem.java:441)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
!SESSION 2008-09-05 18:04:10.175 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:04:12.691
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:04:12.692
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:04:12.692
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:04:12.692
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:04:13.284
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:04:13.299
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:04:13.351
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:07:12.664 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:14.933
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:14.934
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:14.934
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:14.934
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:07:15.428
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:15.448
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:15.456
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:07:25.625 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:27.883
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:27.883
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:27.883
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:27.884
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:07:28.537
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:28.555
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:28.583
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:07:42.435 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:45.004
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:45.005
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:45.005
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:07:45.005
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:07:45.595
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:45.612
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:07:45.623
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:19:44.351 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:19:46.815
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:19:46.816
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:19:46.816
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:19:46.816
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:19:47.413
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:19:47.428
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:19:47.457
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:26:17.090 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:26:19.908
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:26:19.908
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:26:19.909
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 18:26:19.909
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:26:20.424
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:26:20.438
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:26:20.443
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 18:51:00.379 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:51:16.224
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:51:16.245
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (27).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:51:16.254
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.core.resources (27).
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:125)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 13 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	... 23 more
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
!SESSION 2008-09-05 18:51:39.642 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:51:41.857
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:51:41.871
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (27).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:51:41.880
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.core.resources (27).
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:125)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 13 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	... 23 more
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
!SESSION 2008-09-05 18:52:23.120 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:52:24.385
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:52:24.399
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (27).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:52:24.446
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.core.resources (27).
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:125)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 13 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	... 23 more
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
!SESSION 2008-09-05 18:52:37.467 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:52:38.957
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:52:38.971
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (27).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:52:38.990
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.core.resources (27).
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:125)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 13 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	... 23 more
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
!SESSION 2008-09-05 18:55:38.652 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 18:55:41.164
!MESSAGE The workspace exited with unsaved changes in the previous session; refreshing workspace to recover changes.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:55:41.214
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (27).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 18:55:41.242
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:114)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.core.resources (27).
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:125)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:427)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:193)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:368)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:33)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:441)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:397)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:385)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:87)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 13 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.core.resources.ResourcesPlugin.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:984)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:346)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:265)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:400)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:111)
	... 23 more
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element '/treeProcessor/src/modules/db_utils/db_users.py' not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:670)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1326)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1953)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1716)
	at org.eclipse.core.resources.ResourcesPlugin.start(ResourcesPlugin.java:376)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:1009)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1003)
	... 28 more
!SESSION 2008-09-05 19:01:01.851 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:05.419
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:05.419
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:05.420
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:05.420
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 19:01:05.910
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 19:01:05.923
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 19:01:05.930
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
!SESSION 2008-09-05 19:01:25.477 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=ru_RU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:28.115
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:28.115
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:28.115
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-05 19:01:28.115
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-09-05 19:01:28.679
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-09-05 19:01:28.695
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (41).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /treeProcessor/src/modules/db_utils/db_users.py not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-09-05 19:01:28.700
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 14 more
```

I tried to reinstall it - it didn't help, i tried to download latest classic eclipse (3.4), but it also won't launch :( 

Any help is appreciated... i really don't know what to do, and it's my main tool i use a office :(

---

### Post by [CPR]-AL.exe on 2008-09-05
Solved it by renamig my workspace dir and importing projects to new one... idiotism :))

---

