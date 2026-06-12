---
title: "Unable to boot to Windows bootable discs"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by pmurphydc on 2009-04-10
I've been running Ubuntu on a work laptop but the time has to come switch back to XP, at least on this one computer. I'm unable to boot to ANY Windows install disc or bootable discs except Linux discs. BIOS settings are not an issue. I have only one hard drive with two partitions, one being a swap. I'm not very experienced here (obviously) and can't figure out why I wouldn't be able to boot to an XP disc. Does the GRUB bootloader have any effect on that?

---

### Post by zvacet on 2009-04-11
> Does the GRUB bootloader have any effect on that?

I don´t think so.If you set in BIOS to boot from CD you should start new installation process.Windows will recognize that you have already partitions and you can delete them with Windows install disc and format disc as you wish.

> BIOS settings are not an issue.

Maybe you choose AHCI mode instead of IDE.If you try to install Windows XP you will have problems if AHCI mode is active.

---

### Post by pmurphydc on 2009-04-11
Yeah. All of those things have been checked. Went so far as to restore defaults and save settings. Took the drive out and formatted on another computer. Even reinstalled Ubuntu. There's never any indication that an attempt to boot to CD was made. It's so weird. I read some things saying having multiple partitions and a linux MBR could prevent XP CD boots? Gparted shows the following partitions:

SDA1 - ext3
SDA2 - extended
     >SDA5 - linux-swap (shows up under SDA2)

---

### Post by zvacet on 2009-04-11
Do you have any unallocated space on your disc?You need one primary partition to install Windows.What is on sda2?Is just swap there.If it is then delete that partition and make one primary and see if you can boot Windows.If you want to delete all Ubuntu partitions do it with live Cd or with [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by nstolar on 2009-04-12
Pentium E6600 LGA775, 2Gb's SKILL RAM DDR2 pushed to 1066, RAID 0+1
I tried the Sample or test run of Ubuntu The first selection, There was no problems, it acted a bit unstable so I did not spend too much time, but it ran fine, but only one monitor, and would not read the RAID Disk. The O/S left a marker before the file directory so that windows would not try to read it. It should be easy enough to go back and dump them tomorrow. I believe the simplest way will be to set the BIOS to boot from a drive just for Ubuntu and change the BIOS to run windows if ya must. I am running a Celron 2.6, 1Gb RAM, with a I am using a NIVIDA Graphics Card and needed to use one of there Drivers. It is: (Nvidia Driver 96).Made a 100% improvement That will be a help for someone I am sure, if I get it to the right place.

Later, nstolar

---

