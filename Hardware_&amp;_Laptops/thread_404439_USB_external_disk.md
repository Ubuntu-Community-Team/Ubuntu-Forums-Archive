---
title: "USB external disk"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by alkat on 2007-04-08
Hello,
I'm trying to make Ubuntu Edgy recognize an external hard disk connected through a USB port. It seems that the disk is recognized by the system, but it is not possible to mount it or partition it. 

I'm posting the output of some commands in case someone can help.

Part of the output of lshw:
```
description:    SCSI Disk
product:        HDT725032VLAT80
vendor:         Hitachi
physical id:    0.0.0
bus info:       scsi@1:0.0.0
logical name:   /dev/sda
version:        0811
size:   298GB
capabilities:   partitioned partitioned:dos
```


```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=be678408-ff19-4772-8cf9-3f74ed5ceae7 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=9ad6c580-d391-4fd7-b449-8c01a8e674ad none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


```
$ sudo  dmesg | grep sda
Password:
[17179595.876000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179595.892000] sda: test WP failed, assume Write Enabled
[17179595.892000] sda: assuming drive cache: write through
[17179595.904000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179595.920000] sda: test WP failed, assume Write Enabled
[17179595.920000] sda: assuming drive cache: write through
[17179595.920000]  sda:
[17179595.940000] sd 0:0:0:0: Attached scsi disk sda
[17182979.052000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17182979.068000] sda: test WP failed, assume Write Enabled
[17182979.068000] sda: assuming drive cache: write through
[17182979.080000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17182979.096000] sda: test WP failed, assume Write Enabled
[17182979.096000] sda: assuming drive cache: write through
[17182979.096000]  sda:
[17182979.120000] sd 1:0:0:0: Attached scsi disk sda
```

```
$ sudo lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 003: ID 03f0:8604 Hewlett-Packard
Bus 002 Device 004: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

---

### Post by quux on 2007-04-09
Is the disk already partitioned?

According to the dmesg output, no partitions are found. What's the output of "sudo fdisk -l /dev/sda"?

---

### Post by alkat on 2007-04-09
> **quux said:**
> Is the disk already partitioned?

According to the dmesg output, no partitions are found. What's the output of "sudo fdisk -l /dev/sda"?


Hey, thanks for replying! :)

Unfortunately I don't have the disk with me - I'm trying to figure out how to install that disk on a friend's PC running Ubuntu. Right now I can't do any test, but I'll have a look at the PC and disk tomorrow.

I was looking for some general suggestion to solve this problem and I think that yours could be a good one: the disk is new and was never used before, therefore it is not formatted nor partitioned. 

I've tried to tell my friend to format it with the comand sudo mkfs.ext3 /dev/sda but he didn't succeed (I was helping him through the phone...). Do you think that could help?

What else could I use to partition it? Maybe Gparted? Or even I could use Windows to format it in FAT32 and then see if Ubuntu sees he disk.

What would yo try if you were me?

a.

---

### Post by quux on 2007-04-09
I'd say it depends how computer-savvy your friend is. :)

If your friend feels comfortable working on the command line, I'd propose to use cfdisk for partitioning which comes with the ubuntu base system. A "sudo cfdisk /dev/sda" should bring up cfdisk. Using cfdisk is easy: just add a new partition (type: linux), write, quit. Then try formatting the newly generated partition (e.g. sda1) using the command you mentioned above.

Since I've never really used gparted, I can't comment on that one.

If your friend has just recently stated using Linux and has a Windows-Box available, your idea of partitioning/formatting the disk under Windows seems to be the best solution IMHO. For Windows/Linux interoperabiity, it might be worth to consider using FAT32 as filesystem, especially if the disk is to be used on different computers/operating systems. But you'll run into problems when you try to format a partition >32Gb with FAT32 under windows. (h2format, [ftp://ftp.heise.de/pub/ct/ctsi/h2format.zip]("ftp://ftp.heise.de/pub/ct/ctsi/h2format.zip") can help here).

HTH

---

### Post by alkat on 2007-04-09
> **quux said:**
> I'd say it depends how computer-savvy your friend is. :)

If your friend feels comfortable working on the command line, I'd propose to use cfdisk for partitioning which comes with the ubuntu base system. A "sudo cfdisk /dev/sda" should bring up cfdisk. Using cfdisk is easy: just add a new partition (type: linux), write, quit. Then try formatting the newly generated partition (e.g. sda1) using the command you mentioned above.

Since I've never really used gparted, I can't comment on that one.

If your friend has just recently stated using Linux and has a Windows-Box available, your idea of partitioning/formatting the disk under Windows seems to be the best solution IMHO. For Windows/Linux interoperabiity, it might be worth to consider using FAT32 as filesystem, especially if the disk is to be used on different computers/operating systems. But you'll run into problems when you try to format a partition >32Gb with FAT32 under windows. (h2format, [ftp://ftp.heise.de/pub/ct/ctsi/h2format.zip]("ftp://ftp.heise.de/pub/ct/ctsi/h2format.zip") can help here).

HTH

Well, tomorrow I'll be working on that PC so my friend will not have to bother about running exotic command line programs... :)

I hope the only problem is that the disk needs to be formatted. Do you think there could be any other problem?

I believe that an USB disk is just like a pendrive so there shouldn't be any compatibility issues, right?

.a.

---

