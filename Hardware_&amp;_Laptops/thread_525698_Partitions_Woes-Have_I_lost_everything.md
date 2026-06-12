---
title: "Partitions Woes-Have I lost everything?"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by Dylnuge on 2007-08-14
Well, I was working on Ubuntu Linux 7.04, have had it up for months, but did not love the size of its parts-too much space on the win part, not enough on the extended block that contained all my Linux parts. I rebooted into Windows to use this software-since NTFS is not journaled, I use Norton Partition Magic 8 to resize it. So I started the resize operation, and halfway through, an error came up. The error was something like "file attribute missing" or something similar. Norton crashed, and that was it. Went into Linux and switched to root, ran some commands, and here is what I got:

Results of fdisk -l:
```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        8954    71882842+   7  HPFS/NTFS
/dev/sda3           11521       11977     3670852+  db  CP/M / CTOS / ...
/dev/sda4            8955       11520    20611395    f  W95 Ext'd (LBA)
/dev/sda5            8955        9077      987966   83  Linux
/dev/sda6            9078        9332     2048256   82  Linux swap / Solaris
/dev/sda7            9333       10426     8787523+  83  Linux
/dev/sda8           10427       11520     8787523+  83  Linux
```

So far, so good. Unfortunately, /media/sda2 was empty-that meant the usual mount was not there. So I tried sudo mount /dev/sda2 /mnt/win (an emergency mount directory for recovery) and got this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Since the system is windows, I assumed there was nothing in the syslog. Since I had done partition changes and the like before, I made a very dumb decision to not bother with a three hour backup. Well I do not need any of the files on there extremely (thankfully, most of the files I use most often have been moved to Linux), there would be some serious problems if I cannot get it back, and much of my programs, etc, would require manual (phone) deactivation so that I could reinstall.

Any suggestions are helpful. Please help!

Thanks,
Dylan

PS: I don't know a ton about partitions. I know linux uses a Journaled File System, does this mean that I don't need to worry about losing my (Linux) files if I partition through gparted?

---

### Post by Dylnuge on 2007-08-14
Please help. If I don't get a reply soon, I will assume it is hopeless.

At the least, can someone answer the question in the PS. That would be helpful.

---

### Post by el.motar on 2007-08-16
I would not call myself an expert on linux data recovery, but if I were you would do the following.

Try these programs first, testdisk and photorec.

They are available in the ubuntu reps and have help me with a corrupted partition table.

The first one to run would be testdisk.

Hope you have some luck with this.
Just a word about you PS part.
Don´t partition with gparted as I am pretty sure it will delete your data.
ATB

---

### Post by BriskBean on 2007-09-12
For recovery the data from Linux you can even try Stellar Phoenix Linux [Data recovery]("http://www.stellarinfo.com") software for Ext2 & Ext3 file system volumes. The software scans the disk trying to find previously existing partitions and restore the file(s), allowing Linux Partition Data Recovery 
Get the Trial version: [http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm)

---

