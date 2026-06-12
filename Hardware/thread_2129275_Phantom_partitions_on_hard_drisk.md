---
title: "Phantom partitions on hard drisk?"
date: 2013-03-25
forum: Hardware
---

### Post by hlleach on 2013-03-25
I have a hard disk formatted to ntfs, it started out as a single partition but is now being picked up as 2 + free space that together equal a larger size than the disk should even hold.

Funny thing is I can mount the disk with mount -t ntfs  /dev/sdb and it seems to work fine.

/dev/sdb1 and /dev/sdb2 will not mount though giving errors like this:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

ntfsfix produces:

sudo ntfsfix /dev/sdb
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb was processed successfully.

sudo ntfsfix /dev/sdb1
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

fdisk gives:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Unknown
/dev/sdb3   ?   225735265   225735274           5   72  Unknown
/dev/sdb4      2642411520  2642463409       25945    0  Empty


Partition table entries are not in disk order






Should I worry about these phantom partitions? Is there a way to fix it?

It's worth noting that I have not tried to set up multiboot or messed with the disk in any low level fashion, but have installed truecrypt, which I think may be the culprit despite only using it to create a volume in a file on that drive.

---

### Post by oldfred on 2013-03-25
Your partition table looks like it has random data that it is trying to convert into a partition table.
Did you partition drive or just start writing data to it? Drives really need to be partitioned, but some have just formatted an entire drive, copied lots of data to it. It then looks like a floppy disk but cannot be remounted as eveything expects partition table to find files.

Does testdisk find old valid partitions?

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by hlleach on 2013-03-25
I certainly did make the assumption that a single partition would be there upon formatting. TestDisk confirms your guess too.
The drive I was backing up still seems to be working so I'm just going to accept this as a learning experience and start over.

Thank you for the quick and concise answer.

---

