---
title: "Trouble with printer HP P1005"
date: 2009-07-08
forum: Hardware
---

### Post by marsislav on 2009-07-08
Hello! I have installed "Ubuntu" 9.04 and printer HP LaserJet P1005 with USB port. Installation of printer was normal, the OS download necessary PLUG-IN`s and take me back message "Printer installation successful" or something like that. But! When I trying to print some kind of documet or picture the OS show message "Printing..." , but in actuality the printer just do nothink... /no action/ - as though ....NO command send to printer. /Sorry for my horrible english/ 
That is the LOG file generated from "printingbuginfo" shell scrip downloaded from Ubuntu official WEB site.

> ProblemType: printingbuginfo v2.0: printingbug+localusb ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)) 
CupsConfiguredDevices: device for HP_LaserJet_P1005: hp:/usb/HP_LaserJet_P1005?serial=BC15BL5 
CupsConfiguredPPDs: HP_LaserJet_P1005: HP LaserJet p1005 hpijs, 3.9.2 
Date: Sun Jul  5 11:48:14 2009 
DesktopEnvironment: GNOME 
DistroRelease: Ubuntu 9.04 
EtcPapersize: letter 
InstalledPrintingPackages: 
 ii  cups-driver-gutenprint   5.2.3-0ubuntu5           printer drivers for CUPS 
 ii  foo2zjs                  20090217-0ubuntu4        Support for printing to ZjStream-based printers 
 ii  foomatic-db              20090218-0ubuntu3        OpenPrinting printer support - database 
 ii  foomatic-db-engine       4.0.0-0ubuntu6.1         OpenPrinting printer support - programs 
 ii  foomatic-db-hpijs        20090218-0ubuntu3        OpenPrinting printer support - database for HPIJS driver 
 ii  foomatic-filters         4.0.0-0ubuntu9           OpenPrinting printer support - filters 
 ii  ghostscript              8.64.dfsg.1-0ubuntu8     The GPL Ghostscript PostScript/PDF interpreter 
 ii  gs-esp                   8.64.dfsg.1-0ubuntu8     Transitional package 
 ii  hpijs                    3.9.2-3ubuntu4           HP Linux Printing and Imaging - gs IJS driver (hpijs) 
 ii  hplip                    3.9.2-3ubuntu4           HP Linux Printing and Imaging System (HPLIP) 
 ii  libgnomeprint2.2-0       2.18.6-1                 The GNOME 2.2 print architecture - runtime files 
 ii  min12xxw                 0.0.9-1ubuntu2           Printer driver for KonicaMinolta PagePro 1[234]xxW 
 ii  openprinting-ppds        20090218-0ubuntu3        OpenPrinting printer support - PostScript PPD files 
 ii  pnm2ppa                  1.12-16.2ubuntu1         PPM to PPA converter 
 ii  pxljr                    1.1-0ubuntu6             Driver for HP's Color LaserJet 35xx/36xx color laser printers 
 ii  splix                    2.0.0-0.1ubuntu3.1       Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers 
Locale: LANG=en_US.UTF-8, LC_CTYPE=en_US.UTF-8, LC_PAPER=en_US.UTF-8 
Uname: Linux marsislav-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux 
UsbPrinterDevices:  
UsbPrinterIEEE1284Id:  
UsbPrinterKernelModules: usblp                  20224  0  
lsusb: 
 Bus 001 Device 007: ID 03f0:3d17 Hewlett-Packard  
 Bus 001 Device 005: ID 050d:705a Belkin Components F5D7050A Wireless Adapter 
 Bus 001 Device 003: ID 413c:0108 Dell Computer Corp.  
 Bus 001 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard 
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




Thank You ! /And sorry again for my english /
Marsislav

---

### Post by Imunalia on 2009-07-08
I have the same printer and had a similar issue. The following are the steps I took
 
Open the printer controls
Delete the defaultly created printer
Create a new printer and follow its directions, it should tell you that you need the HP tools and then it will offer to fetch it for you.
Get the HP tools and follow its instructions. From here on it will continue to install without a hitch.
Turn the printer off then on wait for ubuntu to pick it up again and you should be good to go.
 
As a warning this printer is slow as a turtle as it spools. Some times it can take 4 or 5 minutes to start. You will just have to be patient. Check the printer status, if it says processing just wait.
 
Hope it helps

---

### Post by marsislav on 2009-07-08
Thank You for the answer.
Printer status show me that message - 

"/usr/lib/cups/filter/foomatic-rip failed"
I don`t know what to do...

---

### Post by marsislav on 2009-07-08
Thank You, man :)
The problem was solved. The OS was detect the wrong driver .... Yes, that is strange but it is fact.
System ->Administration->Printing 
Choose Properties on the specific printer and infront section "Make And Model: choose "Change" button. And after that just select manual the right printer. Restart the printer and... Voala! :)
It`s working ! :)

---

### Post by neon100 on 2009-11-03
> **marsislav said:**
> Thank You for the answer.
Printer status show me that message - 

"/usr/lib/cups/filter/foomatic-rip failed"
I don`t know what to do...

Same problem. Any suggested solution?

---

