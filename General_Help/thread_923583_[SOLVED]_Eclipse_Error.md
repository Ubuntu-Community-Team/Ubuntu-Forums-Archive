---
title: "[SOLVED] Eclipse Error"
date: 2008-09-18
forum: General Help
---

### Post by Gibbs on 2008-09-18
I have an error when trying to run Eclipse via the Adobe Flex Builder. I get:
> An error has occurred. See the log file
/home/gibbs/Flex/workspace/.metadata/.log.

This happened before because I was running gksu. Not it's just randomly started happening again and I can't seem to solve it. I've tried deleting various directories, i've installed everything "eclipse" from the synaptic package manager and just re-installed Flex.

Heres the log. Google doesn't provide anything useful:
```
!SESSION 2008-09-18 20:11:09.052 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.5.0_16
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-09-18 20:11:10.054
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-18 20:11:10.055
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-18 20:11:10.055
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-18 20:11:10.055
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.ui 2 0 2008-09-18 20:11:13.048
!MESSAGE Warnings while parsing the key bindings from the 'org.eclipse.ui.commands' extension point
!SUBENTRY 1 org.eclipse.ui 2 0 2008-09-18 20:11:13.048
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.ZoomIn'
!SUBENTRY 1 org.eclipse.ui 2 0 2008-09-18 20:11:13.048
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.ZoomOut'
!SUBENTRY 1 org.eclipse.ui 2 0 2008-09-18 20:11:13.048
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.css', id='com.adobe.flexbuilder.editors.css.design.Magnify100'
!SUBENTRY 1 org.eclipse.ui 2 0 2008-09-18 20:11:13.049
!MESSAGE Cannot bind to an undefined command: plug-in='com.adobe.flexbuilder.editors.actionscript', id='com.adobe.flexbuilder.editors.actionscript.rename.element'

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-18 20:11:17.889
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:153)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1109)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1090)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:954)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:162)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:465)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1638)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:430)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1587)
	at org.eclipse.swt.widgets.Display.release(Display.java:2904)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:230)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:111)
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

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-18 20:11:17.892
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:153)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1109)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1090)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:954)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:162)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:465)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1638)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:430)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1587)
	at org.eclipse.swt.widgets.Display.release(Display.java:2904)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:230)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:111)
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

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-18 20:11:17.893
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:153)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1109)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1090)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:954)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:162)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:465)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1638)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:430)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1587)
	at org.eclipse.swt.widgets.Display.release(Display.java:2904)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:230)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:111)
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

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-18 20:11:17.895
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:153)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1109)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1090)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:954)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1033)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:162)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:465)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1638)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:957)
	at org.eclipse.swt.widgets.Control.release(Control.java:2546)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:430)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1587)
	at org.eclipse.swt.widgets.Display.release(Display.java:2904)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:230)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:111)
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

!ENTRY org.eclipse.osgi 4 0 2008-09-18 20:11:18.029
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147221164
	at org.eclipse.swt.browser.Browser.error(Browser.java:1382)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:1865)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateDynamicContentForPage(BrowserIntroPartImplementation.java:249)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:445)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:652)
	at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
	at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:439)
	at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:264)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(ViewIntroAdapterPart.java:70)
	at org.eclipse.ui.internal.ViewIntroAdapterPart$1.propertyChanged(ViewIntroAdapterPart.java:55)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:346)
	at org.eclipse.ui.internal.WorkbenchPartReference.fireZoomChange(WorkbenchPartReference.java:511)
	at org.eclipse.ui.internal.PartPane.setZoomed(PartPane.java:333)
	at org.eclipse.ui.internal.PartStack.setZoomed(PartStack.java:1233)
	at org.eclipse.ui.internal.PartSashContainer.zoomIn(PartSashContainer.java:879)
	at org.eclipse.ui.internal.PartSashContainer.childRequestZoomIn(PartSashContainer.java:900)
	at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
	at org.eclipse.ui.internal.PartStack.childRequestZoomIn(PartStack.java:1183)
	at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
	at org.eclipse.ui.internal.PerspectiveHelper.zoomIn(PerspectiveHelper.java:1315)
	at org.eclipse.ui.internal.WorkbenchPage.setState(WorkbenchPage.java:3617)
	at org.eclipse.ui.internal.WorkbenchPage.toggleZoom(WorkbenchPage.java:3678)
	at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(WorkbenchIntroManager.java:200)
	at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:135)
	at org.eclipse.ui.application.WorkbenchWindowAdvisor.openIntro(WorkbenchWindowAdvisor.java:172)
	at org.eclipse.ui.internal.ide.IDEWorkbenchWindowAdvisor.openIntro(IDEWorkbenchWindowAdvisor.java:424)
	at org.eclipse.ui.internal.WorkbenchWindow.open(WorkbenchWindow.java:676)
	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:819)
	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)
	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)
	at org.eclipse.ui.internal.Workbench$16.run(Workbench.java:1415)
	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)
	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)
	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)
	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)
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
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-09-18 20:11:18.085
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-09-18 20:11:18.085
!MESSAGE Bundle update@../../../home/gibbs/Flex/eclipse/plugins/com.adobe.flexbuilder.debug.e33_3.0.204732/ was not resolved.
!SUBENTRY 2 com.adobe.flexbuilder.debug.e33 2 0 2008-09-18 20:11:18.085
!MESSAGE Missing required bundle org.eclipse.debug.ui_[3.3.0,99.0.0).

!ENTRY org.eclipse.osgi 2 0 2008-09-18 20:11:18.085
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-09-18 20:11:18.086
!MESSAGE Bundle update@../../../home/gibbs/Flex/eclipse/plugins/com.adobe.flexbuilder.debug.e33_3.0.204732/ [245] was not resolved.
!SUBENTRY 2 com.adobe.flexbuilder.debug.e33 2 0 2008-09-18 20:11:18.086
!MESSAGE Missing required bundle org.eclipse.debug.ui_[3.3.0,99.0.0).
```

