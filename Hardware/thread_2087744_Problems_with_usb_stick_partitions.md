---
title: "Problems with usb stick partitions"
date: 2012-11-24
forum: Hardware
---

### Post by caesar753 on 2012-11-24
Hello everybody,
I have a strange problem with my usb stick: the partitions over it seem to be messed up, and i cannot delete nor format them, this is my fdisk output

```

Disk /dev/sdb: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70707573

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1701998450  3638285201   968143376    d  Unknown
/dev/sdb2   ?  1701995885  2246105740   272054928    a  OS/2 Boot Manager
/dev/sdb3   ?  1769087090  3538458322   884685616+  6f  Unknown
/dev/sdb4   ?  2885681152  2885734849       26849    a  OS/2 Boot Manager

Partition table entries are not in disk order

Command (m for help): v
Partition 1: previous sectors -656682095 disagrees with total 2868010
Partition 2: previous sectors -2048861556 disagrees with total 2772955
Warning: partition 1 overlaps partition 2.
Partition 3: previous sectors -756508974 disagrees with total 2772657
Warning: partition 1 overlaps partition 3.
Warning: partition 2 overlaps partition 3.
Partition 4: sector 0 greater than maximum 62
Partition 4: previous sectors -1409232447 disagrees with total -125
Warning: partition 1 overlaps partition 4.
Warning: partition 3 overlaps partition 4.
Total allocated sectors 1459216974 greater than the maximum 7897088

Command (m for help): 

```

does anybody know if there is a way to fix this?

Thanks in advance!

---

### Post by PapaNerd on 2012-11-24
Since you seem willing to format it and sacrifice data recovery, I've had success with the dwipe tool ([http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe))

---

### Post by caesar753 on 2012-11-25
Thanks for the answer!
What should this program do?

---

### Post by PapaNerd on 2012-11-25
The dwipe program writes patterns to every location on the drive, and can optionally (using the -z switch) write zeros to the entire drive as its final pass.  You end up with a drive that has no data on it, including the MBR and all previous partitions.  Once the disk has been wiped, you can use a partitioning tool (fdisk, gparted, etc.) to establish new partitions.  The added benefit of using the tool is that since it exercises the entire drive, any new bad blocks encountered will be written to the bad block table.

---

### Post by Tr3dgo on 2012-11-25
Could you use date dump for this 
eg.

# dd bs=512 if=/dev/zero of=/dev/sdb

which would also completey wipe the device. Not sure how lnog this takes though as never fully utilised it.

---

