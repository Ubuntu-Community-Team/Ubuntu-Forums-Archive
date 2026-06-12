---
title: "sapgui  710"
date: 2008-11-13
forum: General Help
---

### Post by diaz8 on 2008-11-13
Hi, 

After upgrading to Ubuntu 8.10 sapgui client has started make strange things. 
In transaction se38 when viewing/editing programs with more than 2000 lines the scrolling makes the editor to display garbage. If you continue to scroll and reaches to line 1900 more or less then the garbage disapears and the text shows clear. 
If you scroll up to see the lines from 1 to 1900 then the garbage appears again. 
Have tested with two versions of java (sun jre 5 and 6 from the repositories) and with every revision of the sapgui client from 0 to 6. 
This garbage didn't appeared with Ubuntu 8.04. 

[http://img395.imageshack.us/my.php?image=pantallazovd6.png](http://img395.imageshack.us/my.php?image=pantallazovd6.png)

Anyone has an idea?. 
Regards.

---

### Post by diaz8 on 2008-11-15
The problem is most probably due to acceleration mode in intel video driver. With Ubuntu 8.10 the default mode is EXA, changing it to XAA the problem disappears. 

However in that mode another applications (mostly Video players) crash or don't work. Do anyone knows the intel video driver options well enough?. May be a little option could be used to set EXA mode and not to see garbage in SAPGUI. 

Best Regards.

---

### Post by christir on 2009-11-02
Hi,

when upgrading Ubuntu 9.04 -> 9.10 I got problems with my SAPGUI. When trying to run the guilogon I get the following java thread exception:

Exception in thread "Thread-1" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at com.sap.platin.Gui$1.run(Gui.java:93)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...1 more
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at com.sap.platin.Gui.main(Gui.java:46)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...1 more

Any clues anyone? :-)

Best,
ChR

---

### Post by sowjendra on 2009-11-14
Hi CHR 

I have done a fresh installation of ubuntu 9.10 and installed the latest PlatinGUI-Linux-710r10.jar SAPgui, It has worked like a charm. 

Please uninstall your SAPgui and try to reinstall the latest one.

Hope so you will overcome this issue.

Regards
Surendra

---

