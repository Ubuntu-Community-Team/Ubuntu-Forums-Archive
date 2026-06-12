---
title: "Cannot mount a hard drive..."
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Nelson-Ray on 2006-08-29
Hello...I recently came back from vacation and found my ubuntu server crashed. I had to do a reinstall and none of the extra hard drives (hdb/hdc/hdd) would mount, until I would manually run fsck on each of the drives. All the drives are now mounted except 1. When I run fsck on /dev/hdh1
it launches fsck but just pauses there :

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)


If I try to mount the drive, I get this msg :

wrong fs type, bad option, bad superblock on /dev/hdh1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If I type in "dmesg | tail" ..I get this msg : [18007461.380000] skge hardware error detected (status 0x400)
[18007461.720000] skge hardware error detected (status 0x400)
[18007465.864000] skge hardware error detected (status 0x400)
[18007467.060000] skge hardware error detected (status 0x400)
[18007469.192000] skge hardware error detected (status 0x400)
[18007469.600000] skge hardware error detected (status 0x400)
[18007687.012000] skge hardware error detected (status 0x400)
[18007867.800000] skge hardware error detected (status 0x400)
[18010234.644000] skge hardware error detected (status 0x400)
[18050447.728000] EXT3: failed to open journal device unknown-block(0,0): -6

could someone offer help on reviving the hard drive? Thanks...

---

### Post by Nelson-Ray on 2006-09-03
anybody could help? I need to badly mount the drive...

---

### Post by HAARP on 2006-09-03
Looks like the filesystem is toast. Try searching for tools that recover files or rebuild the filesystem tree on a EXT3 filesystem. Sorry, I don't know anything better..

---

