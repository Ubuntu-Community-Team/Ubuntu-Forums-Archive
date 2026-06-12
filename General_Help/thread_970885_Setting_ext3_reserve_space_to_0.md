---
title: "Setting ext3 reserve space to 0"
date: 2008-11-04
forum: General Help
---

### Post by stuyguy on 2008-11-04
Hello,

    I just created my first software linux RAID array using mdadm.  I'm using 7x 1 TB disks in a RAID-5 setup and ended up with a /dev/md0 at 5.4 TB.  I'm wondering - is it a good idea to set the reserve space down to 0 blocks if it's not my root file system?  By default, ext3 reserves 5% of the disk, which works out to...276 GB!  I did:

sudo tune2fs -r 0 /dev/md0

which got it all back.  I'm just wondering whether fsck (or something else) will freak out if there's no space left and the file system is corrupt.  If so, what would be a reasonable amount of space to reserve for the inevitable "fixable" file system errors?

Thanks.

---

### Post by Sam on 2008-11-04
I don't think that setting 0% of reserved blocks on any non-system partition will bring issues...

---

### Post by psusi on 2008-11-06
It won't hurt anything, but generally try not to get the disk too full or it will start to get fragmented.

---

### Post by fjgaude on 2008-11-08
> **psusi said:**
> It won't hurt anything, but generally try not to get the disk too full or it will start to get fragmented.

My understanding would be never let the drive fill to a level where the largest file you are to copy to it has no contiguous space to go. I like to leave at least 10% or more free.

---

