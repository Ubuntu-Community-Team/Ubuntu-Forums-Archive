---
title: "JAVA Upgrading Problem"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Apoorvbarwa on 2009-03-27
i have ubuntu 8.10 firefox 3.0.7
i downloaded jre-6u13-linux-i586.bin in /home/apoorv/java
then typed ./jre-6u13-linux-i586.bin

this made a directory /home/apoorv/java/jre1.6.0_13
in terminal i typed
export JAVA_HOME=/home/apoorv/java/jre1.6.0_13
export JRE_HOME=/home/apoorv/java/jre1.6.0_13

on typing echo $JAVA_HOME i get
/home/apoorv/java/jre1.6.0_13

and echo $JRE_HOME 
/home/apoorv/java/jre1.6.0_13

echo $JDK_HOME
/home/apoorv/jdk1.6.0_13/


but in System--->Prefrences--->Sun Java 6 Plugin Control Panel 
in under Java tab---> Java Applet Runtime Settings---->View
i can see under product name two jre
JRE 1.6.0_13 /home/apoorv/java/jre1.6.0_13----> enabled
JRE 1.6.0_10 /usr/lib/jvm/java-6-sun-1.6.0.10/jre------>enabled
i disabled the second one....and also removed it but still whenever i see it again it comes back.....same is true with the JNLP settings
 and whenever i check version of java in--->General tab "about" it shows me Version 6 Update 10 (build 1.6.0_10-b33)
please tell me what m i doing wrong......

also i have installed openlaszlo-4.2.0.2-unix.tar.gz----->extracted to /home/apoorv/lps-4.2.0.2

and ide4laszlo-allInOne-gtk-lps4.0.10_jre.zip----->extracted to /home/apoorv/eclipse

tomcat directory---> /home/apoorv/lps-4.2.0.2/Server/tomcat-5.0.24/bin/startup.sh------->sometimes this works
and i can also view hello.lzx from [http://www.openlaszlo.org/lps4.2/docs/installation/run.html](http://www.openlaszlo.org/lps4.2/docs/installation/run.html)

but i cannot get eclipse to work......in File--->New---->Project----->Laszlo Project----name
when i add an .lzx file to src
it shows me Error opening the editor. and in details shows 
java.lang.NullPointerException

please help me out with these queries

---

### Post by yeats on 2009-03-27
This may help (from [here]("https://help.ubuntu.com/community/Java")):

> Just installing new Java flavours does not change the default Java pointed to by /usr/bin/java. You must explicitly set this:

    * Open a Terminal window
    * Run sudo update-java-alternatives -l to see the current configuration and possibilities.
    * Run sudo update-java-alternatives -s XXXX to set the XXX java version as default. For Sun Java 6 this would be sudo update-java-alternatives -s java-6-sun
    * Run java -version to ensure that the correct version is being called. 

You can also use the following command to interactively make the change;

    * Open a Terminal window
    * Run sudo update-alternatives --config java
    * Follow the onscreen prompt 

---

### Post by Apoorvbarwa on 2009-03-27
this is what i did
apoorv@apoorv-desktop:~$ sudo update-java-alternatives -l
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
apoorv@apoorv-desktop:~$ 

and neither of them have the update version...........which is in /home/apoorv/jre1.6.0_13

apoorv@apoorv-desktop:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java

this also asks for a selection wherein i cannot put the path 
plzz help

also plz can anyone help me in setting up eclipse........thats my main concern

---

### Post by Apoorvbarwa on 2009-03-27
this is wat i did.....
apoorv@apoorv-desktop:~$ echo $JAVA_HOME
/home/apoorv/jdk1.6.0_13
apoorv@apoorv-desktop:~$ /home/apoorv/lps-4.2.0.2/Server/tomcat-5.0.24/bin/startup.sh
Using CATALINA_BASE:   /home/apoorv/lps-4.2.0.2/Server/tomcat-5.0.24
Using CATALINA_HOME:   /home/apoorv/lps-4.2.0.2/Server/tomcat-5.0.24
Using CATALINA_TMPDIR: /home/apoorv/lps-4.2.0.2/Server/tomcat-5.0.24/temp
Using JAVA_HOME:       /home/apoorv/jdk1.6.0_13

apoorv@apoorv-desktop:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.4) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)

