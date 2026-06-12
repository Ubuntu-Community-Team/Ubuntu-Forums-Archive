---
title: "Installation on unallocated partition"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by evar on 2009-10-30
I want to install 9.10 over 9.04 but installation and gparted says that the whole disk is unallocated.

```
fdisk -l

Disk /dev/sdb: 250.1 GB
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3fff3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22382   179783383+   7  HPFS/NTFS
/dev/sdb2           22383       25035    21310222+  83  Linux
/dev/sdb3           25036       25156      971932+   f  W95 Ext'd (LBA)
/dev/sdb4           25157       30402    42138145    7  HPFS/NTFS
/dev/sdb5           25036       25156      971901   82  Linux swap / Solaris
```sdb2 is ext4 partition with 9.04, I want to format it. 
Current ubuntu and all logical disks works fine though, looks like partition table or something else is broken. How to fix it? fsck /dev/sdb does nothing.

---

### Post by macogw on 2009-10-30
Are you using the live or alternate installer?  If Live, make sure you choose Manual partitioning.  In both cases, you want to select sdb2 and tell it:
Use as: ext4 (or ext3, your choice)
Mount point: /
Format: Yes

That should be all you need to do.

---

### Post by JBAlaska on 2009-10-30
Do you by chance have 2 or more physical drives in your system..seems like you should have a sda if you have a sdb. Remember on the upper left of gparted there is a drop down that allows you to select your physical HD's.

---

### Post by evar on 2009-10-30
> **macogw said:**
> Are you using the live or alternate installer?  If Live, make sure you choose Manual partitioning.  In both cases, you want to select sdb2 and tell it:
Use as: ext4 (or ext3, your choice)
Mount point: /
Format: Yes

That should be all you need to do.

I'm using live installer and there is no sdb partitions because as I said disk is unallocated.

> **JBAlaska said:**
> Do you by chance have 2 or more physical drives in your system..seems like you should have a sda if you have a sdb. Remember on the upper left of gparted there is a drop down that allows you to select your physical HD's.

Yes, drop down is on upper right actually %)

I made screenshot in live installation. 22 gb drive is sdb2 partition with ubuntu 9.04. Installation can only offer to format and use whole sdb.

380kb

[[IMG]http://rghost.ru/568783/thumb.png[/IMG]]("http://rghost.ru/568783.view")

---

### Post by evar on 2009-10-30
So nobody know?

---

### Post by macogw on 2009-10-31
There obviously is an sdb2 if fdisk says there is.  And you just said sdb2 is ext4 with Linux on it and that you want to replace it... Just ignore GParted and use the installer's built-in partitioner.  It has a manual option.  Use the settings I mentioned before if you want to re-use that partition for your install.

---

### Post by evar on 2009-10-31
Manual partitioner in installation can't see sdb partition table too. Look at screenshot, there is no sdb2.

So what I need now is the program that can fix partition table for linux or windows. On the windows there is Partition Table Doctor but it does not work on vista/7 even with compatibility. I wonder maby fixboot fixmbr will help?

---

### Post by terryscott on 2009-10-31
Try testdisk in Synaptic. Worked for me in recovering XP system disk.
One later problem I had was with an overheating disk. At switch on, all was ok. I could boot to it, run system with it but, on re-boot, it was unusable.
Both xp's diskpart and gparted then said it was empty. Shut down, let it cool then all was ok.

---

