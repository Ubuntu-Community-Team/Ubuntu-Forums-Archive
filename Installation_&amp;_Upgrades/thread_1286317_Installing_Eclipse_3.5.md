---
title: "Installing Eclipse 3.5"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by LeonBlade on 2009-10-08
Hey everyone,

I'm trying to install Eclipse 3.5 Galileo on my Ubuntu 9.04 machine.

```
apt-get install eclipse
```

Gives me an older version of it that isn't up to date.
I've tried to download the archived file and put it in /opt or whatever but none of that is working out for me.

Is there a way I can use apt-get to install the 3.5 or upgrade the old version that apt-get gives me?

Thanks,
LeonBlade

---

### Post by Drood on 2009-10-09
Ubuntu 9.10 installs eclipse 3.5, and if you dont feel like getting 9.10, look on google for a eclipse 3.5 .deb package for ubuntu, I found it once but I don't remember exactly where.

---

### Post by dominiquec on 2009-10-09
I install the latest version of Eclipse downloaded directly from the Eclipse web site.  Works fairly well.  Just make sure you set the JAVA_HOME environment properly.  Will write a short how-to on it soon.

---

### Post by LeonBlade on 2009-10-09
Wow, how stupid of me for not even thinking to look for a Debian package for it #-o

Thanks for the reply, I found what I was looking for.
If anyone else has this problem too (but hopefully you aren't as dumb as I am) here is where I found it:

[http://blog.yogarine.com/2009/08/eclipse-35-galileo-packages-for-ubuntu.html](http://blog.yogarine.com/2009/08/eclipse-35-galileo-packages-for-ubuntu.html)

The whole time I was searching things like "ubuntu 9.04 eclipse 3.5" and got nothing, never thought to check for an package. 

Thanks again.

---

### Post by nabendt on 2009-10-09
Please be careful in the moment with upgrading to 9.10, just for running eclipse 3.5. I did and it is causing me some problems in the moment. It seems to be a problem with gtk, but I am not enough into this, only know that I am not able to install eclipse plugins or using subclipse at all.

Cheers.

---

### Post by LeonBlade on 2009-10-09
Okay... well there are loads of problems with that install...
I don't know why I keep getting crap with it.

```

An error has occurred. See error log for more details.
java.lang.NullPointerException

```
```

eclipse.buildId=I20090611-1540
java.version=1.6.0_16
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  -product org.eclipse.epp.package.java.product
Command-line arguments:  -os linux -ws gtk -arch x86 -product org.eclipse.epp.package.java.product


Error
Fri Oct 09 04:00:51 EDT 2009
The URL "bundleentry://212.fwk4354460/icons/elcl16/restore_log.gif" could not be extracted probably due to insufficient permissions or insufficient disk space.

java.io.IOException: The URL "bundleentry://212.fwk4354460/icons/elcl16/restore_log.gif" could not be extracted probably due to insufficient permissions or insufficient disk space.
	at org.eclipse.core.runtime.internal.adaptor.URLConverterImpl.toFileURL(URLConverterImpl.java:40)
	at org.eclipse.core.runtime.FileLocator.toFileURL(FileLocator.java:206)
	at org.eclipse.jface.resource.URLImageDescriptor.getFilePath(URLImageDescriptor.java:137)
	at org.eclipse.jface.resource.URLImageDescriptor.createImage(URLImageDescriptor.java:157)
	at org.eclipse.jface.resource.ImageDescriptor.createResource(ImageDescriptor.java:165)
	at org.eclipse.jface.resource.DeviceResourceManager.allocate(DeviceResourceManager.java:56)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:88)
	at org.eclipse.jface.resource.LocalResourceManager.allocate(LocalResourceManager.java:82)
	at org.eclipse.jface.resource.AbstractResourceManager.create(AbstractResourceManager.java:88)
	at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(ResourceManager.java:192)
	at org.eclipse.jface.action.ActionContributionItem.updateImages(ActionContributionItem.java:1046)
	at org.eclipse.jface.action.ActionContributionItem.update(ActionContributionItem.java:783)
	at org.eclipse.jface.action.ActionContributionItem.fill(ActionContributionItem.java:342)
	at org.eclipse.jface.action.ToolBarManager.update(ToolBarManager.java:353)
	at org.eclipse.ui.internal.ViewPane.updateActionBars(ViewPane.java:447)
	at org.eclipse.ui.internal.ViewActionBars.updateActionBars(ViewActionBars.java:59)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:414)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:226)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.Perspective.showView(Perspective.java:2228)
	at org.eclipse.ui.internal.WorkbenchPage.busyShowView(WorkbenchPage.java:1067)
	at org.eclipse.ui.internal.WorkbenchPage$20.run(WorkbenchPage.java:3816)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3813)
	at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3789)
	at org.eclipse.ui.statushandlers.WorkbenchStatusDialogManager$7.widgetSelected(WorkbenchStatusDialogManager.java:1507)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:228)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1176)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1200)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1185)
	at org.eclipse.swt.widgets.Link.gtk_button_release_event(Link.java:340)
	at org.eclipse.swt.widgets.Widget.windowProc(Widget.java:1559)
	at org.eclipse.swt.widgets.Control.windowProc(Control.java:4586)
	at org.eclipse.swt.widgets.Display.windowProc(Display.java:4191)
	at org.eclipse.swt.internal.gtk.OS._gtk_main_do_event(Native Method)
	at org.eclipse.swt.internal.gtk.OS.gtk_main_do_event(OS.java:7586)
	at org.eclipse.swt.widgets.Display.eventProc(Display.java:1185)
	at org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(Native Method)
	at org.eclipse.swt.internal.gtk.OS.g_main_context_iteration(OS.java:1858)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3110)
	at org.eclipse.jface.window.Window.runEventLoop(Window.java:825)
	at org.eclipse.jface.window.Window.open(Window.java:801)
	at org.eclipse.ui.actions.NewProjectAction.run(NewProjectAction.java:117)
	at org.eclipse.jface.action.Action.runWithEvent(Action.java:498)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
	at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1176)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3493)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3112)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2405)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2369)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2221)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:500)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:493)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)


```

---

### Post by Mighty_Joe on 2009-10-09
```
The URL "bundleentry://212.fwk4354460/icons/elcl16/restore_log.gif" could not be extracted probably due to insufficient permissions or insufficient disk space.

```

Well, it sounds like either you are out of disk space or your user doesn't have permission to access the resource bundle restore_log.gif is in.

---

### Post by LeonBlade on 2009-10-09
Oh wow... haha... why didn't I read that...
It was early in the morning and I wasn't thinking enough I guess lol.

Well, I installed Ubuntu Inside of Windows for whatever reason (normally I never do that) and now it seems I've ran out of space (must of not given myself a lot of room).

Do you know where I can go to figure out how to transfer all my files onto another partition so I can boot with GRUB instead of the crappy Windows boot manager and then actually have a physical partition of both my Windows and Ubuntu OS?

EDIT: Would it be a logical idea to just copy the entire root of my Ubuntu OS onto a backup hard drive and then install Ubuntu and copy all the files over... while writing that I realized it doesn't really sound very practical.
I saw tools like LVPM that should do the job for me, but that may take a while.
If all else fails, I might just reinstall Ubuntu on a new partition... but then again... I don't want to lose all the packages and things I installed.

---

### Post by LeonBlade on 2009-10-11
Okay... now this is just odd...

I've removed eclipse from Ubuntu and I went to go install it again.
So if I run eclipse from the terminal, I get this:

```
The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
```

So I try running **sudo apt-get install eclipse** to install it again, and I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
eclipse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Uhh... what?
Can someone explain what in the world is going on here?

---

### Post by MelDJ on 2009-10-11
try finding it in synaptic and mark it for complete removal

---

### Post by LeonBlade on 2009-10-11
Thank you so much everyone for helping me out with this one.

EDIT: I'm also having some issues with permissions.
I added Eclipse to my Programming menu, and I instead have to run it with **sudo eclipse** to prevent permission errors.

Everything is installed and ready to go, the only problem is with Flex now (of course).  

I installed Flex Builder into Eclipse and I'm getting this error:
```

org.eclipse.jface.util.Assert$AssertionFailedException: Assertion failed: 
	at org.eclipse.jface.util.Assert.isTrue(Assert.java:179)
	at org.eclipse.jface.util.Assert.isTrue(Assert.java:164)
	at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.setActivePage(FlexMultiPageEditorPart.java:569)
	at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.setActivePage(CodeAndDesignEditor.java:647)
	at com.adobe.flexbuilder.editors.mxml.MXMLEditor.setActivePage(MXMLEditor.java:487)
	at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.createPartControl(FlexMultiPageEditorPart.java:235)
	at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.createPartControl(CodeAndDesignEditor.java:162)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:662)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:462)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:313)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:180)
	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:270)
	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:473)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1256)
	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1209)
	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1608)
	at org.eclipse.ui.internal.PartStack.add(PartStack.java:499)
	at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:103)
	at org.eclipse.ui.internal.PartStack.add(PartStack.java:485)
	at org.eclipse.ui.internal.EditorStack.add(EditorStack.java:112)
	at org.eclipse.ui.internal.EditorSashContainer.addEditor(EditorSashContainer.java:63)
	at org.eclipse.ui.internal.EditorAreaHelper.addToLayout(EditorAreaHelper.java:225)
	at org.eclipse.ui.internal.EditorAreaHelper.addEditor(EditorAreaHelper.java:213)
	at org.eclipse.ui.internal.EditorManager.createEditorTab(EditorManager.java:778)
	at org.eclipse.ui.internal.EditorManager.openEditorFromDescriptor(EditorManager.java:677)
	at org.eclipse.ui.internal.EditorManager.openEditor(EditorManager.java:638)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2854)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2762)
	at org.eclipse.ui.internal.WorkbenchPage.access$11(WorkbenchPage.java:2754)
	at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2705)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2701)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2685)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2668)
	at org.eclipse.ui.ide.IDE.openEditor(IDE.java:683)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI.openEditor(FlexProjectUI.java:264)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI.access$2(FlexProjectUI.java:259)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI$1.runInUIThread(FlexProjectUI.java:185)
	at org.eclipse.ui.progress.UIJob$1.run(UIJob.java:95)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2405)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2369)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2221)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:500)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:493)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

```

Other than that, everything else seems to be working fine.

---

### Post by pthivent on 2009-10-29
> **nabendt said:**
> Please be careful in the moment with upgrading to 9.10, just for running eclipse 3.5. I did and it is causing me some problems in the moment. It seems to be a problem with gtk, but I am not enough into this, only know that I am not able to install eclipse plugins or using subclipse at all.

Cheers.

As described in [Upgrade to Karmic: Eclipse/Aptana UI woes]("http://bit.ly/T8MIc"), the workaround is to set the GDK_NATIVE_WINDOWS environment variable. So, at least for now, write your startup script like this:

```

#!/bin/bash
export GDK_NATIVE_WINDOWS=true
/opt/eclipse/eclipse
```

---

