---
title: "fstab: special device does not exist"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by tch on 2005-06-05
I tried to configure some mountpoints for my s-ata partitions (sda1 -> sdb4) and for hda3 & hda4, so I edited fstab to the following state:
```
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       3
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3	/mnt/hda3	reiserfs defaults	0	0
/dev/hda4	/mnt/hda4	reiserfs defaults	0	0
/dev/sda1	/mnt/sda1	reiserfs defaults	0	0
/dev/sda2	/mnt/sda2	reiserfs defaults	0	0
/dev/sda3	/mnt/sda3	reiserfs defaults	0	0
/dev/sda4	/mnt/sda4	reiserfs defaults	0	0
/dev/sdb1	/mnt/sdb1	reiserfs defaults	0	0
/dev/sdb2	/mnt/sdb2	reiserfs defaults	0	0
/dev/sdb3	/mnt/sdb3	reiserfs defaults	0	0
/dev/sdb4	/mnt/sdb4	reiserfs defaults	0	0
```
The problem is, /dev/hda3 and /dev/hda4 are mounted during bootup, but /dev/sdbx or /dev/sdax are not. It only reports for example "Special device /dev/sda1 does not exist". However, I can mount them straight away after I log in. So they should exist, but systems thinks otherwise.

Am I 1) stupid not knowing something I should know about fstab (haven't configured it before), or 2) might it be because they're s-ata? Whatever the case is, what should I do?

Thanks beforehand.

---

### Post by tch on 2005-06-05
OK, sorry, no problem anymore, I missed couple of [these](http://www.ubuntuforums.org/showthread.php?t=30233) crucial threads. I think they will be helpful.

---

