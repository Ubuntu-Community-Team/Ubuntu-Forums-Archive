---
title: "Texlipse and Eclipse help"
date: 2008-09-19
forum: General Help
---

### Post by Executor89 on 2008-09-19
I have Eclipse SDK 3.2.2 and am trying to use Texlipse 1.2 but am unable to edit the Texlipse config or actually use it. Here is the error that occurs when I try to configure the "build" for Texlipse.

Does anybody know how to fix this? I went on the web but could not find anything to fix this.

```
!ENTRY org.eclipse.jface 4 2 2008-09-19 14:54:34.931
!MESSAGE Problems occurred when invoking code from plug-in: "org.eclipse.jface".
!STACK 0
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IResource
	at net.sourceforge.texlipse.builder.BuilderRegistry.<init>(BuilderRegistry.java:164)
	at net.sourceforge.texlipse.builder.BuilderRegistry.<clinit>(BuilderRegistry.java:33)
	at net.sourceforge.texlipse.properties.BuilderSettingsPreferencePage.resolveTexDir(BuilderSettingsPreferencePage.java:74)
	at net.sourceforge.texlipse.properties.BuilderSettingsPreferencePage.<init>(BuilderSettingsPreferencePage.java:67)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at java.lang.Class.newInstance0(Class.java:355)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:157)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.ui.internal.WorkbenchPlugin$1.run(WorkbenchPlugin.java:242)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(WorkbenchPlugin.java:238)
	at org.eclipse.ui.internal.dialogs.WorkbenchPreferenceNode.createPage(WorkbenchPreferenceNode.java:46)
	at org.eclipse.jface.preference.PreferenceDialog.createPage(PreferenceDialog.java:1241)
	at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.createPage(FilteredPreferenceDialog.java:315)
	at org.eclipse.jface.preference.PreferenceDialog.showPage(PreferenceDialog.java:1134)
	at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.showPage(FilteredPreferenceDialog.java:438)
	at org.eclipse.jface.preference.PreferenceDialog$8.selectionChanged(PreferenceDialog.java:661)
	at org.eclipse.jface.viewers.StructuredViewer$3.run(StructuredViewer.java:839)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.core.runtime.Platform.run(Platform.java:858)
	at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:44)
	at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:149)
	at org.eclipse.jface.viewers.StructuredViewer.firePostSelectionChanged(StructuredViewer.java:837)
	at org.eclipse.jface.viewers.StructuredViewer.handlePostSelect(StructuredViewer.java:1143)
	at org.eclipse.jface.viewers.StructuredViewer$5.widgetSelected(StructuredViewer.java:1163)
	at org.eclipse.jface.util.OpenStrategy.firePostSelectionEvent(OpenStrategy.java:236)
	at org.eclipse.jface.util.OpenStrategy.access$4(OpenStrategy.java:230)
	at org.eclipse.jface.util.OpenStrategy$1$2.run(OpenStrategy.java:404)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)

```

---

### Post by stringkarma on 2009-03-29
Have you made any progress on this?

I am having a similar issue

---

### Post by santiasnquino on 2009-05-04
there is no future, I have the same problem.


!SESSION 2009-05-04 17:30:33.175 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_10
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=es_CL
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2009-05-04 17:30:36.126
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-04 17:30:36.126
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-04 17:30:36.126
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-05-04 17:30:36.126
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.jface 4 2 2009-05-04 17:30:58.165
!MESSAGE Se han producido problemas al invocar el código del plug-in: "org.eclipse.jface".
!STACK 0
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IResource
    at net.sourceforge.texlipse.builder.BuilderRegistry.<init>(BuilderRegistry.java:164)
    at net.sourceforge.texlipse.builder.BuilderRegistry.<clinit>(BuilderRegistry.java:33)
    at net.sourceforge.texlipse.properties.BuilderSettingsPreferencePage.resolveTexDir(BuilderSettingsPreferencePage.java:74)
    at net.sourceforge.texlipse.properties.BuilderSettingsPreferencePage.<init>(BuilderSettingsPreferencePage.java:67)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
    at java.lang.Class.newInstance0(Class.java:355)
    at java.lang.Class.newInstance(Class.java:308)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:157)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.ui.internal.WorkbenchPlugin$1.run(WorkbenchPlugin.java:242)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
    at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(WorkbenchPlugin.java:238)
    at org.eclipse.ui.internal.dialogs.WorkbenchPreferenceNode.createPage(WorkbenchPreferenceNode.java:46)
    at org.eclipse.jface.preference.PreferenceDialog.createPage(PreferenceDialog.java:1241)
    at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.createPage(FilteredPreferenceDialog.java:315)
    at org.eclipse.jface.preference.PreferenceDialog.showPage(PreferenceDialog.java:1134)
    at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.showPage(FilteredPreferenceDialog.java:438)
    at org.eclipse.jface.preference.PreferenceDialog$8.selectionChanged(PreferenceDialog.java:661)
    at org.eclipse.jface.viewers.StructuredViewer$3.run(StructuredViewer.java:839)
    at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
    at org.eclipse.core.runtime.Platform.run(Platform.java:858)
    at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:44)
    at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:149)
    at org.eclipse.jface.viewers.StructuredViewer.firePostSelectionChanged(StructuredViewer.java:837)
    at org.eclipse.jface.viewers.StructuredViewer.handlePostSelect(StructuredViewer.java:1143)
    at org.eclipse.jface.viewers.StructuredViewer$5.widgetSelected(StructuredViewer.java:1163)
    at org.eclipse.jface.util.OpenStrategy.firePostSelectionEvent(OpenStrategy.java:236)
    at org.eclipse.jface.util.OpenStrategy.access$4(OpenStrategy.java:230)
    at org.eclipse.jface.util.OpenStrategy$1$2.run(OpenStrategy.java:404)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
    at org.eclipse.jface.window.Window.runEventLoop(Window.java:820)
    at org.eclipse.jface.window.Window.open(Window.java:796)
    at org.eclipse.ui.internal.OpenPreferencesAction.run(OpenPreferencesAction.java:65)
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
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IResource
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 67 more

---

### Post by macabro22 on 2009-07-22
I switched to using gedit with the latex plugin! It works marvelously

---

