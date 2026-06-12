---
title: "Not sure why this is happening..."
date: 2008-08-03
forum: General Help
---

### Post by MistaHardkill on 2008-08-03
First and foremost, my specs are as follows:

CPU: Intel Core 2 Quad Q6600
Mobo: Gigabyte GA-EP45-DS3R
RAM: 4GB OSZ 800mhz
HD: 2xWD Caviar 500gb
GPU: ATI Radeon HD4870


Now, I'll tell you what I'm trying to do:
I'm trying to dual boot Vista SP1 (x86), and Kubuntu 8.04. With Vista installed first. I've followed guide after guide, which all included EasyBCD (including the one from the official EasyBCD site). Every outcome ends in a "Cannot boot from harddisk" error. Or "insert systemdisk". Something along those lines. I'm not sure why this is happening....Vista still boots perfectly, so thats good, but I want my Kubuntu working. 

Now the system is obviously there, because it gets to grub (although grub appears after the first error of "cannot boot from harddisk"). It shows all the options in grub, but none will boot. I've tried putting the swap at the beginning, end, and even leaving the swap out completely. No avail. I'm installing from an actual Kubuntu disk (shipit), and am installing the x86 version. I've also tried burning different ones from downloaded ISO's, and also tried Ubuntu itself, but still nothing. 

I know theres absolutely nothing wrong with the hard drive, as I can boot XP from it in a dual boot, no problem.

Quick note: I had to go into my bios and change SATA mode to AHCI before kubuntu would even see the drives...if that matters.

What am I doing wrong?

---

### Post by sayakb on 2008-08-03
Use the Supergrub disk to reconfigure grub: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by MistaHardkill on 2008-08-03
I've tried that too, I'm afraid...

---

