---
title: "Boot problem"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by coolclassic on 2006-03-05
This is an error I am getting since replacing my motherboard It was caused by me trying to boot into the wrong drive and repeatly rebooting :(
----- 
Udev is already active on /dev/

The device node /dev/hdc1 for the root filesystem is missing,incorrect, or there is no entry in /etc/fstab.

The system is also unable to create a temporary node in /dev/shm 
------
I am unable to use recovery mode as I get the same errors, at present I am using knoppix to get access to my drive. 

I have used fsck and this is the result I get.

sudo fsck ext3  /mnt/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: No such file or directory while trying to open ext3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Am I using fsck correctly and if so how do I correct this.

---

