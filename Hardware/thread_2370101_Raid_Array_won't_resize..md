---
title: "Raid Array won't resize."
date: 2017-08-30
forum: Hardware
---

### Post by rsteinmetz70112 on 2017-08-30
I have a RAID 1 array using software raid with Ubuntu 16.04 LTS.  I am trying to resize it. It was on two drives which were too small. I have added two new larger drives, created a partition on each drive and added the new drives to the array. I then removed each of the old drives in turn and allowed the new drives to sync. The array is now working but as expected it is the same size as the old array.

The underlying partition is the new size I selected but the array shows up as the old size.

I need to expand the array to fill the new partition, but it's not working as I expect.

mdadm shows this on the array:

```
root@thelma:~# mdadm --detail /dev/md1
/dev/md1:
           Version : 0.90
  Creation Time : Sun Mar 11 19:06:41 2007
      Raid Level : raid1
      Array Size : 312567552 (298.09 GiB 320.07 GB)
  Used Dev Size : 312567552 (298.09 GiB 320.07 GB)
  Raid Devices : 2
  Total Devices : 2
  Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Aug 30 10:43:47 2017
    State : clean
    Active Devices : 2
    Working Devices : 2
    Failed Devices : 0
    Spare Devices : 0

         UUID : a5865e80:27a899df:bfaac05b:eff3fc62
         Events : 0.16317296

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2
```

parted shows this information:

```
root@thelma:~# parted /dev/sda unit kB p
Model: ATA TOSHIBA HDWD110 (scsi)
Disk /dev/sda: 1000204886kB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start       End          Size         Type     File system  Flags
 1      32.3kB      80023749kB   80023717kB   primary               boot, raid
 2      80024175kB  551156711kB  471132537kB  primary  reiserfs     raid
```

mdadm returns this error

```
root@thelma:~# mdadm --grow /dev/md1 --size=471132537
mdadm: Cannot set device size for /dev/md1: No space left on device
```

Resizing the files system returns this error

```
resize_reiserfs -f /dev/md1
resize_reiserfs 3.6.24

/dev/md1 already is of the needed size. Nothing to be done
```

I'm obviously missing something can someone point out my error.

---

### Post by slickymaster on 2017-08-30
*Thread moved to **Hardware**.*

---

### Post by rsteinmetz70112 on 2017-09-16
I solved this apparently when uing the resizing a raid array using the size parameter causes problems. I wasa attempting to be careful because I didn't want the array to cause he partition to grow or take over the rest of the drive. simpy using mdadm --grow /dev/mdX will fill the current partition. I had asimilar problme with resize_reiserfs but omiting th siz t filled the array just fine. I was overthing it.

---

