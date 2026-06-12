---
title: "Second hard drive size is wrong"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by power-coder on 2009-01-19
I have added a second 100gb drive to my Ubuntu Server 8.10 machine, in Webmin under 'Partitions on local disks' the drive shows a total size of 93.16 GB which is what I am expecting.  

The problem is that when I attempt to create a partition on the drive (ext3 or reiserfs) I can only ever get a size of ~46gb.  

From the command line when I run fdisk it reports the following:

```
Disk /dev/sda1: 49.0 GB, 49039087104 bytes
255 heads, 63 sectors/track, 5961 cylinders, total 95779467 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48ef5d37
```

Is there something that I'm missing to make this drive able to use all the available space on the disk?

Thanks,
Wally

---

### Post by power-coder on 2009-01-21
I managed to fix this by installing the drive into another machine and using a disk tool to completely wipe the drive.  I`m guessing that the partition tables on the drive had somehow gotten corrupted.  

Feel free to consider this question closed.
Thanks.

---

