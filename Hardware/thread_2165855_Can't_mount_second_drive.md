---
title: "Can't mount second drive"
date: 2013-08-06
forum: Hardware
---

### Post by littlemissinuka on 2013-08-06
Hi, 

I have an Asus U500V which has two 128GB SSD drives. I wiped Windows off it today and installed Ubuntu 13.04 onto one of the SSD drives. The install was fine and I've booted into it. But it's not letting me mount the second SSD as a data drive. When I try to mount it, I get this: 

```
inuka@ulappy:~$ sudo mount /dev/sda test/
mount: unknown filesystem type 'isw_raid_member'
```

This is even after I've turned RAID off in the BIOS and I've uninstalled dmraid (as I saw on a previous post). 

The output of fdisk -lu is:

```
inuka@ulappy:~$ sudo fdisk -lu 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb19f8d36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   465568255   232784127+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   250069679   125034839+  ee  GPT

```


Can anyone help me turn this drive into a regular secondary data disk? 

Thank you!
Inuka.

---

### Post by oldfred on 2013-08-06
If drives are partitioned with gpt, fdisk will not work. You can use parted or download gdisk which is like fdisk but for gpt drives. gdisk is in the repository.

If drives were RAID, then you have to remove RAID meta-data from drive. Or if you have RAID then both drives are being used already?

If you are sure you do not have RAID.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by littlemissinuka on 2013-08-06
Thank you for the reply! 

Yes the drive is formatted using gpt, as I just realised when I tried to open it with gparted. It gives me the following error and exits before the GUI is fully started so I can't format it there. 

```
inuka@ulappy:~$ sudo gparted
======================
libparted : 2.3
======================
Invalid argument during seek for read on /dev/sda
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Backtrace has 10 calls on stack:
  10: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x2e) [0x7fe69a10f4ae]
  9: /lib/x86_64-linux-gnu/libparted.so.0(+0x412bb) [0x7fe69a1412bb]
  8: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x58) [0x7fe69a1156b8]
  7: /usr/sbin/gpartedbin() [0x472154]
  6: /usr/sbin/gpartedbin() [0x47c393]
  5: /usr/sbin/gpartedbin() [0x4ac087]
  4: /usr/lib/x86_64-linux-gnu/libglibmm-2.4.so.1(+0x413bd) [0x7fe698b823bd]
  3: /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6ceb5) [0x7fe6981abeb5]
  2: /lib/x86_64-linux-gnu/libpthread.so.0(+0x7f8e) [0x7fe697506f8e]
  1: /lib/x86_64-linux-gnu/libc.so.6(clone+0x6d) [0x7fe697230e1d]
Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:980 in function _parse_header() failed.
Aborted (core dumped)
```

I installed gdisk and it reads the drive and there are a number of recovery options. Do you have any idea which one I should go for? 

```
inuka@ulappy:~$ sudo gdisk
GPT fdisk (gdisk) version 0.8.5

Type device filename, or press <Enter> to exit: /dev/sda
Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): r

Recovery/transformation command (? for help): ?
b    use backup GPT header (rebuilding main)
c    load backup partition table from disk (rebuilding main)
d    use main GPT header (rebuilding backup)
e    load main partition table from disk (rebuilding backup)
f    load MBR and build fresh GPT from it
g    convert GPT into MBR and exit
h    make hybrid MBR
i    show detailed information on a partition
l    load partition data from a backup file
m    return to main menu
o    print protective MBR data
p    print the partition table
q    quit without saving changes
t    transform BSD disklabel partition
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Recovery/transformation command (? for help): 
```

I'm not entirely sure what the problem is. When I ask it to verify the disk in gdisk, I get the following. 

```
Recovery/transformation command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 250069680 sectors, needs to be 465568256 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Problem: partition 7 is too big for the disk.

Identified 6 problems!

Recovery/transformation command (? for help): 
```

Where should I go from here?

Thank you again!
Inuka.

---

### Post by oldfred on 2013-08-06
It looks like that is related to the RAID info?

Not sure if you should not remove RAID data, then run the gdisk repairs and if it looks ok the w command to write changes.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by littlemissinuka on 2013-08-07
Thank you again. I followed the recommended repairs and it works fine now! :D

---

