---
title: "[SOLVED] Wine help!"
date: 2008-08-24
forum: General Help
---

### Post by claymater on 2008-08-24
Ok so im running "aptana" in wine (I know it comes out for linux, but I have a 64-bit version and I dont feel like putting it in as a plugin on eclips) 

But When I open the program (it is installed) it gives me a "An error has occurred. See the log file." Message.. what is wrong?!

---

### Post by unca.paka on 2008-08-24
Did you check the log? What was the error it gave?

---

### Post by claymater on 2008-08-24
> **unca.paka said:**
> Did you check the log? What was the error it gave?

Ok here was everything in the file.. (sorry its so long) 


```
!SESSION 2008-08-24 17:35:58.797 -----------------------------------------------

eclipse.buildId=unknown

java.version=1.6.0_05

java.vendor=Sun Microsystems Inc.

BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

Framework arguments:  C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio

Command-line arguments:  -os win32 -ws win32 -arch x86 C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio



!ENTRY org.eclipse.ui 4 4 2008-08-24 17:36:24.761

!MESSAGE Unable to find Action Set: com.aptana.ide.server.ui.launchActionSet



!ENTRY org.eclipse.osgi 4 0 2008-08-24 17:36:25.363

!MESSAGE Application error

!STACK 1

org.eclipse.swt.SWTError: No more handles

	at org.eclipse.swt.SWT.error(SWT.java:3589)

	at org.eclipse.swt.SWT.error(SWT.java:3481)

	at org.eclipse.swt.SWT.error(SWT.java:3452)

	at org.eclipse.swt.graphics.Image.<init>(Image.java:724)

	at com.aptana.ide.editors.views.profiles.ProfilesView.fillEnvironmentTable(ProfilesView.java:1329)

	at com.aptana.ide.editors.views.profiles.ProfilesView.createPartControl(ProfilesView.java:1010)

	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)

	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)

	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)

	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)

	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)

	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)

	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)

	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)

	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)

	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)

	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)

	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)

	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)

	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)

	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)

	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2436)

	at org.eclipse.ui.internal.WorkbenchWindow$6.run(WorkbenchWindow.java:2616)

	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)

	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2597)

	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:658)

	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:811)

	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)

	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)

	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1415)

	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)

	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)

	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)

	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)

	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)

	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)

	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)

	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)

	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:116)

	at com.aptana.ide.rcp.Application.run(Application.java:43)

	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)

	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)

	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)

	at java.lang.reflect.Method.invoke(Unknown Source)

	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)

	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)

	at org.eclipse.core.launcher.Main.run(Main.java:977)

	at org.eclipse.core.launcher.Main.main(Main.java:952)



!ENTRY org.eclipse.osgi 2 0 2008-08-24 17:36:25.380

!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:36:25.380

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.

!SUBENTRY 2 org.eclipse.swt.win32.win32.x86 2 0 2008-08-24 17:36:25.381

!MESSAGE Missing Constraint: Fragment-Host: org.eclipse.swt; bundle-version="[3.0.0,4.0.0)"

!SUBENTRY 2 org.eclipse.swt.win32.win32.x86 2 0 2008-08-24 17:36:25.381

!MESSAGE Another singleton version selected: org.eclipse.swt.win32.win32.x86_3.3.0.v3345f

!SESSION 2008-08-24 17:36:50.329 -----------------------------------------------

eclipse.buildId=unknown

java.version=1.6.0_05

java.vendor=Sun Microsystems Inc.

BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

Framework arguments:  C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio

Command-line arguments:  -os win32 -ws win32 -arch x86 C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio



!ENTRY org.eclipse.ui 4 4 2008-08-24 17:36:59.486

!MESSAGE Unable to find Action Set: com.aptana.ide.server.ui.launchActionSet



!ENTRY org.eclipse.osgi 4 0 2008-08-24 17:36:59.949

!MESSAGE Application error

!STACK 1

org.eclipse.swt.SWTError: No more handles

	at org.eclipse.swt.SWT.error(SWT.java:3589)

	at org.eclipse.swt.SWT.error(SWT.java:3481)

	at org.eclipse.swt.SWT.error(SWT.java:3452)

	at org.eclipse.swt.graphics.Image.<init>(Image.java:724)

	at com.aptana.ide.editors.views.profiles.ProfilesView.fillEnvironmentTable(ProfilesView.java:1329)

	at com.aptana.ide.editors.views.profiles.ProfilesView.createPartControl(ProfilesView.java:1010)

	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)

	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)

	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)

	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)

	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)

	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)

	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)

	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)

	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)

	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)

	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)

	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)

	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)

	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)

	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)

	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2436)

	at org.eclipse.ui.internal.WorkbenchWindow$6.run(WorkbenchWindow.java:2616)

	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)

	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2597)

	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:658)

	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:811)

	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)

	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)

	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1415)

	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)

	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)

	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)

	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)

	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)

	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)

	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)

	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)

	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:116)

	at com.aptana.ide.rcp.Application.run(Application.java:43)

	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)

	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)

	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)

	at java.lang.reflect.Method.invoke(Unknown Source)

	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)

	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)

	at org.eclipse.core.launcher.Main.run(Main.java:977)

	at org.eclipse.core.launcher.Main.main(Main.java:952)



!ENTRY org.eclipse.osgi 2 0 2008-08-24 17:36:59.981

!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:36:59.981

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.

!SESSION 2008-08-24 17:38:58.369 -----------------------------------------------

eclipse.buildId=unknown

java.version=1.6.0_05

java.vendor=Sun Microsystems Inc.

BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

Framework arguments:  C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio

Command-line arguments:  -os win32 -ws win32 -arch x86 C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio



!ENTRY org.eclipse.ui 4 4 2008-08-24 17:39:03.647

!MESSAGE Unable to find Action Set: com.aptana.ide.server.ui.launchActionSet



!ENTRY org.eclipse.osgi 4 0 2008-08-24 17:39:04.089

!MESSAGE Application error

!STACK 1

org.eclipse.swt.SWTError: No more handles

	at org.eclipse.swt.SWT.error(SWT.java:3589)

	at org.eclipse.swt.SWT.error(SWT.java:3481)

	at org.eclipse.swt.SWT.error(SWT.java:3452)

	at org.eclipse.swt.graphics.Image.<init>(Image.java:724)

	at com.aptana.ide.editors.views.profiles.ProfilesView.fillEnvironmentTable(ProfilesView.java:1329)

	at com.aptana.ide.editors.views.profiles.ProfilesView.createPartControl(ProfilesView.java:1010)

	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)

	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)

	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)

	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)

	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)

	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)

	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)

	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)

	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)

	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)

	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)

	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)

	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)

	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)

	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)

	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2436)

	at org.eclipse.ui.internal.WorkbenchWindow$6.run(WorkbenchWindow.java:2616)

	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)

	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2597)

	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:658)

	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:811)

	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)

	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)

	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1415)

	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)

	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)

	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)

	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)

	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)

	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)

	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)

	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)

	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:116)

	at com.aptana.ide.rcp.Application.run(Application.java:43)

	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)

	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)

	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)

	at java.lang.reflect.Method.invoke(Unknown Source)

	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)

	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)

	at org.eclipse.core.launcher.Main.run(Main.java:977)

	at org.eclipse.core.launcher.Main.main(Main.java:952)



!ENTRY org.eclipse.osgi 2 0 2008-08-24 17:39:04.120

!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:39:04.120

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.

!SESSION 2008-08-24 17:40:26.570 -----------------------------------------------

eclipse.buildId=unknown

java.version=1.6.0_05

java.vendor=Sun Microsystems Inc.

BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

Framework arguments:  C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio

Command-line arguments:  -os win32 -ws win32 -arch x86 C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio



!ENTRY org.eclipse.ui 4 4 2008-08-24 17:40:31.744

!MESSAGE Unable to find Action Set: com.aptana.ide.server.ui.launchActionSet



!ENTRY org.eclipse.osgi 4 0 2008-08-24 17:40:32.172

!MESSAGE Application error

!STACK 1

org.eclipse.swt.SWTError: No more handles

	at org.eclipse.swt.SWT.error(SWT.java:3589)

	at org.eclipse.swt.SWT.error(SWT.java:3481)

	at org.eclipse.swt.SWT.error(SWT.java:3452)

	at org.eclipse.swt.graphics.Image.<init>(Image.java:724)

	at com.aptana.ide.editors.views.profiles.ProfilesView.fillEnvironmentTable(ProfilesView.java:1329)

	at com.aptana.ide.editors.views.profiles.ProfilesView.createPartControl(ProfilesView.java:1010)

	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)

	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)

	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)

	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)

	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)

	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)

	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)

	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)

	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)

	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)

	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)

	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)

	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)

	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)

	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)

	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2436)

	at org.eclipse.ui.internal.WorkbenchWindow$6.run(WorkbenchWindow.java:2616)

	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)

	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2597)

	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:658)

	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:811)

	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)

	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)

	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1415)

	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)

	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)

	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)

	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)

	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)

	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)

	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)

	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)

	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:116)

	at com.aptana.ide.rcp.Application.run(Application.java:43)

	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)

	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)

	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)

	at java.lang.reflect.Method.invoke(Unknown Source)

	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)

	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)

	at org.eclipse.core.launcher.Main.run(Main.java:977)

	at org.eclipse.core.launcher.Main.main(Main.java:952)



!ENTRY org.eclipse.osgi 2 0 2008-08-24 17:40:32.202

!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:40:32.202

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.

!SESSION 2008-08-24 17:43:34.293 -----------------------------------------------

eclipse.buildId=unknown

java.version=1.6.0_05

java.vendor=Sun Microsystems Inc.

BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

Framework arguments:  C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio

Command-line arguments:  -os win32 -ws win32 -arch x86 C:\Program Files\Aptana\Aptana Studio\AptanaStudio.exe Studio



!ENTRY org.eclipse.ui 4 4 2008-08-24 17:43:44.060

!MESSAGE Unable to find Action Set: com.aptana.ide.server.ui.launchActionSet



!ENTRY org.eclipse.osgi 4 0 2008-08-24 17:43:45.059

!MESSAGE Application error

!STACK 1

org.eclipse.swt.SWTError: No more handles

	at org.eclipse.swt.SWT.error(SWT.java:3589)

	at org.eclipse.swt.SWT.error(SWT.java:3481)

	at org.eclipse.swt.SWT.error(SWT.java:3452)

	at org.eclipse.swt.graphics.Image.<init>(Image.java:724)

	at com.aptana.ide.editors.views.profiles.ProfilesView.fillEnvironmentTable(ProfilesView.java:1329)

	at com.aptana.ide.editors.views.profiles.ProfilesView.createPartControl(ProfilesView.java:1010)

	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)

	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)

	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)

	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)

	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)

	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)

	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)

	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)

	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)

	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)

	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)

	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)

	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)

	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)

	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)

	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)

	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2436)

	at org.eclipse.ui.internal.WorkbenchWindow$6.run(WorkbenchWindow.java:2616)

	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)

	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2597)

	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:658)

	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:811)

	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1453)

	at org.eclipse.ui.internal.Workbench.access$10(Workbench.java:1451)

	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1415)

	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)

	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1413)

	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)

	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:708)

	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)

	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)

	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)

	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)

	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:116)

	at com.aptana.ide.rcp.Application.run(Application.java:43)

	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)

	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)

	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)

	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)

	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)

	at java.lang.reflect.Method.invoke(Unknown Source)

	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)

	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)

	at org.eclipse.core.launcher.Main.run(Main.java:977)

	at org.eclipse.core.launcher.Main.main(Main.java:952)



!ENTRY org.eclipse.osgi 2 0 2008-08-24 17:43:45.091

!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:43:45.091

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.

```

---

### Post by unca.paka on 2008-08-24
Looks like theres a problem with a plugin not being able to load properly.
```
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:43:45.091

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.
```
Your best bet might be to check the Aptana forums. 
Never having used it myself, ive got no idea what the fix could be.

---

### Post by claymater on 2008-08-24
> **unca.paka said:**
> Looks like theres a problem with a plugin not being able to load properly.
```
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:

!SUBENTRY 1 org.eclipse.osgi 2 0 2008-08-24 17:43:45.091

!MESSAGE Bundle update@plugins/org.eclipse.swt.win32.win32.x86_3.2.2.v3236.jar [6] was not resolved.
```
Your best bet might be to check the Aptana forums. 
Never having used it myself, ive got no idea what the fix could be.

Ok thanks :)

---

