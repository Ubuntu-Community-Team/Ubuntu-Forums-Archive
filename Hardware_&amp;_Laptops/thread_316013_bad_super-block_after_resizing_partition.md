---
title: "bad super-block after resizing partition"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by eliabramo on 2006-12-10
I recently installed Arch linux next to my Ubuntu (and XP). I liked it so I decide to deliver some space from the Ubuntu partition to the Arch partition. I done this with partition magic on WinXP and it's stops with some error (bad block or something) in the middle of the job. now I can't mount the Arch partition in Ubuntu (and of curse can't boot into it) and get this error:
> mount: wrong fs type, bad option, bad superblock on /dev/hda8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 
fsck results:
> fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda8

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
I tried alternate superblock (by mke2fs) but it didn't work.

how can I fix the super-block? it seems that that partition is ok, i can see it in fstab and the size looks ok in gparted. is there is any program to fix bad super-blocks?

---

