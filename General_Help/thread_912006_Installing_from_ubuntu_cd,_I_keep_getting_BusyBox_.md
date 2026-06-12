---
title: "Installing from ubuntu cd, I keep getting BusyBox v1.1.3 message?"
date: 2008-09-06
forum: General Help
---

### Post by Robohoe on 2008-09-06
i keep receiving this message:
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter ‘help’ for a list of built-in commands.

(initramfs)


my computer:
3.0Ghz Intel Core 2 Duo E8400 6MB Cache FSB 1333
Stock Intel LGA775 Heatsink and Fan
ASUS P5Q (Intel P45, 2xPCIEx, 8-Channel Audio, LAN, 8xSATA2, 1394, 1333FSB)
4GB (2GBx2) PC6400 DDR2 800Mhz Memory Lifetime Warranty
750GB 7200RPM 32MB Cache Serial ATA300
20X Samsung SH-S202G Dual Layer DVD+/-RW/CDRW w/Nero
512MB NVIDIA GeForce 8800 GT GDDR3 PCI Express DVI/Tvout 
Foxconn Black FX-776 (4 5.25, 6 3.5 bays) 2 Fans, Front Audio/USB
650watt Cooler Master eXtreme Power RS-650-PCAR


i'm not sure what to do? if someone could explain in lamest terms what to do, id really appreciate it.

btw this isnt a burned cd, its an orginal ubuntu 8.04.1 lts desktop edition cd.

---

### Post by Robohoe on 2008-09-06
bump

---

### Post by wolfen69 on 2008-09-06
i had this problem once, and wound up just using the alternate cd instead. [Ubuntu 8.04.1 Alternate CD]("http://releases.ubuntu.com/hardy/ubuntu-8.04.1-alternate-i386.iso")

---

### Post by ModelM on 2008-09-06
When this happened to me I had to go to the boot prompt when the CD booted & add:

all_generic_ide

to the command line options. All worked fine after that.

---

