---
title: "superblock error on modern drive. tried fsck.ext3/testdisk/etc"
date: 2009-04-30
forum: Hardware
---

### Post by R2LL2R on 2009-04-30
Hi all,

I'm getting the typical superblock errors when tring to access my old boot drive. 

I can se the drive from nautilus, and see the home folder (where  the problem seems to be), can copy, and all the file headers will copy to new location, but all data is unreadable. its at this stage that I get bad superblock errors.

so I used testdisk to show all superblock backups and attempted to run fsck.ext3 using:
fsck.ext3 -b 2654208 /dev/disk
and I recieved the following error message regardless of any option I try:
-----------begin quote----------------
/
fsck.ext3: No such file or directory while trying to open ext3
ext3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
-----------end quote------------------

also; drive becomes unreadable after first attempt to read untill next reboot.... 

amny help greatly appreciated, I have many .iso files & backups on this drive I'd rather not use...

---

