---
title: "Printing From Java"
date: 2008-08-23
forum: General Help
---

### Post by peterl_j on 2008-08-23
Hi

I am not sure where this belongs, but I am unable to print from Java.

I get the following:

peter@peter-main:~/java/secondprinttest$ java HelloWorldPrinter
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
        at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
        at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
        at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
        at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
        at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
        at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
        at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
        at sun.print.RasterPrinterJob.printDialog(RasterPrinterJob.java:856)
        at sun.print.PSPrinterJob.printDialog(PSPrinterJob.java:421)
        at HelloWorldPrinter.actionPerformed(HelloWorldPrinter.java:64)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
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
        at java.awt.Window.dispatchEventImpl(Window.java:2440)
        at java.awt.Component.dispatchEvent(Component.java:4243)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)


Has anyone any ideas about this please?

All the best

Peter L-J

---

### Post by qstraza on 2008-08-23
Is code 100 % correct? Cuz i see Null pointer exception...

---

### Post by peterl_j on 2008-08-23
Hi

Yes the code is correct as I downloaded helloWorldPrinter.java from the sun web site, and I get the same problem with a programme (JMRI) which certaily prints in Windows.

Peter

---

### Post by qstraza on 2008-08-23
give me the link of src. Ill try it on my ubuntu;p

---

### Post by peterl_j on 2008-08-23
Hi

Thanks, that would be very kind, and a great help.  (Would prove I am not going mad!)

[http://java.sun.com/docs/books/tutorial/2d/printing/examples/HelloWorldPrinter.java](http://java.sun.com/docs/books/tutorial/2d/printing/examples/HelloWorldPrinter.java)

and the actual code

[http://java.sun.com/docs/books/tutorial/2d/printing/examples/HelloWorldPrinter.java](http://java.sun.com/docs/books/tutorial/2d/printing/examples/HelloWorldPrinter.java)

All the best

Peter L-J

---

### Post by qstraza on 2008-08-23
well it works for me, i get a frame with a button saying "Print Hello World" when i click on it print dialog pops up, where you select printer and number of pages...

Is there something wrong with your jdk? Do you expirience any trouble with other java programs?

---

### Post by peterl_j on 2008-08-23
Hi

I have found this on the web.  It seems to be working for me!

   1. Click on the System menu item on the main panel (typically located at the top of the screen)
   2. Click on the Administration menu item
   3. Click on the Printing menu item
   4. Change the job options for each printer by:
         1. Click on the name of the printer in the list
         2. Click the Job Options tab
         3. Select the Portrait option in the Orientation drop down list
         4. Click the Apply button
         5. Repeat steps 4.1 - 4.4 for each printer in your list
   5. Close the Printer configuration window


All the best

Peter L-J

---

### Post by prostar on 2008-11-21
Peter, those last steps worked for me!  Our corp. expense reporting is java, and it would never print for me until doing that!

Java sucks BTW...

---

### Post by qstraza on 2008-11-21
> **prostar said:**
> Peter, those last steps worked for me!  Our corp. expense reporting is java, and it would never print for me until doing that!

Java sucks BTW...

There is nothing wrong with java.

---

### Post by craigster0 on 2009-03-08
i ran into the same problem when trying to print from XXE (XMLMind XML Editor).  it's a general problem with Java and/or CUPS (they're pointing fingers at each other).

i encountered it using Hardy Heron (Ubuntu 8.04), but it should also occur in Fesity Faun (7.04) and Gutsy Gibbon (7.10).

this bug occurs with CUPS version 1.2 or later and with Sun Java JRE 5 or 6.  it occurs because the CUPS folks added an "auto-orientation" option for certain printers which causes the Java library to crash because it doesn't recognize the option.

you can read about the bug on the CUPS web site here:

    [http://www.cups.org/str.php?L2610](http://www.cups.org/str.php?L2610)

that bug was closed in Nov. 2007 with the claim that its a Sun Java bug.


you can find the bug described here in the Sun Developer's Forum:

    [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6633656](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6633656)

according to the above page, it is fixed in Sun Java JRE 6 Update 10-build 20 and in Sun Java JRE 7-build 28.  unfortunately, Ubuntu 8.04 is shipping with Sun Java JRE 6 Update 7, so it's still broken for Ubuntu 8.04.

the above described Orientation GUI fix didn't work for me because i couldn't find the "job options" tab.  either i'm stupid, or else it has changed in Cups 1.3.7-1ubuntu3.


the only workaround that actually fixed the problem for me is described here:

    [http://www.pikopong.com/blog/2008/09/09/java-printing-fix-for-linux-with-cups/](http://www.pikopong.com/blog/2008/09/09/java-printing-fix-for-linux-with-cups/)

i'm using Ubuntu 8.04 (really Kubuntu 8.04) Hardy Heron.  what i did was edit /etc/cups/printers.conf and add the line

Option orientation-requested 3

just above </Printer> everywhere it appears in the file.  for example:

  ErrorPolicy retry-job
+ Option orientation-requested 3
  </Printer>

you must be root to edit the file.  to do this with sudo and vi:

    % sudo vi /etc/cups/printers.conf

you should probably save a backup copy of the file before you edit it.

after you edit the file you must restarts the Cups daemon.  try:

    % sudo /etc/init.d/cupsys restart

---

### Post by craigster0 on 2009-03-08
oh, i should have added that this bug may be fixed in OpenJDK-6 (one report here claims that its fixed):

    [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191)

but that doesn't help me any because my app, xxe (XMLmind XML Editor) gets a SIGSEGV when using the OpenJDK bundled with Ubununtu 8.04.  per the release notes that come with the editor, you need to be using Sun Java 1.5 or later; nothing else is supported.

once you install Sun Java 5 (or 6) on your box, you'll need to run the following to select that as the JRE that's run:

      % sudo update-alternatives --config java

---

