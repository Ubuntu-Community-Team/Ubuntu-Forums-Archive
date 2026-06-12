---
title: "Ubuntu 7.04 - cannot find hard disk driver"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by mike24hockey on 2007-07-28
i'm new to ubuntu and wanted to install it, but i'm having a problem installing it on my Lenovo Thinkpad T61.  I got the tip that the liveCD will work if you change the SATA config to "compatible" while you install.  However, when i try to install using the graphical version, it never boots up beyond its 'scrolling checklist' thingy.

Then i tried using the alternate text based installer.  I got farther in this installer, but when it got to the detecting hard drive part, it couldn't detect my driver.  it asked me to choose one, but I don't know what to choose.  I tried looking online but it hasn't helped me much.  I can't proceed farther in the install because the partitioning part doesn't work either (i guess it depends on it finding the hard drive driver in the first place).

Help would be greatly appreciated!!

specs:
currently running Windows Vista
Intel Core Duo processor
2 GB RAM

---

### Post by pcmanlin on 2007-07-28
Can you give some detailed information, such as your motherboard's type, chipset,  harddisk?

Commonly, the problem is about the sata controller and the bios.

---

### Post by mike24hockey on 2007-07-28
sure. thanks for the help.
Intel Centrino Pro processor
Santa Rosa motherboard
2 GB DDR2 RAM
120 GB HDD 5400rpm hard disk

---

### Post by rleon on 2007-07-29
I am not an expert but Santa Rosa is based on the 965 chipset.I do not know if that particular version is supported by the kernel in Feisty, but I think you should begin with Serial Ata configured as AHCI.

---

### Post by mike24hockey on 2007-07-29
I have tried booting both the graphical CD and the alternate CD with SATA configured as AHCI - the graphical doesn't get past its checklist, and the alternate CD cannot find my hard disk driver

---

