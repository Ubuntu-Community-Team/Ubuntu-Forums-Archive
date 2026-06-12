---
title: "[SOLVED] Errors when Printing using Ubuntu 7.10"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by vortex0007 on 2008-01-03
I have an HP LaserJet 1300n network printer that is now refusing to print any documents. Windows printers on the network are able to print fine. 

From Ubuntu 7.10, I choose Print, and two printer icons appear in the top right hand panel and then one of them gets a red circle with a white line through it. I click on the icon and it reads "Status Processing" for the print job I just selected.

I opened up /var/log/syslog and it continues to repeat the following error:

Jan  3 16:04:52 NAME hp_LaserJet_1300n?ip=W.X.Y.Z: io/hpmud/jd.c 484: timeout write_channel hp:/net/hp_LaserJet_1300n?ip=W.X.Y.Z 

followed by a "ERROR: check device; will retry in 30 seconds...

I've been searching the forums and find no general advice on troubleshooting printing problems or printers in general. 

Where can I find a general troubleshooting document or even a basic explanation of how printing works in Linux?

Or if anyone knows a fix for this that would be useful.

---

### Post by Paul Moir on 2008-01-03
Check the logs in /var/log/cups (especially error_log) and see if there's anything useful there for a start.

Since UNIX is old there's a bunch of different ways to print.  CUPS unifies these and outputs the data to the printer (via the physical drivers in the kernel like the network and USB drivers).  CUPS can readily be accessed by the System->administration->print program or directly from a web browser by:

[http://localhost:631/](http://localhost:631/) 


Hopefully that gets you started.  ip=w.x.y.z seems suspicous to me, like it doesn't know the ip of the printer.

---

### Post by vortex0007 on 2008-01-03
Sorry I should have specified - I changed the IP address you see in the error message from the original, correct IP to the letters you see. I don't ever post my personal IP addresses in public forums - even if it is just a printer. 

Same with the computer name in the error message you see on this post. 

Thanks for the reply - I'll look into this and see if it gets me started.

---

### Post by vortex0007 on 2008-01-04
I was able to solve this problem by using HP's Linux Imaging and Printing Tool found here.

[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html) 

Very cool.

---

