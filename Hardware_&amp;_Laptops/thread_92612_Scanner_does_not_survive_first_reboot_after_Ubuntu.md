---
title: "Scanner does not survive first reboot after Ubuntu install"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by palladium on 2005-11-20
I have a HP printer/Copier/Scanner (model 1100A) that uses the parallel port only. Printing works fine. Scanning works (but slowly) if I use xsane after a fresh installation of Ubuntu (5.10) before a reboot. However, after rebooting Ubuntu, the scanner is not detected.  

When the scanner is working (ie, prior to any reboot after installing Ubuntu) if I open xsane > File > Info => it tells me
Device: “/par/HP_LaserJet_1100?device=/dev/parport0
Loaded backend: hpaio
Sane version: 1.0.15 “

Things I have tried:
Changing the BIOS so the parallel port is at 278 rather than 378
Booting from the Ubuntu live CD
Changing the parallel port from SPP to EPP or ECP in the BIOS
Installing the printer driver
Turning the printer off and on and resetting the printer
sudo /etc/init.d/hplip restart
Running xsane with sudo
Checked users are part of the scanner group
A different computer. Same behaviour on a Tecra 8100 laptop and a Pentium 4 desktop. 

After rebooting, none of these enabled the scanner to be detected. I am new to both Linux and Ubuntu and would appreciate any suggestions that may make the scanner work.
Thanks

---

### Post by palladium on 2005-12-08
Sorry to bump myself up like this but I am still hoping that someone may be able to throw some light on this problem. Any ideas would be welcome.
Thanks

---

