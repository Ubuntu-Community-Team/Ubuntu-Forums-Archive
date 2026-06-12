---
title: "MATLAB printing problem"
date: 2008-08-10
forum: General Help
---

### Post by subjugater on 2008-08-10
I have been expriencing the following errors for a long time when I was trying to print programs or plots by simply clicking the print icon in MATLAB.

=============================================================================
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
	at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
	at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
	at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
	at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
	at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
	at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
	at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
	at com.mathworks.widgets.text.print.PrintSettings.showPrintDialog(PrintSettings.java:665)
	at com.mathworks.mde.cmdwin.XCmdWndView.print(XCmdWndView.java:1644)
	at com.mathworks.mde.cmdwin.CmdWinEditorKit$PrintAction.actionPerformed(CmdWinEditorKit.java:1359)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI.doClick(MBasicMenuItemUI.java:1142)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI$MouseInputHandler.mouseReleased(MBasicMenuItemUI.java:962)
	at java.awt.Component.processMouseEvent(Component.java:6041)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5806)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4413)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
==========================================================================

It seems that this is a java issue. But the thing is that I originally was suffered by the issue like:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
xxx@ubuntu:~$ matlab
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5581767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb55818b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb591529d]
#3 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef4922e]
#4 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef27ed7]
#5 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xaef28188]
#6 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xaef2848f]
#7 [0xafe1a68e]
#8 [0xafe12e9d]
#9 [0xafe12e9d]
#10 [0xafe10207]
#11 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x620967d]
#12 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x63057d8]
#13 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209510]
#14 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f38b]
#15 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1e7c96d]
#16 [0xafe1a68e]
#17 [0xafe12d37]
#18 [0xafe10207]
#19 /usr/local/matlab75/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x620967d]
MATLAB: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)
xxx@ubuntu:~$
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

This nasty problem is encountered when I was launching matlab. Now, I have successfully solved this problem by the 2-step way below:

=============================================================
1.
Matlab uses a jvm of its own.

adding this

"export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.04/jre"

as first line of $MATLABROOT/bin/matlab .

Makes Matlab use an external jvm (java-6-sun-1.6.0.04 for me).

2.
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
==============================================================

I am really wondering that what should I do now to make Matlab work properly. I am now utterly comfused. Any comments? Thanks in advance.

BTW, I have searched and read dozens of previous threads regarding this kind of issue. But they did not help too much.

---

### Post by MikaelHolber on 2008-09-16
I have the exact same problem. Looking for a solution but haven't found anything yet.

---

