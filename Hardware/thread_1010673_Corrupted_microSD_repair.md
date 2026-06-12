---
title: "Corrupted microSD repair?"
date: 2008-12-14
forum: Hardware
---

### Post by wolftousen on 2008-12-14
Ok, so somehow I screwed up my microSD 1gb card when i tried to format it for use as a boot drive.  Whenever I plug it in (through the usb dongle i have) /dev/sdb appears (ls /dev before and after plugging in found this out...)

mounting that to a folder with usbfs gives me 5 folders 001 002 003 004 005 and a file named devices... have found no use for this...

When i run sfdisk /dev/sdb output is:
Checking that no-one is using this disk right now ...
BLKRRPART: Input/output error
OK

Disk /dev/sdb: 8 cylinders, 64 heads, 32 sectors/track
read: Input/output error

sfdisk: read error on /dev/sdb - cannot read sector 0
 /dev/sdb: unrecognized partition table type
Old situation:
No partitions found
Input in the following format; absent fields get a default value.
<start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
Usually you only need to specify <start> and <size> (and perhaps <type>).

/dev/sdb1 :
/dev/sdb1          0+      7       8-      8191+  83  Linux
/dev/sdb2 :
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3 :
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4 :
/dev/sdb4          0       -       0          0    0  Empty
New situation:
Units = cylinders of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+      7       8-      8191+  83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Do you want to write this to disk? [ynq]  

When i run fsck -a /dev/sdb1 output is:
fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdb1
/dev/sdb1:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

i've tried dd if=/dev/zero of=/dev/sdb1 bs= 3000000 and it completes but doesn't fix anything.

Any suggestions?

---

### Post by wolftousen on 2008-12-14
ok, i think i made some headway, but am now lost again.

I ran parted /dev/sdb1 mklabel msdos and it succeeded
I then ran parted /dev/sdb1 mkpartfs primary fat32 0 512 and it succeeded

But now if I do fdisk -l /dev/sdb1 i get this:
You must set cylinders.
You can do this from the extra functions menu.

Disk /dev/sdb1: 0 MB, 0 bytes
4 heads, 32 sectors/track, 0 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x000b1573

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1        7813      500016    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 3, 32) logical=(7812, 3, 32)

any suggestions on what to do next?

---

