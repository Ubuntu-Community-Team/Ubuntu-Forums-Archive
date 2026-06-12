---
title: "usr/lib/cups/filter/rastertoqpdl not available"
date: 2016-07-02
forum: Hardware
---

### Post by kent122 on 2016-07-02
Ubuntu 16.04 on a laptop computer.  I am a computer and ubuntu novice.
 
 
 I have been using Ubuntu for several months, and last printed anything about two weeks ago,  Today, my Samsung ML-2240 laser printer is switched on and connected.  I cannot print anything.
 
 
 Buried in “Printers-localhost / Printer Properties / Settings / Printer State” is the message “Idle - File "/usr/lib/cups/filter/rastertoqpdl" not available: No such file or directory”
 
 
 I did a large ubuntu update earlier today.
 
 
 How do I get it to print again?  I have "Checked if already posted", but the messages returned were too technical or off-subject for me.

---

### Post by hans12345 on 2016-08-04
Did you find a solution?

I have the same problem after upgrading to 16.04

---

### Post by hans12345 on 2016-08-04
Here is the cups log file:
```
E [04/Aug/2016:07:36:36 +0200] Filter \"rastertopwg\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"pstopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"bannertopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"urftopdf\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:07:36:36 +0200] cupsdLoadBanners: Unable to open banner directory "/usr/share/cups/banners": No such file or directory
E [04/Aug/2016:07:36:36 +0200] ML-1640-Series: File \"/usr/lib/cups/filter/rastertoqpdl\" not available: No such file or directory
E [04/Aug/2016:07:36:36 +0200] Photosmart-C5200-series: File \"/usr/lib/cups/filter/hpcups\" not available: No such file or directory
E [04/Aug/2016:12:52:14 +0200] Filter \"rastertopwg\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"pstopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"bannertopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"urftopdf\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:12:52:14 +0200] cupsdLoadBanners: Unable to open banner directory "/usr/share/cups/banners": No such file or directory
E [04/Aug/2016:12:52:14 +0200] ML-1640-Series: File \"/usr/lib/cups/filter/rastertoqpdl\" not available: No such file or directory
E [04/Aug/2016:12:52:14 +0200] Photosmart-C5200-series: File \"/usr/lib/cups/filter/hpcups\" not available: No such file or directory
E [04/Aug/2016:13:16:53 +0200] Filter \"rastertopwg\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"pstopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"texttopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"bannertopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"urftopdf\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"imagetoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] Filter \"gstoraster\" not found.
E [04/Aug/2016:13:16:53 +0200] cupsdLoadBanners: Unable to open banner directory "/usr/share/cups/banners": No such file or directory
E [04/Aug/2016:13:16:53 +0200] ML-1640-Series: File \"/usr/lib/cups/filter/rastertoqpdl\" not available: No such file or directory
E [04/Aug/2016:13:16:53 +0200] Photosmart-C5200-series: File \"/usr/lib/cups/filter/hpcups\" not available: No such file or directory
E [04/Aug/2016:13:28:34 +0200] ML-1640-Series: File \"/usr/lib/cups/filter/rastertoqpdl\" not available: No such file or directory
E [04/Aug/2016:13:28:34 +0200] Photosmart-C5200-series: File \"/usr/lib/cups/filter/hpcups\" not available: No such file or directory
E [04/Aug/2016:13:30:04 +0200] [cups-deviced] PID 11340 (gutenprint52+usb) stopped with status 1!
```

---

