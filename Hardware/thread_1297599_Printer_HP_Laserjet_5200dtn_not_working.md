---
title: "Printer HP Laserjet 5200dtn not working"
date: 2009-10-21
forum: Hardware
---

### Post by PhilipGanchev on 2009-10-21
Hi all. I'd appreciate any help making my printer work. When I print a test page or a text file, nothing is printed. The job appears in the print status list and the stays there forever.

It's a network printer, model HP LaserJet 5200dtn.  When I configure it as a new printer, I select "HP Laserjet 5200" from the list of printers, and it has the correct IP address. For Connections, I select "HPLIP". For the driver, there are 5 choices, none of which work: postscript, hpjis, CUPS+Gutenprint, CUPS+Gutenprint simplified, postscript.

According to LinuxPrinting.org, the printer is supported by the HPLIP driver. Packages hplip and hpijs are installed, and cupsd is running. The printer works from Windows.

---

### Post by Dark_Stang on 2009-10-22
HPLIP says you're good.
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_5200.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_5200.html)

Install the latest HPLIP software and everything should be fine.

---

### Post by PhilipGanchev on 2009-10-22
The HPLIP web site says my printer is supported since HPLIP version 0.9.11 ([http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_5200.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_5200.html)), while I have version 3.9.2. The newest version is 3.9.8. The problem must be elsewhere.

||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          3.9.2-3ubuntu4 HP Linux Printing and Imaging System (HPLIP)

---

### Post by PhilipGanchev on 2010-03-30
It's been 5 months. Anyone have any ideas?

---

### Post by PRC09 on 2010-03-30
Try using the newest version from hplip.I had all kinds of grief until I installed the latest version and followed the install instructions on the website....Hope this helps.....


[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

