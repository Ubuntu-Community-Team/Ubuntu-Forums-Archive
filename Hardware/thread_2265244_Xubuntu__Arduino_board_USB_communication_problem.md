---
title: "Xubuntu / Arduino board USB communication problem"
date: 2015-02-13
forum: Hardware
---

### Post by garymcrobertpdx on 2015-02-13
Not sure if this the appropriate forum for dealing with a Xubuntu and a Arduino board
USB communication problem but here it is. (My apologizes in advance if this it the wrong
area of the Ubuntu forum )  (Also have been to the Arduino support forum not luck there yet)

&#65279;Been using 14.10 day one, brand spanking new Arduino Mega 2560 board also
down loaded  the Arduino IDE 1.6.0 as of yesterday.  Just reinstalled OpenJDK
Java 7 Runtime via the Ubuntu Software Center.  

Open Arduino folder,  Execute  Sketch script,
Tools > Board select Arduino Mega or Mega 2560
Processor > ATmega2560
Port > /dev/ttyACM0 (Ardiono Mega or Mega 2560)

Attempt a upload of the default minimal code.

ERROR:

Arduino: 1.6.0 (Linux), Board: "Arduino Mega or Mega 2560, ATmega2560 (Mega 2560)"

Sketch uses 642 bytes (0%) of program storage space. Maximum is 253,952 bytes.
Global variables use 9 bytes (0%) of dynamic memory, leaving 8,183 bytes for local variables. Maximum is 8,192 bytes.
avrdude: ser_open(): can't open device "/dev/ttyACM0": Permission denied
ioctl("TIOCMGET"): Inappropriate ioctl for device
ioctl("TIOCMGET"): Inappropriate ioctl for device
avrdude: ser_send(): write error: Bad file descriptor
Problem uploading to board.  See [http://www.arduino.cc/en/Guide/Troubleshooting#upload](http://www.arduino.cc/en/Guide/Troubleshooting#upload) for suggestions.
processing.app.SerialException: Error opening serial port '/dev/ttyACM0'.
   at processing.app.Serial.<init>(Unknown Source)
   at processing.app.Serial.<init>(Unknown Source)
   at processing.app.SerialMonitor$3.<init>(SerialMonitor.java:94)
   at processing.app.SerialMonitor.open(SerialMonitor.java:94)
   at processing.app.Editor.handleSerial(Editor.java:2536)
   at processing.app.Editor$17.actionPerformed(Editor.java:688)
   at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2018)
   at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2341)
   at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:402)
   at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
   at javax.swing.AbstractButton.doClick(AbstractButton.java:376)
   at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:833)
   at javax.swing.plaf.basic.BasicMenuItemUI$Handler.menuDragMouseReleased(BasicMenuItemUI.java:943)
   at javax.swing.JMenuItem.fireMenuDragMouseReleased(JMenuItem.java:585)
   at javax.swing.JMenuItem.processMenuDragMouseEvent(JMenuItem.java:482)
   at javax.swing.JMenuItem.processMouseEvent(JMenuItem.java:428)
   at javax.swing.MenuSelectionManager.processMouseEvent(MenuSelectionManager.java:321)
   at javax.swing.plaf.basic.BasicPopupMenuUI$MouseGrabber.eventDispatched(BasicPopupMenuUI.java:859)
   at java.awt.Toolkit$SelectiveAWTEventListener.eventDispatched(Toolkit.java:2448)
   at java.awt.Toolkit$ToolkitEventMulticaster.eventDispatched(Toolkit.java:2340)
   at java.awt.Toolkit$ToolkitEventMulticaster.eventDispatched(Toolkit.java:2339)
   at java.awt.Toolkit$ToolkitEventMulticaster.eventDispatched(Toolkit.java:2339)
   at java.awt.Toolkit.notifyAWTEventListeners(Toolkit.java:2298)
   at java.awt.Component.dispatchEventImpl(Component.java:4768)
   at java.awt.Container.dispatchEventImpl(Container.java:2287)
   at java.awt.Component.dispatchEvent(Component.java:4698)
   at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4832)
   at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4492)
   at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4422)
   at java.awt.Container.dispatchEventImpl(Container.java:2273)
   at java.awt.Window.dispatchEventImpl(Window.java:2719)
   at java.awt.Component.dispatchEvent(Component.java:4698)
   at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:740)
   at java.awt.EventQueue.access$300(EventQueue.java:103)
   at java.awt.EventQueue$3.run(EventQueue.java:699)
   at java.awt.EventQueue$3.run(EventQueue.java:697)
   at java.security.AccessController.doPrivileged(Native Method)
   at java.security.ProtectionDomain$1.doIntersectionPrivilege(ProtectionDomain.java:76)
   at java.security.ProtectionDomain$1.doIntersectionPrivilege(ProtectionDomain.java:87)
   at java.awt.EventQueue$4.run(EventQueue.java:713)
   at java.awt.EventQueue$4.run(EventQueue.java:711)
   at java.security.AccessController.doPrivileged(Native Method)
   at java.security.ProtectionDomain$1.doIntersectionPrivilege(ProtectionDomain.java:76)
   at java.awt.EventQueue.dispatchEvent(EventQueue.java:710)
   at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:242)
   at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:161)
   at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:150)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:146)
   at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:138)
   at java.awt.EventDispatchThread.run(EventDispatchThread.java:91)
Caused by: jssc.SerialPortException: Port name - /dev/ttyACM0; Method name - openPort(); Exception type - Permission denied.
   at jssc.SerialPort.openPort(SerialPort.java:170)
   ... 50 more
Error opening serial port '/dev/ttyACM0'.

Can anyone here lend a newbie a hand or a couple of neurons. 

Thnaks

---

### Post by garymcrobertpdx on 2015-02-13
The solution appears to be one command. 
&#65279;sudo adduser <username> dialout
logout then login again in oder to have this take effect.

Also adding a &#65279;New file : /etc/udev/rules.d/usbasp.rules
With: ATTRS{idVendor}=="16c0", ATTRS{idProduct}=="05dc", MODE="0666", GROUP="plugdev"
May also be necessary

---

### Post by mdgeist on 2015-12-31
Thank you for this, I searched a bunch of other sites and none of them helped.
This also works on Linux Mint 17.3

---

### Post by alexvermillion on 2016-12-24
Thank you very much, I had the same problem and was getting very confused. The one command fixed it!

P.S. As a lurker on the forums, I created an account just to tell you how much this helped!

---

### Post by DuckHook on 2016-12-24
Welcome to the forums, alexvermillion,

It is very kind of you to express your gratitude and satisfaction, but please refrain from keeping old threads alive. As time passes, such necroposts skew the help database and the natural progression of obsolescence for old advice. This thread will now be retired.

---

