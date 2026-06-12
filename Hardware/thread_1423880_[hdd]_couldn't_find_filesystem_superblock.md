---
title: "[hdd] couldn't find filesystem superblock"
date: 2010-03-07
forum: Hardware
---

### Post by xxxYURAxxx on 2010-03-07
hdd partition table is broken
/dev/sda4 & /dev/sda5 are ext4 partitions

**sudo testdisk -l /dev/sda**
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Partition Start End Size in sectors
1 P EFI System 40 409639 409600 [EFI System Partition]
2 P Mac HFS 409640 244608863 244199224 [Leopard]
3 P Linux Swap 244608864 248702264 4093401
No FAT, NTFS, EXT2, JFS, Reiser, cramfs or XFS marker
4 P MS Data 248702265 265088564 16386300
4 P MS Data 248702265 265088564 16386300
5 P MS Data 265088565 488392064 223303500


**e2fsck -f -y -v /dev/sda5**
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No such file or directory while trying to open /dev/sda5


**sudo e2fsck -vnb 8193 /dev/sda5**
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No such file or directory while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>


**ls -la /dev/sd***
brw-rw---- 1 root disk 8, 0 2010-03-07 12:56 /dev/sda


is anyone help me?

---

### Post by xxxYURAxxx on 2010-03-07
or when it posiible howto get /dev/sda5 from /dev/sda ?

/dev/sda
type: gpt
heads: 255
sectors: 63
cylinders: 30401
total sectors: 488392065

/dev/sda5
size: 106.48 GiB
first sector: 265088565
last sector: 488392064
total sectors: 223303500

---

