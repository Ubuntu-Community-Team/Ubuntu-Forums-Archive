---
title: "Installation errors, really annoying"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by feardotcom on 2009-06-11
Ok, heres the deal, im trying to install linux on my other pc. The cd is good, because i used the same cd to install on my laptop. Heres what its doing.

After install, it says restart, i restart
It comes up and saying nothing to boot from.
I looked in bios the boot priority is set fine, and it sees the hard drive, but for some reason the machine wont boot to linux from the hard drive, it only boots to windows.

At first i thought it might a grub issue, but i didn't see anything in the install options for grub, or boot loader period.

Any ideas?

AMD Athlon 64 x2 1.9ghz
MSI K9N6GM series Motherboard
2gb ram
8800gtx
trying to install onto a 80gb sata

---

### Post by Therion on 2009-06-11
Do you want to *dual-boot* (Ubuntu & Windows), or do you want Ubuntu as the sole OS on the drive?

---

### Post by feardotcom on 2009-06-11
sole os

---

### Post by feardotcom on 2009-06-11
I got it, it was a under the adnacned tab it was loading the bootloader in hda instead of hdb

---

