---
title: "Sata Hdd Nvidia"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by arulselvan.m on 2007-06-28
Hi,

Anyone tried installing ubuntu in SATA HDD if so please update the following how to do 

Either LIVE CD or Installation package of 7.04


Thanks,

Arulselvan

---

### Post by djgrandmarquis on 2007-06-28
Please be more specific. Ubuntu runs on dozens of configurations of SATA hardware and disks.

---

### Post by dabl on 2007-06-28
I'm running Ubuntu and Kubuntu on a system with 2 SATA and 1 PATA drives.  The only issue I've observed is that the installer will INSIST on putting Grub on the MBR of the PATA/IDE drive, rather than on a SATA drive, if there is a mix of drive types.  Resistance is futile -- don't waste your time fighting that one, if you happen to have a PATA/IDE drive in your system.  Otherwise, there was no problem -- it installs and runs great.  I experimentally took the IDE drive out, during the time I was fighting the placement of Grub, and if there's no IDE drive available then it seems happy to put Grub on a SATA drive.

---

### Post by tonymaro on 2007-06-28
My experience is that this depends a lot on your BIOS.  Better boards allow you to select the boot order of the drives.  Newer boards seem to fair much better at this.

---

