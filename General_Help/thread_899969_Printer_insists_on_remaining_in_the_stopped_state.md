---
title: "Printer insists on remaining in the stopped state"
date: 2008-08-24
forum: General Help
---

### Post by AngusM on 2008-08-24
I have a Lexmark z600 printer with the z600cups packaged installed. For some reason when I try printing anything and look at the print jobs status window, the print job insists on remaining "stopped". If I try "reprinting" then it goes into the "processing" state, then immediately to "stopped".

I'm not sure what to tell you about my setup. The device URI is given as:
usb://Dell/Photo%20AIO%20Printer%20924
I'm not even sure if that is right, but it was what was given when I pushed the "Change" button. The Make and Model is given as:
Lexmark Z600 v1.0-1

---

### Post by AngusM on 2008-08-25
I went poking around looking for error logs I found this when calling sudo cat /var/log/cups/error_log:
E [25/Aug/2008:16:52:30 -0400] [Job 21] No %%BoundingBox: comment in header!
E [25/Aug/2008:16:52:31 -0400] [Job 21] Cannot Process Raster
E [25/Aug/2008:16:52:31 -0400] PID 22858 (/usr/lib/cups/filter/rastertoz600) stopped with status 1!
E [25/Aug/2008:16:52:32 -0400] [Job 21] Job stopped due to filter errors.

Does this shed any light on the problem?

---

### Post by Crafty Kisses on 2008-08-25
Lexmark isn't really supported in Linux, look over these

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by AngusM on 2008-08-25
Unfortunately, none of these are the printer I have. What I need is to know how to get this one working, not Monday-morning-quarterback data on what I should have done.

---

