---
title: "Converting from fat32 to ntfs?"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by mEtho on 2006-03-06
i have several partitions on my harddrive, the problem is that i have a fat32 partition which i would like to convert into ntfs because i would like to install windows xp home which does not support an option for converting vfat into ntfs therefore i decided to do under ubuntu. I installed Gparted to do just that, i was happy that it converted vfat to ntfs but the problem is /etc/fstab shows different results. 

> metho@ubuntu:/etc$ more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /backup         ext3    defaults        0       2
/dev/hda6       /dos            vfat    defaults        0       0
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda8       /media/hda8     ext3    defaults        0       2
/dev/hda9       /media/hda9     ext2    defaults        0       2
/dev/hda10      /windows        vfat    defaults        0       0
/dev/hda11      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda6 /mnt/windows ntfs users,owner,ro,umask=000 0 0
metho@ubuntu:/etc$


as you can see hda6 is vfat and also ntfs, which is very confusing could you please tell me what the problem is or is there another partition program that can be used.

---

### Post by woedend on 2006-03-06
is there data on it?  I do not see the difference in just deleting hda6 partition and leaving it blank and letting windows xp repartition it to ntfs for you.

---

### Post by mEtho on 2006-03-06
there is no data on it, i thought about deleting the partition and lets windows do its magic but i have windows xp home which is not like windows xp professional, in other  words it wont let me change a partition into ntfs... anyway you think XP home will change the partition to ntfs if i delete hda6 partition and leave it blank!!!!

---

