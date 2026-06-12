---
title: "[SOLVED] PHPEclipse throwing errors on opening PHP files"
date: 2008-09-06
forum: General Help
---

### Post by Pitt Stains on 2008-09-06
Hello,

I am running Ubuntu 8.10 on a 64-bit system, with sun-java6-bin, sun-java6-jre (and a number of other packages with java in the name), and Eclipse SDK 3.2.2, all from the repositories.

Eclipse per se seems to be working fine.  I installed the PHPeclipse plug-in via the Software Updates, from this URL: [http://phpeclipse.sourceforge.net/update/stable/1.1.x/](http://phpeclipse.sourceforge.net/update/stable/1.1.x/).  When I try to open a PHP file, I get a blank PHP Editor in my main window, and an error message approximating the following in ~/workspace/.metadata/.log:

```
!ENTRY org.eclipse.ui 4 0 2008-09-06 13:23:06.725
!MESSAGE java.lang.NullPointerException
!STACK 0
java.lang.NullPointerException
   at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)
   at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.setVisible(TabbedStackPresentation.java:308)
   at org.eclipse.ui.internal.PartStack.setVisible(PartStack.java:989)
   at org.eclipse.ui.internal.PartSashContainer.remove(PartSashContainer.java:733)
   at org.eclipse.ui.internal.EditorSashContainer.removeEditor(EditorSashContainer.java:217)
   at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:84)
   at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:62)
   at org.eclipse.ui.internal.WorkbenchPage.closeEditors(WorkbenchPage.java:1264)
   at org.eclipse.ui.internal.WorkbenchPage.closeEditor(WorkbenchPage.java:1324)
   at org.eclipse.ui.internal.EditorPane.doHide(EditorPane.java:54)
   at org.eclipse.ui.internal.PartStack.close(PartStack.java:499)
   at org.eclipse.ui.internal.EditorStack.close(EditorStack.java:205)
   at org.eclipse.ui.internal.PartStack$1.close(PartStack.java:106)
   at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation$1.handleEvent(TabbedStackPresentation.java:81)
   at org.eclipse.ui.internal.presentations.util.AbstractTabFolder.fireEvent(AbstractTabFolder.java:267)
   at org.eclipse.ui.internal.presentations.util.AbstractTabFolder.fireEvent(AbstractTabFolder.java:276)
   at org.eclipse.ui.internal.presentations.defaultpresentation.DefaultTabFolder.access$1(DefaultTabFolder.java:1)
   at org.eclipse.ui.internal.presentations.defaultpresentation.DefaultTabFolder$1.closeButtonPressed(DefaultTabFolder.java:67)
   at org.eclipse.ui.internal.presentations.PaneFolder.notifyCloseListeners(PaneFolder.java:580)
   at org.eclipse.ui.internal.presentations.PaneFolder$3.close(PaneFolder.java:187)
   at org.eclipse.swt.custom.CTabFolder.onMouse(CTabFolder.java:2107)
   at org.eclipse.swt.custom.CTabFolder$1.handleEvent(CTabFolder.java:292)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

Can anyone shed some light on the matter?

Thanks,
-Pitt

---

### Post by Pitt Stains on 2008-09-06
I cleared out the log, then opened Eclipse, then tried to open a PHP file using the PHP Editor (I can open them with the text editor, but that doesn't provide me with much of an IDE), then closed Eclipse.  Here is the resulting log, in case that provides any additional detail:

```
!SESSION 2008-09-06 13:50:18.935 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2008-09-06 13:50:22.081
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-06 13:50:22.082
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-06 13:50:22.082
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-09-06 13:50:22.082
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.ui 4 4 2008-09-06 13:50:40.527
!MESSAGE Unhandled event loop exception

!ENTRY org.eclipse.ui 4 0 2008-09-06 13:50:40.527
!MESSAGE net.sourceforge.phpeclipse.phpeditor.PHPEditor
!STACK 0
java.lang.NoClassDefFoundError: net.sourceforge.phpeclipse.phpeditor.PHPEditor
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:157)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(WorkbenchPlugin.java:234)
   at org.eclipse.ui.internal.registry.EditorDescriptor.createEditor(EditorDescriptor.java:231)
   at org.eclipse.ui.internal.EditorManager.createPart(EditorManager.java:911)
   at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:549)
   at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:372)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)
   at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)
   at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)
   at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
   at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:394)
   at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)
   at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)
   at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)
   at org.eclipse.ui.internal.PartStack.add(PartStack.java:455)
   at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:102)
   at org.eclipse.ui.internal.PartStack.add(PartStack.java:441)
   at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:111)
   at org.eclipse.ui.internal.EditorSashContainer.addEditor(EditorSashContainer.java:60)
   at org.eclipse.ui.internal.EditorAreaHelper.addToLayout(EditorAreaHelper.java:217)
   at org.eclipse.ui.internal.EditorAreaHelper.addEditor(EditorAreaHelper.java:207)
   at org.eclipse.ui.internal.EditorManager.createEditorTab(EditorManager.java:822)
   at org.eclipse.ui.internal.EditorManager.openEditorFromDescriptor(EditorManager.java:721)
   at org.eclipse.ui.internal.EditorManager.openEditor(EditorManager.java:682)
   at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2593)
   at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2528)
   at org.eclipse.ui.internal.WorkbenchPage.access$10(WorkbenchPage.java:2520)
   at org.eclipse.ui.internal.WorkbenchPage$9.run(WorkbenchPage.java:2505)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2500)
   at org.eclipse.ui.actions.OpenWithMenu.openEditor(OpenWithMenu.java:288)
   at org.eclipse.ui.actions.OpenWithMenu.access$0(OpenWithMenu.java:280)
   at org.eclipse.ui.actions.OpenWithMenu$2.handleEvent(OpenWithMenu.java:184)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.ide.FileStoreEditorInput
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...58 more

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-06 13:50:46.508
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
   at org.eclipse.jface.window.Window.close(Window.java:330)
   at org.eclipse.jface.window.ApplicationWindow.close(ApplicationWindow.java:299)
   at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1510)
   at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:622)
   at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:598)
   at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:713)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:711)
   at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
   at org.eclipse.ui.internal.Workbench$12.run(Workbench.java:715)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:712)
   at org.eclipse.ui.internal.Workbench.access$8(Workbench.java:642)
   at org.eclipse.ui.internal.Workbench$14.run(Workbench.java:855)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:853)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:828)
   at org.eclipse.ui.internal.QuitAction.run(QuitAction.java:57)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-06 13:50:46.511
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
   at org.eclipse.jface.window.Window.close(Window.java:330)
   at org.eclipse.jface.window.ApplicationWindow.close(ApplicationWindow.java:299)
   at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1510)
   at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:622)
   at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:598)
   at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:713)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:711)
   at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
   at org.eclipse.ui.internal.Workbench$12.run(Workbench.java:715)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:712)
   at org.eclipse.ui.internal.Workbench.access$8(Workbench.java:642)
   at org.eclipse.ui.internal.Workbench$14.run(Workbench.java:855)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:853)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:828)
   at org.eclipse.ui.internal.QuitAction.run(QuitAction.java:57)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.ui.workbench 4 0 2008-09-06 13:50:46.514
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
   at org.eclipse.jface.window.Window.close(Window.java:330)
   at org.eclipse.jface.window.ApplicationWindow.close(ApplicationWindow.java:299)
   at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1510)
   at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:622)
   at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:598)
   at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:713)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:711)
   at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
   at org.eclipse.ui.internal.Workbench$12.run(Workbench.java:715)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:712)
   at org.eclipse.ui.internal.Workbench.access$8(Workbench.java:642)
   at org.eclipse.ui.internal.Workbench$14.run(Workbench.java:855)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:853)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:828)
   at org.eclipse.ui.internal.QuitAction.run(QuitAction.java:57)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.ui.workbench 4 2 2008-09-06 13:50:46.547
