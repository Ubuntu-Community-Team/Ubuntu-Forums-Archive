---
title: "problem after removing a parttion"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by juniorsonny on 2007-12-26
After moving a partition and resizing another I now come up with this error.

fsck 1.40.2 (12-Jul-2007)
/dev/hda3: clean, 6945/11894784 files, 3725376/23786240 blocks
fsck.ext3: Unable to resolve 'UUID=fe38c9cb-0366-4b3c-878c-7c185da13103'

fsck.ext3: Unable to resolve 'UUID=425f41d6-c02c-4bc6-9614-c173ecc7259d'

fsck died with exit status 8


I do not know how to fix it.  Can anyone please help in any way?

---

### Post by RudolfMDLT on 2007-12-26
What EXACTLY did you do? can you boot Ubuntu? What program did you use to do the partitioning? can you please post the output of this command: "cat /etc/fstab"

Look at the output and then tell me which of those folders/drives did you move? As far as I have read, 8 means that it can't find the drive with the UUID specified in fstab.

---

### Post by uidb4056 on 2007-12-26
Also will be helpful if you post the output of blkid

---

### Post by RudolfMDLT on 2007-12-26
> **uidb4056 said:**
> Also will be helpful if you post the output of blkid

thats a command I'll be writing on my forehead! Thanks!

---

### Post by juniorsonny on 2007-12-26
Here's that output.   I used Gparted to delete partitions hdb1 and hdb6 and tried to resize hda1.   I ended up unplugging the hdb drive.  the hdb1 and hdb6 are the ones that are showing up in the error message at boot up.  

I can bootup but have to hit enter then control +d to finish the bootup.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=551fc25f-4f2f-44a0-aee5-37da68ff8aec /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=83d13eb3-d64f-4fbe-b23b-f557d29235a3 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=fe38c9cb-0366-4b3c-878c-7c185da13103 /media/hdb1     ext3    defaults        0       2
# /dev/hdb6
UUID=425f41d6-c02c-4bc6-9614-c173ecc7259d /media/hdb6     ext3    defaults        0       2
# /dev/hda2
UUID=3d51cd2d-2e06-426f-9c96-b4e40866cfb8 none            swap    sw              0       0
# /dev/hdb5
UUID=8b41e8da-8ead-4535-8bf1-a994eef56708 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by juniorsonny on 2007-12-26
Here's that output.   I used Gparted to delete partitions hdb1 and hdb6 and tried to resize hda1.   I ended up unplugging the hdb drive.  the hdb1 and hdb6 are the ones that are showing up in the error message at boot up.  

I can bootup but have to hit enter then control +d to finish the bootup.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=551fc25f-4f2f-44a0-aee5-37da68ff8aec /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=83d13eb3-d64f-4fbe-b23b-f557d29235a3 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=fe38c9cb-0366-4b3c-878c-7c185da13103 /media/hdb1     ext3    defaults        0       2
# /dev/hdb6
UUID=425f41d6-c02c-4bc6-9614-c173ecc7259d /media/hdb6     ext3    defaults        0       2
# /dev/hda2
UUID=3d51cd2d-2e06-426f-9c96-b4e40866cfb8 none            swap    sw              0       0
# /dev/hdb5
UUID=8b41e8da-8ead-4535-8bf1-a994eef56708 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by juniorsonny on 2007-12-26
sorry for all the posts firefox was acting weird.  I did fix my problem I deleted the 2 entries in the /etc/fstab relating to hdb1 and hdb6.  Now it boots up just fine.

---

### Post by RudolfMDLT on 2007-12-27
That's what fixed it for other people too. Glad you got it sorted!

---

