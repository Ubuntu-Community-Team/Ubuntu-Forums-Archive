---
title: "HP Laserjet 1000"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by mr2v6 on 2005-12-03
Hello,
Need some help setting up an HP laserjet 1000. Ubuntu seems to have the printer on file, but when I do a testpage, nothing happens. Any help is appreciated.
thanks,
Mr2v6

---

### Post by Moloko on 2005-12-03
I had a similar problem with a LaserJet 1100, the problem was solved removing a reinstalling the print related packages.

[http://www.ubuntuforums.org/showthread.php?t=97677](http://www.ubuntuforums.org/showthread.php?t=97677)

Regards.

---

### Post by mlomker on 2005-12-03
I have a 1012 and it works perfectly.  You might want to check the output of **lsusb** when plugged in and **dmesg | tail** right after plugging it in to make sure that it is being recognized.

---

