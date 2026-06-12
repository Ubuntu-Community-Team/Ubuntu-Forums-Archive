---
title: "rename hdd's, auto mount"
date: 2008-09-25
forum: Hardware
---

### Post by chrisneedshelp on 2008-09-25
I currently have a laptop that I just wiped, and reinstalled XP and Ubuntu 8.04.  It is one physical drive with four partitions

0.xp
1.empty ntfs for media
2.ubuntu 
3.swap(ext3)

I would like to have both 0/1 auto mount when starting on ubuntu, and also change the names from the drive size to 'WinXP' and 'Media' respectively.  

Worst part is I've done this before but simply can't remember how, and was unable to find another post addressing this.

---

### Post by IcarusR on 2008-09-27
You need to create a mount point within your filesystem. 

```
mkdir /home/andy/WinXP /home/andy/Media
```

Then create an entry in /etc/fstab read man fstab.

You will need to know which partition of which drive each is.

```
sudo fdisk -l
```

Which will give you something like this ..

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc423cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2590    20804143+   7  HPFS/NTFS
/dev/sda2            9459        9729     2176807+  82  Linux swap / Solaris
/dev/sda3            2591        9458    55167210   83  Linux

Your line in /etc/fstab would need to look something like

```
/dev/sda1 /home/andy/Media NTFS            0 0 
```

Above will not nescessarily work but is an example of how to add the line.
You can add numerous options between NTFS & 0 0  
As said earlier read fstab manpage & google for help.

Of course do not blame me if you manage to fubar your system in the process. 
Always backup important system files before editing them !!

---

