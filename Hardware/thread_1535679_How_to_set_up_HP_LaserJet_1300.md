---
title: "How to set up HP LaserJet 1300"
date: 2010-07-21
forum: Hardware
---

### Post by aPieceOfCode on 2010-07-21
I really need to know what to do as soon as possible. I installed ubuntu 10.04 on a computer in my firma, and forgot to check if printing works. That problem needs to be fixed rapidly.
OS: Ubuntu 10.04 (lucid)
Printer: HP LaserJet 1300


I tried running hp-setup, but it says som PPD files are missing.

---

### Post by ronnielsen1 on 2010-07-21
That printer should be picked up on automatically. What does it say if you go to System > Administration > Printing and click ADD in the new window?

> [IMG]http://welcome.hp-ww.com/img/s.gif[/IMG]                                                                                                                         
     Next »            
            [B]You have selected Ubuntu  10.04 using the HP LaserJet 1300 Printer.

Ubuntu 10.04 supplies  HPLIP 3.10.2 and it does support your printer.

As the version of  HPLIP supplied with your operating system supports your printer, you may  continue to use that version of HPLIP.

You may now optionally  download the latest version of HPLIP to get access to new features and  bug fixes.

[/B]

      **Please click *Previous* to select a different operating  system or printer.**

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by aPieceOfCode on 2010-07-21
The Add button is disabled. By the way, theres "Server" main-menu entry, and CUPS (whatever that is) seems to not be connected. Any ideas?

---

### Post by ronnielsen1 on 2010-07-21
> It could be that the cups service is not running.
Either start it via menus or in a terminal window give the command:

sudo /etc/init.d/cups start

[http://ubuntuforums.org/showthread.php?t=1360426](http://ubuntuforums.org/showthread.php?t=1360426)

---

### Post by aPieceOfCode on 2010-07-21
Worked, Thanks!

---