!MESSAGE Problems occurred when invoking code from plug-in: "org.eclipse.ui.workbench".
!STACK 0
java.lang.NullPointerException
   at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)
   at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.setVisible(TabbedStackPresentation.java:308)
   at org.eclipse.ui.internal.PartStack.setVisible(PartStack.java:989)
   at org.eclipse.ui.internal.PartSashContainer.remove(PartSashContainer.java:733)
   at org.eclipse.ui.internal.EditorSashContainer.removeEditor(EditorSashContainer.java:217)
   at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:84)
   at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:62)
   at org.eclipse.ui.internal.WorkbenchPage.closeEditors(WorkbenchPage.java:1264)
   at org.eclipse.ui.internal.WorkbenchPage.closeAllEditors(WorkbenchPage.java:1088)
   at org.eclipse.ui.internal.WorkbenchPage.dispose(WorkbenchPage.java:1597)
   at org.eclipse.ui.internal.WorkbenchWindow.closeAllPages(WorkbenchWindow.java:748)
   at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1486)
   at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:622)
   at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:598)
   at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:713)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:711)
   at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
   at org.eclipse.ui.internal.Workbench$12.run(Workbench.java:715)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:712)
   at org.eclipse.ui.internal.Workbench.access$8(Workbench.java:642)
   at org.eclipse.ui.internal.Workbench$14.run(Workbench.java:855)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:853)
   at org.eclipse.ui.internal.Workbench.close(Workbench.java:828)
   at org.eclipse.ui.internal.QuitAction.run(QuitAction.java:57)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

