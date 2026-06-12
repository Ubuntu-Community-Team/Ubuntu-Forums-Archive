---
title: "RSSOwl installs but doesn't display content in Hardy"
date: 2008-10-15
forum: General Help
---

### Post by ArchVile on 2008-10-15
the title pretty much says everything. RSSOwl 2.0/8a starts, but the right pane remains empty, whatever i do. installed the contents of the standard linux package in /usr/lib/rssowl and s-linked it to /usr/bin/RSSOwl

there is a flashing error message when closing the prog, but it disappears too quickly. no error messages on the console, .log for one session is attached.

i assume there is just some lib missing, but *which*? libswt* is all installed. what is "swt-mozilla-gtk"???

is there anyone running RSSOwl successfully under hardy?

thanks in adv.!


-------

```
!SESSION 2009-10-15 11:37:02.743 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.ui 4 0 2008-10-15 11:39:10.647
!MESSAGE Unhandled event loop exception
!STACK 0
org.eclipse.swt.SWTError: No more handles (java.lang.UnsatisfiedLinkError: no swt-mozilla-gtk-3349 or swt-mozilla-gtk in swt.library.path, java.library.path or the jar file)
	at org.eclipse.swt.SWT.error(SWT.java:3589)
	at org.eclipse.swt.SWT.error(SWT.java:3481)
	at org.eclipse.swt.browser.Mozilla.create(Mozilla.java:323)
	at org.eclipse.swt.browser.Browser.<init>(Browser.java:109)
	at org.rssowl.ui.internal.CBrowser.createBrowser(CBrowser.java:118)
	at org.rssowl.ui.internal.CBrowser.<init>(CBrowser.java:82)
	at org.rssowl.ui.internal.editors.feed.NewsBrowserViewer.<init>(NewsBrowserViewer.java:97)
	at org.rssowl.ui.internal.editors.feed.NewsBrowserControl.createViewer(NewsBrowserControl.java:88)
	at org.rssowl.ui.internal.editors.feed.FeedView.createPartControl(FeedView.java:1401)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:661)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:426)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:592)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:299)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:179)
	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)
	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:400)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1256)
	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1209)
	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1604)
	at org.eclipse.ui.internal.PartStack.add(PartStack.java:499)
	at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:103)
	at org.eclipse.ui.internal.PartStack.add(PartStack.java:485)
	at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:112)
	at org.eclipse.ui.internal.EditorSashContainer.addEditor(EditorSashContainer.java:63)
	at org.eclipse.ui.internal.EditorAreaHelper.addToLayout(EditorAreaHelper.java:217)
	at org.eclipse.ui.internal.EditorAreaHelper.addEditor(EditorAreaHelper.java:207)
	at org.eclipse.ui.internal.EditorManager.createEditorTab(EditorManager.java:774)
	at org.eclipse.ui.internal.EditorManager.openEditorFromDescriptor(EditorManager.java:673)
	at org.eclipse.ui.internal.EditorManager.openEditor(EditorManager.java:634)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2737)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2651)
	at org.eclipse.ui.internal.WorkbenchPage.access$13(WorkbenchPage.java:2643)
	at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2595)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2590)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2574)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2565)
	at org.rssowl.ui.internal.OwlUI.openInFeedView(OwlUI.java:1084)
	at org.rssowl.ui.internal.views.explorer.BookMarkExplorer$4.open(BookMarkExplorer.java:343)
	at org.rssowl.ui.internal.views.explorer.BookMarkViewer$3.run(BookMarkViewer.java:185)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.core.runtime.Platform.run(Platform.java:857)
	at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:46)
	at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:199)
	at org.rssowl.ui.internal.views.explorer.BookMarkViewer.internalFireOpen(BookMarkViewer.java:183)
	at org.rssowl.ui.internal.views.explorer.BookMarkViewer.internalHandleOpen(BookMarkViewer.java:175)
	at org.rssowl.ui.internal.views.explorer.BookMarkViewer.access$1(BookMarkViewer.java:171)
	at org.rssowl.ui.internal.views.explorer.BookMarkViewer$2.handleOpen(BookMarkViewer.java:156)
	at org.rssowl.ui.internal.util.ViewerOpenStrategy.fireOpenEvent(ViewerOpenStrategy.java:147)
	at org.rssowl.ui.internal.util.ViewerOpenStrategy.mouseSelectItem(ViewerOpenStrategy.java:286)
	at org.rssowl.ui.internal.util.ViewerOpenStrategy.handleEvent(ViewerOpenStrategy.java:238)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3319)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2971)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2389)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2353)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2219)
	at org.eclipse.ui.internal.Workbench$4.run(Workbench.java:466)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:289)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:461)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.rssowl.ui.internal.Application.start(Application.java:110)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1173)
Caused by: java.lang.UnsatisfiedLinkError: no swt-mozilla-gtk-3349 or swt-mozilla-gtk in swt.library.path, java.library.path or the jar file
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:219)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
	at org.eclipse.swt.browser.Mozilla.create(Mozilla.java:308)
	... 73 more

!ENTRY org.eclipse.ui.workbench 4 0 2008-10-15 11:39:12.010
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:169)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:116)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1125)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1106)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:970)
	at org.eclipse.swt.widgets.Control.release(Control.java:2984)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1098)


	at org.eclipse.swt.widgets.Widget.release(Widget.java:973)
	at org.eclipse.swt.widgets.Control.release(Control.java:2984)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1098)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:973)
	at org.eclipse.swt.widgets.Control.release(Control.java:2984)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1098)
	at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:162)
	at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:465)
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1704)
	at org.eclipse.swt.widgets.Widget.release(Widget.java:973)
	at org.eclipse.swt.widgets.Control.release(Control.java:2984)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:434)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1649)
	at org.eclipse.jface.window.Window.close(Window.java:330)
	at org.eclipse.jface.window.ApplicationWindow.close(ApplicationWindow.java:306)
	at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1600)
	at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:699)
	at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:675)
	at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:790)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:788)
	at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
	at org.eclipse.ui.internal.Workbench$15.run(Workbench.java:908)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:905)
	at org.eclipse.ui.internal.Workbench.access$15(Workbench.java:834)
	at org.eclipse.ui.internal.Workbench$22.run(Workbench.java:1078)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.Workbench.close(Workbench.java:1076)
	at org.eclipse.ui.internal.Workbench.close(Workbench.java:1048)
	at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:696)
	at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:675)
	at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:790)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:788)
	at org.eclipse.jface.window.Window.handleShellCloseEvent(Window.java:736)
	at org.eclipse.jface.window.Window$3.shellClosed(Window.java:682)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:91)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1125)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1110)
	at org.eclipse.swt.widgets.Shell.closeWidget(Shell.java:542)
	at org.eclipse.swt.widgets.Shell.gtk_delete_event(Shell.java:922)
	at org.eclipse.swt.widgets.Widget.windowProc(Widget.java:1478)
	at org.eclipse.swt.widgets.Control.windowProc(Control.java:4234)
	at org.eclipse.swt.widgets.Display.windowProc(Display.java:3973)
	at org.eclipse.swt.internal.gtk.OS._gtk_main_do_event(Native Method)
	at org.eclipse.swt.internal.gtk.OS.gtk_main_do_event(OS.java:5593)
	at org.eclipse.swt.widgets.Display.eventProc(Display.java:1192)
	at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
	at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(OS.java:1487)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2969)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2389)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2353)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2219)
	at org.eclipse.ui.internal.Workbench$4.run(Workbench.java:466)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:289)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:461)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.rssowl.ui.internal.Application.start(Application.java:110)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1173)

!ENTRY org.eclipse.ui.workbench 4 2 2008-10-15 11:39:12.059
!MESSAGE Problems occurred when invoking code from plug-in: "org.eclipse.ui.workbench".
!STACK 0
java.lang.NullPointerException
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:179)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.setVisible(TabbedStackPresentation.java:314)
	at org.eclipse.ui.internal.PartStack.setVisible(PartStack.java:1058)
	at org.eclipse.ui.internal.PartSashContainer.remove(PartSashContainer.java:735)
	at org.eclipse.ui.internal.EditorSashContainer.removeEditor(EditorSashContainer.java:295)
	at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:84)
	at org.eclipse.ui.internal.EditorAreaHelper.closeEditor(EditorAreaHelper.java:62)
	at org.eclipse.ui.internal.WorkbenchPage.closeEditors(WorkbenchPage.java:1307)
	at org.eclipse.ui.internal.WorkbenchPage.closeAllEditors(WorkbenchPage.java:1131)
	at org.eclipse.ui.internal.WorkbenchPage.dispose(WorkbenchPage.java:1653)
	at org.eclipse.ui.internal.WorkbenchWindow.closeAllPages(WorkbenchWindow.java:825)
	at org.eclipse.ui.internal.WorkbenchWindow.hardClose(WorkbenchWindow.java:1559)
	at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:699)
	at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:675)
	at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:790)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:788)
	at org.eclipse.jface.window.WindowManager.close(WindowManager.java:109)
	at org.eclipse.ui.internal.Workbench$15.run(Workbench.java:908)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.ui.internal.Workbench.busyClose(Workbench.java:905)
	at org.eclipse.ui.internal.Workbench.access$15(Workbench.java:834)
	at org.eclipse.ui.internal.Workbench$22.run(Workbench.java:1078)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.Workbench.close(Workbench.java:1076)
	at org.eclipse.ui.internal.Workbench.close(Workbench.java:1048)
	at org.eclipse.ui.internal.WorkbenchWindow.busyClose(WorkbenchWindow.java:696)
	at org.eclipse.ui.internal.WorkbenchWindow.access$0(WorkbenchWindow.java:675)
	at org.eclipse.ui.internal.WorkbenchWindow$2.run(WorkbenchWindow.java:790)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchWindow.close(WorkbenchWindow.java:788)
	at org.eclipse.jface.window.Window.handleShellCloseEvent(Window.java:736)
	at org.eclipse.jface.window.Window$3.shellClosed(Window.java:682)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:91)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1125)

	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1110)
	at org.eclipse.swt.widgets.Shell.closeWidget(Shell.java:542)
	at org.eclipse.swt.widgets.Shell.gtk_delete_event(Shell.java:922)
	at org.eclipse.swt.widgets.Widget.windowProc(Widget.java:1478)
	at org.eclipse.swt.widgets.Control.windowProc(Control.java:4234)
	at org.eclipse.swt.widgets.Display.windowProc(Display.java:3973)
	at org.eclipse.swt.internal.gtk.OS._gtk_main_do_event(Native Method)
	at org.eclipse.swt.internal.gtk.OS.gtk_main_do_event(OS.java:5593)
	at org.eclipse.swt.widgets.Display.eventProc(Display.java:1192)
	at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
	at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(OS.java:1487)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2969)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2389)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2353)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2219)
	at org.eclipse.ui.internal.Workbench$4.run(Workbench.java:466)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:289)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:461)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.rssowl.ui.internal.Application.start(Application.java:110)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1173)
```

---

### Post by der-eremit on 2008-10-27
Hi,

sudo apt-get install xul-runner

and the pain will be gone ;)

regards

---

