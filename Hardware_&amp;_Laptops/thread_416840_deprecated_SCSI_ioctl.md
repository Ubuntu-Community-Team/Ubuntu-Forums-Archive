---
title: "deprecated SCSI ioctl"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by wireless on 2007-04-21
Hello All
 specs: thinkpad x60, trying to install ubuntu 7.04
when i get to the partitioning part the installer crashes.
dmesg shows >  "program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO"

heres my partition table

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1        9667    73082519+   f  W95 Ext'd (LBA)
/dev/sda4            9668       10337     5065200    b  W95 FAT32
/dev/sda5               1        6570    49664916   83  Linux
/dev/sda6            6570        6773     1534176   82  Linux swap / Solaris
/dev/sda7            6773        7451     5124703+   7  HPFS/NTFS
/dev/sda8            7451        9667    16755763+   7  HPFS/NTFS


Im totaly clueless after searching for solution in google and havnt found an answer..
apriciate any assistance
thnx in advance! ;)

---

### Post by feydreva on 2007-11-12
I do have the exact same issue... any idea ?

---

### Post by feydreva on 2007-11-12
i am trying to install Ubuntu 7.10

---