---

### Post by Pitt Stains on 2008-09-15
bump

---

### Post by matthewboh on 2008-09-22
I'm having the exact same problem with 8.04 on a 32-bit system.  I have also updated the java_home file in /etc/eclipse to include the link to the Java 6 JDK before the Gnu version.

Any ideas?

---

### Post by pawelfx1 on 2008-09-22
I had the same problem.
I FiX this problem like this:
1.Uninstall all old Eclipse packages.
2.Install Ganymede Packages (based on Eclipse 3.4) link to 32bit version for linux: [http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/ganymede/R/eclipse-java-ganymede-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/ganymede/R/eclipse-java-ganymede-linux-gtk.tar.gz)
3.Install PHPEclipse plugin 1.2.x with this instruction: [http://www.phpeclipse.de/wiki/Installation](http://www.phpeclipse.de/wiki/Installation)

"Install" - its mean extract archive -thats all.
This will extract:
sudo tar -vxzf eclipse-java-ganymede-linux-gtk.tar.gz /usr/lib/

This will create link: sudo ln -s /usr/lib/eclipse/eclipse /usr/bin

For polish people:
I gitara gra :) :guitar:

---

### Post by Pitt Stains on 2008-09-27
Thanks for your reply, but this didn't solve my problem.  I extracted the tar such that all the files are in /usr/lib/eclipse.  I also created the symlink, but when I start eclipse I get a failure and am pointed to a log file which is about 2,000 lines long.  This is on my first startup -- before I try to install any plugins.

It makes me wonder if there is some Java compatibility issue.  I think the important stuff is at the beginning of the log.  Here's the beginning:

