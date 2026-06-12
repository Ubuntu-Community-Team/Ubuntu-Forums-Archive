---
title: "ubuntu removing"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by mohd on 2009-10-02
I have ubuntu alone on my laptop , but i need to install xp 
so i want to remove ubuntu and replace it by xp , i tried formatting the hdd but xp couldn't read my hdd at all only vista and seven could

my hdd is sata , any help ?

---

### Post by dmizer on 2009-10-02
Use a [partitioning tool]("http://gparted.sourceforge.net/livecd.php") to remove all the partitions on the hard drive.

Is your XP disk a full install CD, or just a recovery CD?

---

### Post by mohd on 2009-10-02
a full install , and got the recovery option as well i believe

i guess the problem is about the partition extension ext3 unrecognizable by the win xp cd

---

### Post by ElevenWarrior on 2009-10-02
yes windows can not recognizes anything that is not windows.... unlike like linux which recognizes both windows and linux.

---

### Post by Moses Palmér on 2009-10-02
The problem is that you have a SATA drive. Windows XP cannot install to a SATA/SCSI drive without external drivers.

Unfortunately, the only way to provide those drivers is by floppy.

If you actually have a floppy drive, you have to find the drivers and then, during the first phase of the installation, you have to press, I think, F6 to load them.

For this reason alone, I used to keep a floppy drive in a box; even five years ago, when I still used Windows and had to perform the occasional formatting, floppys were a thing of the past.

---

