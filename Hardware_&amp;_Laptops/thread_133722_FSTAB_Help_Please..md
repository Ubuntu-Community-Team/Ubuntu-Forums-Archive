---
title: "FSTAB Help Please."
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by cetol on 2006-02-20
I am getting a failed message during the boot up when mounting local filesystems. Here is the contents of the FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/win_gen	vfat	rw,user,auto	0	0
/dev/hda2	/media/win_vid	vfat	rw,user,auto	0	0
/dev/hda3	/media/win_aud	vfat	rw,user,auto	0	0
/dev/hdb5	/media/win_prog	vfat	rw,user,auto	0	0
/dev/hda6	/video		ext3	rw,user,auto	0	0


I cant seem to find the problem. Ideas anyone?

---

### Post by Jedeye on 2006-02-20
well... you sure do have a lot of partitions. There wasn't anything that really jumped out at me... The only thing I did not see was swap memory which I do not think is required.

---

### Post by luna6 on 2006-02-20
Think ...a swap directory might help
should look something like this

/dev/hda2       none            swap    sw              0       0

replacing "hda2" with the mount point of your swap dir...


edit : ..sorry to be redundant didnt see the end of the post above but having the swap sure wouldnt hurt.

---