does this mean that java environment variable is set ??????
still my java version is not 1.6.0_13.......

---

### Post by Apoorvbarwa on 2009-03-27
i get this error in my eclipse--path/home/apoorv/eclipse

java.lang.NullPointerException
	at org.eclipse.ui.internal.browser.BrowserViewer.home(BrowserViewer.java:264)
	at org.eclipse.ui.internal.browser.BrowserViewer.setURL(BrowserViewer.java:650)
	at org.eclipse.ui.internal.browser.BrowserViewer.setURL(BrowserViewer.java:287)
	at org.eclipse.ui.internal.browser.WebBrowserEditor.createPartControl(WebBrowserEditor.java:80)
	at org.eclipse.laszlo.rct.editor.ve.VisualEditor.createPartControl(VisualEditor.java:206)
	at org.eclipse.ui.part.MultiPageEditorPart.addPage(MultiPageEditorPart.java:190)
	at org.eclipse.ui.part.MultiPageEditorPart.addPage(MultiPageEditorPart.java:160)
	at org.eclipse.laszlo.rct.editor.RCTMultiPageEditor.createEditorPages(RCTMultiPageEditor.java:1092)
	at org.eclipse.laszlo.rct.editor.RCTMultiPageEditor.createPages(RCTMultiPageEditor.java:187)
	at org.eclipse.ui.part.MultiPageEditorPart.createPartControl(MultiPageEditorPart.java:283)
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
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2719)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2633)
	at org.eclipse.ui.internal.WorkbenchPage.access$12(WorkbenchPage.java:2625)
	at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2577)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2572)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2556)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2547)
	at org.eclipse.ui.ide.IDE.openEditor(IDE.java:644)
	at org.eclipse.ui.ide.IDE.openEditor(IDE.java:603)
	at org.eclipse.laszlo.rct.script.ui.edit.EditorUtility.openInEditor(EditorUtility.java:239)
	at org.eclipse.laszlo.rct.script.ui.edit.EditorUtility.openInEditor(EditorUtility.java:159)
	at org.eclipse.laszlo.rct.script.ui.actions.OpenAction.run(OpenAction.java:138)
	at org.eclipse.laszlo.rct.script.ui.actions.OpenAction.run(OpenAction.java:124)
	at org.eclipse.laszlo.rct.script.ui.actions.SelectionDispatchAction.dispatchRun(SelectionDispatchAction.java:102)
	at org.eclipse.laszlo.rct.script.ui.actions.SelectionDispatchAction.run(SelectionDispatchAction.java:84)
	at org.eclipse.laszlo.rct.script.ui.explorer.ScriptExplorerActionGroup.handleOpen(ScriptExplorerActionGroup.java:225)
	at org.eclipse.laszlo.rct.script.ui.explorer.ExplorerPart$5.open(ExplorerPart.java:372)
	at org.eclipse.jface.viewers.StructuredViewer$2.run(StructuredViewer.java:820)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.core.runtime.Platform.run(Platform.java:857)
	at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:46)
	at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:193)
	at org.eclipse.jface.viewers.StructuredViewer.fireOpen(StructuredViewer.java:818)
	at org.eclipse.jface.viewers.StructuredViewer.handleOpen(StructuredViewer.java:1079)
	at org.eclipse.jface.viewers.StructuredViewer$6.handleOpen(StructuredViewer.java:1183)
	at org.eclipse.jface.util.OpenStrategy.fireOpenEvent(OpenStrategy.java:263)
	at org.eclipse.jface.util.OpenStrategy.access$2(OpenStrategy.java:257)
	at org.eclipse.jface.util.OpenStrategy$1.handleEvent(OpenStrategy.java:297)
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
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:106)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:153)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:504)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:443)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1169)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1144)

does this mean that the java environment variable is not set?????
plz help:confused:

---

