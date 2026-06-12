---
title: "Cannot boot into Ubuntu"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by normanlee on 2009-01-03
Hi, very new to Linux/Ubuntu. Had just installed Ubuntu onto a PC using the official Ubuntu CD (8.04.1 LTS) and following the onscreen instructions. After the installation completes and the system reboots, it went directly into the WinXP OS without asking for which OS to be loaded. Please advise how I can get the OS selection page turn on.

---

### Post by Herman on 2009-01-03
Try going into your BIOS settings and changing the hard drive boot order. (Not the floppy drive/CD-ROM/hard drive one, the other one, where you switch hard drive 1 to be hard drive 2 ...).

---

### Post by normanlee on 2009-01-03
Hi Herman, my Ubuntu partition is sitting on the same harddisk as my WinXP. I have 3 partitions on this harddisk, 1st for WinXP, the 2nd for WinXP data and the 3rd (20Gb) for Ubuntu OS (and data).

---

### Post by Herman on 2009-01-03
If you have another hard disk or disks and especially if there's a mixture of IDE and SATA or if you have IDE drives with the jumpers set funny, GRUB might install the MBR code to the wrong hard disk's MBR. If so, it will probably be configured wrong as well.
The easiest thing to do is just try switching the hard disk around in your BIOS until everythig works. 
Unless I'm guessing wrong. :)

---

### Post by normanlee on 2009-01-03
Hi Herman, thanks, it worked ..... somehow GRUB ended on the IDE drive :D

---

### Post by Herman on 2009-01-03
Okay, thanks for the feedback, I'm glad it worked. :)

---