Any help much appreciated!

---

### Post by Gibbs on 2008-09-19
After spending hours looking online for a solution and nothing coming up I thought I should post how I resolved this...

When starting Eclipse you chose your workspace directory. In the chosen path you'll find a **.metadata** hidden directory. You need to delete **properties.index** which is located in **path-to-workspace/.metadata/.plugins/org.eclipse.core.resources/.root/.indexes** file and re-launch.

For example on my machine it's located at: **/home/gibbs/Flex/workspace/.metadata/.plugins/org.eclipse.core.resources/.root/.indexes**

Hope that helps someone.

---

### Post by monik425 on 2009-09-26
I did what you say but it didnt work  :(

---

### Post by vlatkop on 2009-12-12
Same error here on:

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

$ uname -r
2.6.31-16-generic

while starting IBM Data Studio 2.2 IDE

I tried this:

[http://www-01.ibm.com/support/docview.wss?rcss=faqtt_1Q09&uid=swg21265773](http://www-01.ibm.com/support/docview.wss?rcss=faqtt_1Q09&uid=swg21265773)

but not helps...

Regards, Vlado

---

### Post by ztjames on 2009-12-19
it's not working ,man.

anyone help....

---

### Post by stevanbt on 2009-12-30
Hi,
I've successfully managed to get IBM Data Studio 2.2 to run under Karmic (I was previously getting "!MESSAGE Widget disposed too early!" errors).  I made the following changes:-

amend datastudio.ini, replace spaces with underscores for workspace path (dunno if this was absolutely necessary and you will have to create a matching path in your home directory) and added XULRunnerPath:-
```
-vm
./jre/bin/javaw
-data
@user.home/IBM/Data_Studio_2.2_stand-alone/workspace
-vmargs
-Xmx1024m
-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

```

Once it runs you may end up with problems getting buttons etc to work correctly in Data Studio.  If this happens try the following.

Run from a shell script like so:-
```
export GDK_NATIVE_WINDOWS=true
./datastudio
```

Hope this helps someone.

Thanks, Steve.

---

### Post by jhSillybuntu on 2010-01-05
Thanks stevanbt -- the export GDK_NATIVE_WINDOWS=true  solved the issue for me (with standard eclipse 3.5).

---

### Post by sansrival on 2010-01-21
Hi everyone,

I need a help about eclipse and flex. i installed the eclipse-php and also flex builder the .bin one. I opened eclipse and try if flex is ready to used but i was dissapointed. in file->new-> can't find my flex. Is there something wrong with my installation? im installing this and can't figured out what is the problem with eclipse and flex since yesterday. Help me guys thank you so much!!!:(

---

### Post by sansrival on 2010-01-21
oh i find it! i find my flex builder in eclipse but when im going to create a new project and then select Flex builder i can't select it why?

thanks cris

---

### Post by lionstone on 2010-04-24
Nothing above fixed this for me running Flex builder on Hardy. I had to remove the project and create a new Flex project using the same sources. 

I was experiencing a situation where there was a permanent error on my project but it wasn't providing any information about what was wrong. But removing the project by deleting all the hidden  eclipse/flex folders in the directory did the trick.

---

### Post by hamidoo on 2010-04-26
It worked for me when appending the following line in eclipse.ini
```

-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

```

thx stevanbt

---

### Post by hamidoo on 2010-04-26
I had this problem in for Rational Software Architect for WebSphere Software V7.5 and it worked for me only after appedning the following line in eclipse.ini in /opt/IBM/SDP7.5

```

-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

```

thx stevanbt

---

### Post by stuarttaylor on 2010-10-27
> **hamidoo said:**
> It worked for me when appending the following line in eclipse.ini
```

-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

```

thx stevanbt

Ditto, also worked for me :-D

Thanks

---

### Post by annu2127 on 2010-11-11
Here is the problem as reported in the /.metadata/.log file
==================================================
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1597)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1820)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:733)
at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged
 -Dorg.eclipse.swt.browser.XULRunnerPath=/dev/nul
 ==================================================
Here is how I solved the issue in Ubunty Hardy Harron
 sudo apt-get install xulrunner
 # Include this in the .bachrc
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
export LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME:$LD_LIBRARY_PATH
 and for safety also download the SWT binaries for Linux.  Installation procedure:  
 *  unpack the archive: swt-*-linux-gtk.zip
*  copy libswt*.so to
%JAVA_HOME%/jre/lib/i386, (%JAVA_HOME% is the folder where JRE is
installed on your system; e.g.: opt/jdk1.5._07),
*  copy swt.jar to %JAVA_HOME%/jre/lib/ext
 ==================================================

---

### Post by Rfarchou on 2011-05-10
It worked for me on Ubuntu10.04 when appending the following line in eclipse.ini
-Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner

---

### Post by OwenRackham on 2012-03-06
I solved this by running eclipse from the command line with argument -clean

eclipse -clean

assuming you have it in you path.

---

