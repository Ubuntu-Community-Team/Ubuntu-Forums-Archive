---
title: "Gparted recognizes my whole HDD as unpartitioned"
date: 2013-11-22
forum: Hardware
---

### Post by salman-m on 2013-11-22
Hi, 
I searched the forum but found no answer for my problem.

MY QUEST:
How can I make GParted recognize my paritions not as unpartitioned?

CURRENT SITUATION:
I have a triple-boot Laptop (Trisquel 6, Ubuntu 13.10, and Windows 7) which works correctly but W7 doesn not boot. My problem is that GParted cannot recognize my partitions and shows my whole HDD as unpartitioned either in Trisquel or Ubuntu (The screenshot is attached).

HOW DID IT HAPPEN?
I was working with GParted and wanted to change the partition type of Trisquel home that mistakenly deleted the "home" partition of Trisquel. After that I created a partition and introduced it to the system as the home partition of Trisquel by playing with UUIDs, etc.

MORE INFO.?
I pasted the output of "$ sudo boot_info_script" here:
[http://paste.ubuntu.com/6459543/](http://paste.ubuntu.com/6459543/)

Thanks
Salman

---

### Post by coffeecat on 2013-11-22
You have a partition table irregularity, which is why Gparted shows "unallocated".  From your boot info pastebin:

> ```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   635,865,087   635,865,025   7 NTFS / exFAT / HPFS
/dev/sda2         635,865,088   636,889,087     1,024,000  83 Linux
/dev/sda3         636,891,134 1,250,263,039   613,371,906   5 Extended
Extended partition linking to another extended partition.
/dev/sda5         636,891,136   666,185,727    29,294,592  83 Linux
/dev/sda6         666,187,776   668,581,887     2,394,112  82 Linux swap / Solaris
/dev/sda7         753,940,480   762,218,495     8,278,016  83 Linux
/dev/sda8         762,220,544 1,045,463,039   283,242,496  83 Linux
/dev/sda9       1,045,478,133 1,250,242,559   204,764,427   7 NTFS / exFAT / HPFS
/dev/sda4         741,748,736   753,938,431    12,189,696  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4
```

Partition sda4, which is a primary/extended partition, is inside your sda3 extended partition. That is very wrong. Fortunately, fixparts should fix this:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by salman-m on 2013-11-23
Thank you. It could solve my problem by deleting home partition of Ubuntu :)

I just used the flag "s" to sort my partitions, in fixparts.

---

