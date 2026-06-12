---
title: "File-system problem"
date: 2008-10-25
forum: General Help
---

### Post by GavinT on 2008-10-25
Hi all,

I'm a relative newbie to linux running Ubuntu 8.04.

When trying to make a USB boot disk for my Aspire One the Ubuntu machine seemed to lock up.  Upon restart it checked disk and produced an error on my second drive dev/sdb1 (where all my files are).  The checkfs log shows:

Log of fsck -C3 -R -A -a 
Sat Oct 25 12:20:52 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/sdb1

/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8


I checked gparted and it is showing sdb1 as 'unallocated' with a size of 465.76Gb (its a 500Gb HD).

I'm completely lost and fear that so is my data.  Any thoughts / suggestions?

Thanks,
Gavin.

---

### Post by geirha on 2008-10-25
Try running [testdisk](apt://testdisk). It may find your lost partition and be able to recover it.

---

### Post by GavinT on 2008-10-25
Worked a treat.  Thanks very much geirha.

Gav.

---

