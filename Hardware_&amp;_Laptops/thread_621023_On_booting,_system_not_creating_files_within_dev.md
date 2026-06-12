---
title: "On booting, system not creating files within /dev/"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by mgtsol on 2007-11-23
Hi,

From my main Ubuntu desktop machine I'm trying to access partitions on a laptop hard drive I have connected via one of those 3.5inch to 2.5inch IDE connectors.

The system can see the disk (/dev/sdc):
....
<snip>

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1785    14337981    7  HPFS/NTFS
/dev/sdc2            1786        5511    29929095    7  HPFS/NTFS
/dev/sdc3            5512        7215    13687380   83  Linux
/dev/sdc4            7216        7296      650632+   f  W95 Ext'd (LBA)
/dev/sdc5            7216        7296      650601   82  Linux swap / Solaris
....

But when I tried to mount the NTFS partition (I have already mounted a separate NTFS partition on the primary disk so it's not a driver problem) I got:

mark@mark-desktop:~$ sudo mount /dev/sdc2 /lincoln -t ntfs
mount: special device /dev/sdc2 does not exist

So following advice I got in a few other threads I tried:

mark@mark-desktop:~$ sudo ls -apl /dev/sd*
brw-rw---- 1 root disk 8,  0 2007-11-23 13:52 /dev/sda
brw-rw---- 1 root disk 8,  1 2007-11-23 13:52 /dev/sda1
brw-rw---- 1 root disk 8,  2 2007-11-23 13:52 /dev/sda2
brw-rw---- 1 root disk 8,  3 2007-11-23 13:52 /dev/sda3
brw-rw---- 1 root disk 8,  5 2007-11-23 13:52 /dev/sda5
brw-rw---- 1 root disk 8, 16 2007-11-23 13:52 /dev/sdb
brw-rw---- 1 root disk 8, 17 2007-11-23 13:52 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2007-11-23 13:52 /dev/sdc

....

So for some reason when my system boots it can see the partitions on the disk sdc but doesn't create the files for them within /dev/sdc

Any suggestions? :confused:

---

### Post by mgtsol on 2007-11-23
From /var/log/messages:

mark@mark-desktop:~$ cat /var/log/messages | grep sdc | more
Nov 23 14:33:47 mark-desktop kernel: [   37.979236] SCSI device sdc: 117210240 5
12-byte hdwr sectors (60012 MB)
Nov 23 14:33:47 mark-desktop kernel: [   37.979250] sdc: Write Protect is off
Nov 23 14:33:47 mark-desktop kernel: [   37.979272] SCSI device sdc: write cache
: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 14:33:47 mark-desktop kernel: [   37.979333] SCSI device sdc: 117210240 5
12-byte hdwr sectors (60012 MB)
Nov 23 14:33:47 mark-desktop kernel: [   37.979345] sdc: Write Protect is off
Nov 23 14:33:47 mark-desktop kernel: [   37.979368] SCSI device sdc: write cache
: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 14:33:47 mark-desktop kernel: [   37.979372]  sdc:<3>ata2.00: exception E
mask 0x0 SAct 0x0 SErr 0x0 action 0x2
Nov 23 14:33:47 mark-desktop kernel: [   39.041064] sdc: Current [descriptor]: s
ense key: Aborted Command
Nov 23 14:33:47 mark-desktop kernel: [   39.041091] end_request: I/O error, dev 
sdc, sector 0
Nov 23 14:33:47 mark-desktop kernel: [   39.403953] SCSI device sdc: 117210240 5
12-byte hdwr sectors (60012 MB)
Nov 23 14:33:47 mark-desktop kernel: [   39.404020] Dev sdc: unable to read RDB 
block 0
Nov 23 14:33:47 mark-desktop kernel: [   39.404109] sdc: Write Protect is off
Nov 23 14:33:47 mark-desktop kernel: [   39.438006] sd 1:0:0:0: Attached scsi di
sk sdc
Nov 23 14:33:47 mark-desktop kernel: [   39.440248] SCSI device sdc: write cache
: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 14:33:47 mark-desktop kernel: [   39.448251] SCSI device sdc: 117210240 5
12-byte hdwr sectors (60012 MB)
Nov 23 14:33:47 mark-desktop kernel: [   39.452211] sdc: Write Protect is off
Nov 23 14:33:47 mark-desktop kernel: [   39.460214] SCSI device sdc: write cache
: enabled, read cache: enabled, doesn't support DPO or FUA

---

