---
title: "ubunutu 14.04 xsane 0.998 LONNNG time to scan for devices"
date: 2014-09-23
forum: Hardware
---

### Post by goodstuff9 on 2014-09-23
Ubuntu 14.04, kernel 3.13.0.36 generic, xsane 0.998, HPLIP 3.14.6, HP Photosmart 7520 connected directly to the computer via a USB cable.    


Until recently, this combination of hardware and software worked great for printing and scanning.  

Now for some reason, a problem has arisen:  Whenever I try to scan using xsane (or Simple Scan), it consistently takes 5 - 6 minutes for the application to "find" the scanner.  It always eventually does find the scanner, and once it does find the scanner, it scans just fine.  But it always takes 5 - 6 minutes to find the scanner.  

Also, if I try to scan to the computer using the control panel on the printer itself, I get these error message on the printer:  


No Computer Found

(USB) Check that:  
- The USB cable is firmly connected.  
- The HP printer software is installed on the computer.  


The cable seems to me to be firmly installed on both ends.  Anyway, as I wrote above, the computer scanning program always does eventually find the scanner.  And, when I try just regular printing from the computer, it works great, no delay "looking" for the printer.  So, I don't think the cable is the problem.  

I know HPLIP 3.14.6 is installed, so missing printer software shouldn't be the problem.  

When I run HPLIP's driver diagnostic program, it reports no errors, but it does take about five minutes for it to find the HP scanner once it gets to that stage.  But it does eventually find it.  

lsusb reports this in part (the Photosmart):  Bus 003 Device 116: ID 03f0:bc11 Hewlett-Packard 


Anyone have any ideas on why it is taking so long for the scanner to be found?

---

