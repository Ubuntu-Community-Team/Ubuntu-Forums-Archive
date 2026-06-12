---
title: "cx3600 printer not working, maybe gs esp problem"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by gc1 on 2005-07-23
My Epson cx3600 printer will work with another Debian distro but not with Ubuntu. I have suitable drivers with CUPS and Gimp-Print. Top shows that cupsys takes over most of the CPU and will keep running indefinitely with the command gs esp in operation. I have had this problem for a long time and an expert helper thought that gs esp and rastertoprint seemed to be the source of the problem. Is there a way to test the performance of gs esp perhaps?

---

### Post by gc1 on 2005-07-24
I have got the printer working: only in Gimp for images and graphic files. Gimp is happy with Epson drivers from Gimp-print for the models C62 and CX-3100 and CX-3200, so I have confirmed that these drivers were suitable. However they don't seem to interface properly with cupsys and looking at the log seems to show a repetitive loop. The PID of the gs esp routine gets stopped with status 0, presumably timed out.
Any ideas?

---

### Post by PuleX on 2005-10-03
Thanks for the info! My Epson Stylus Color CX3600 printer is now working with the driver for the C62.

Update: aand I added the info to the Ubuntu Wiki page about printer hardware support.  :-)

---

### Post by Tobs1 on 2006-08-24
Where did you get the driver and how do you load it

New to Ubuntu

---

