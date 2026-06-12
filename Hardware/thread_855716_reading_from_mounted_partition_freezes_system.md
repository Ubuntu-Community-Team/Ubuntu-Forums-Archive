---
title: "reading from mounted partition freezes system"
date: 2008-07-10
forum: Hardware
---

### Post by izmeh on 2008-07-10
I've been trying to get my 2nd internal hdd to mount, and so far it seems I'm getting closer to where I want to be. The partition shows up as it's own drive on my desktop, however when i read a file from it (ie play a video in movie payer, or scan for music in rhythmbox), it locks/freezes the system completely. I'm forced to do a hard restart.

I've partioned the drive as ext3 and changed the file permissions to 770.

fstab included below (sdb5 is the partition)

Any suggestions?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c8fc3d95-9e4f-49b4-b348-782d6bb768be /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9dec3dc7-ea40-49a5-a464-60fe1f6da253 none            swap    sw            0       0
# /dev/sdb
UUID=d751f19c-ec95-449a-96c9-5a8a7cf4b8ca /media/mass	  ext3    user,errors=remount-ro	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 		0       0
```

---

