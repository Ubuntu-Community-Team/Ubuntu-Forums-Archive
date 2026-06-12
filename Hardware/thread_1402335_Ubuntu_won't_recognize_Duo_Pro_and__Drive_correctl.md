---
title: "Ubuntu won't recognize Duo Pro and  Drive correctly"
date: 2010-02-09
forum: Hardware
---

### Post by yedidyah on 2010-02-09
I am using lucid lynx alpha (but the problem exists in live cd 9.04) and I have a 64 bit system.

I got a Duo Pro Drive (by simpletech a fabrik company) case and installed a brand new (sealed) western digital 750GB hard drive in the Duo Pro Drive case.

From the beginning all "gparted" and "disk utility" see is an unallocated 8 GB hard drive. Until I hooked it directly into my system as a secondary hard drive.

Then I was able to format the 750GB drive and even place files on the drive it worked fine.

When I put it back into the Duo Pro case "gparted" and "disk utility" see is an unallocated 8 GB hard drive and Ubuntu doesn't recognize it to be used.

I have run:

sudo ntfsfix /dev/sdb1

Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

**_AND_**

sudo fdisk -l

Disk /dev/sdb: 8589 MB, 8589934592 bytes
64 heads, 32 sectors/track, 8192 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

**_AND_**

dmesg | tail
[ 2702.833653] end_request: I/O error, dev sdb, sector 16777215
[ 2702.833661] __ratelimit: 17 callbacks suppressed
[ 2702.833667] Buffer I/O error on device sdb, logical block 2097151
[ 2702.838963] sd 10:0:0:0: [sdb] Unhandled sense code
[ 2702.838968] sd 10:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2702.838974] sd 10:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2702.838982] sd 10:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 2702.838990] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 ff ff ff 00 00 01 00
[ 2702.839007] end_request: I/O error, dev sdb, sector 16777215
[ 2702.839013] Buffer I/O error on device sdb, logical block 2097151

**_AND_**

lsusb

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04e8:327e Samsung Electronics Co., Ltd 
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 4971:ce14 SimpleTech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Disk /dev/sdb doesn't contain a valid partition table


If, as these things say, my drive doesn't contain a valid partition why does my drive work fine when put directly into my computer apart from the Duo Pro Drive?

---

### Post by yedidyah on 2010-02-09
This problem is solved.

The Duo Pro Drive by Simpletech (a fabrik company) was garbage. I went to the guy who sold it to me and we tested another one in linux and windows and it had the same problem. 

We put the drive into a Pro Drive (single drive) case and it worked fine in windows and linux.

---

### Post by kubilus1 on 2010-03-10
I just got a bare SimpleTech Duo Pro.  I installed one 750GB drive in the bay with the cables, switched it to RAID1, plugged it in, and got the same results as you.  8.6GB drive, cannot partition it, red blinky lights, lots of 'Unhandled sense' errors.  Frustration.

Then I read the manual for the drive.

To get this to work, you have to turn the drive on, and press and hold the 'RESET' switch for 5 seconds.  That initializes the RAIDness of the drives.

After doing, that the drive showed up as 750GB, let me format as EXT3 and is working fine.  I plan to pickup a second 750GB drive and play with mirroring and disaster simulation.

So far so good with a Duo Pro on Ubuntu.

---