```
!SESSION 2008-09-27 23:01:22.052 -----------------------------------------------
eclipse.buildId=I20080617-2000
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.core.runtime.compatibility 4 0 2008-09-27 23:02:24.928
!MESSAGE 
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.plugins.CompatibilityActivator.stop() of bundle org.eclipse.core.runtime.compatibility.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1066)
   at org.eclipse.osgi.framework.internal.core.BundleHost.stopWorker(BundleHost.java:457)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.suspend(AbstractBundle.java:531)
   at org.eclipse.osgi.framework.internal.core.Framework.suspendBundle(Framework.java:1104)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.suspendBundle(PackageAdminImpl.java:280)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.processDelta(PackageAdminImpl.java:415)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.doResolveBundles(PackageAdminImpl.java:223)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl$1.run(PackageAdminImpl.java:162)
   at java.lang.Thread.run(libgcj.so.81)
Caused by: java.lang.IllegalStateException
   at org.eclipse.core.internal.runtime.CompatibilityHelper.getPluginDescriptor(CompatibilityHelper.java:59)
   at org.eclipse.core.internal.plugins.CompatibilityActivator.stop(CompatibilityActivator.java:28)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1050)
   at java.security.AccessController.doPrivileged(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1046)
   ...8 more
Root exception:
java.lang.IllegalStateException
   at org.eclipse.core.internal.runtime.CompatibilityHelper.getPluginDescriptor(CompatibilityHelper.java:59)
   at org.eclipse.core.internal.plugins.CompatibilityActivator.stop(CompatibilityActivator.java:28)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1050)
   at java.security.AccessController.doPrivileged(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1046)
   at org.eclipse.osgi.framework.internal.core.BundleHost.stopWorker(BundleHost.java:457)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.suspend(AbstractBundle.java:531)
   at org.eclipse.osgi.framework.internal.core.Framework.suspendBundle(Framework.java:1104)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.suspendBundle(PackageAdminImpl.java:280)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.processDelta(PackageAdminImpl.java:415)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.doResolveBundles(PackageAdminImpl.java:223)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl$1.run(PackageAdminImpl.java:162)
   at java.lang.Thread.run(libgcj.so.81)

!ENTRY org.eclipse.equinox.p2.reconciler.dropins 4 0 2008-09-27 23:02:29.933
!MESSAGE 
!STACK 0
org.osgi.framework.BundleException: State change in progress for bundle "reference:file:plugins/org.eclipse.equinox.p2.reconciler.dropins_1.0.0.v20080611.jar" by thread "Start Level Event Dispatcher".
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.beginStateChange(AbstractBundle.java:1144)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.suspend(AbstractBundle.java:529)
   at org.eclipse.osgi.framework.internal.core.Framework.suspendBundle(Framework.java:1104)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.suspendBundle(PackageAdminImpl.java:280)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.processDelta(PackageAdminImpl.java:415)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.doResolveBundles(PackageAdminImpl.java:223)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl$1.run(PackageAdminImpl.java:162)
   at java.lang.Thread.run(libgcj.so.81)
Caused by: org.eclipse.osgi.framework.internal.core.AbstractBundle$BundleStatusException
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.beginStateChange(AbstractBundle.java:1144)
   ...7 more
Root exception:
org.eclipse.osgi.framework.internal.core.AbstractBundle$BundleStatusException
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.beginStateChange(AbstractBundle.java:1144)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.suspend(AbstractBundle.java:529)
   at org.eclipse.osgi.framework.internal.core.Framework.suspendBundle(Framework.java:1104)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.suspendBundle(PackageAdminImpl.java:280)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.processDelta(PackageAdminImpl.java:415)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.doResolveBundles(PackageAdminImpl.java:223)
   at org.eclipse.osgi.framework.internal.core.PackageAdminImpl$1.run(PackageAdminImpl.java:162)
   at java.lang.Thread.run(libgcj.so.81)

!ENTRY org.eclipse.osgi 4 0 2008-09-27 23:02:30.290
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry. The applications available are: org.eclipse.equinox.app.error, org.eclipse.equinox.p2.artifact.repository.mirrorApplication, org.eclipse.equinox.p2.director.app.application, org.eclipse.equinox.p2.metadata.generator.EclipseGenerator, org.eclipse.equinox.p2.metadata.repository.mirrorApplication, org.eclipse.equinox.p2.reconciler.application.
   at org.eclipse.equinox.internal.app.EclipseAppHandle.getConfiguration(EclipseAppHandle.java:301)
   at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:188)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:382)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1236)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1212)

```

If you need more log, just let me know... Thanks!

---

### Post by Pitt Stains on 2008-11-26
Well, I rebuilt this machine and installed Ubuntu 8.10.  I went for the Eclipse version from the website (Ganymede) and went with PDT instead of PHPEclipse.  I think I read somewhere that PHPEclipse is either no longer maintained or that the PDT project was kind of overtaking it.

---

### Post by ngothean on 2008-12-03
I have exactly the same problem with Ubuntu 8.04 
I installed it using CD ISO 
I followed literally word by word [https://help.ubuntu.com/community/PHPEclipse](https://help.ubuntu.com/community/PHPEclipse)

Reintsall would be a nightmare for me.
 
Despite that I have high speed internet, when I let the package manager handle the download and install, it took me 12 hours just to download (This does not happen when I download directly, just about 5 minutes).

---

### Post by pawelfx1 on 2008-12-05
Little correcting: Pitt Stains of course you are trying install 64bit version Eclipse. In my previous post link was to 32 bit version. 64 bit version: eclipse-SDK-3.4.1-linux-gtk-x86_64.tar.gz.

I greet ):P

---

