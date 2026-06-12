---
title: "Quad-Boot PC"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Zipster90 on 2009-06-05
Hello. We're trying to set up a computer at my job that will boot four different OS systems off of four separate partition on one hard drive. I currently have installed XP, Vista, Windows 7 and Ubuntu. My problem is that GRUB will only detect my XP and Ubuntu installations. I have tried to edit the menu.lst file in GRUB, but haven't been able to get my Vista and 7 partitions to boot.

Does anyone know how to properly configure the menu.lst file for this kind of set up? Thanks.

---

### Post by Mark Phelps on 2009-06-06
If you installed the MS Windows OSs in the "right" order, you did XP, then Vista, then Seven -- which will result in the bootmanager files and directories being written to the XP partition, and an MS Windows boot menu listing all three OSs.

You then point GRUB to that partition, it will hand off control to the MS Windows loader (in this case Seven), which will render the boot loader menu and allow you to choose among the three MS Windows OSs.

You need to find which partition XP was installed to and use that one.

---

### Post by Soul-Sing on 2009-06-07
A harddisk can only contain 4 primairy partitions. So make an extended partition, which can contain unlimited logical partitions.
linux can be installed on logical and primairy partitions....
Then you need a tool to partition: the gparted iso, burn it, and it runs like a live-cd!
1) make an extended primairy partition which you divide into the deisired number of logical partitions.
Logical partitions begins with the 5 number, because the first 4 are reserved for the primairy partitions.
You need 1 swap for all linux systems.
BSD systems and windows can only be installed on primairy partitions!!

good luck

---

