---
title: "Stop internal partition automounting in other user account"
date: 2008-09-24
forum: General Help
---

### Post by duckgoesoink on 2008-09-24
Hi everyone,

I've been happily automounting my FAT32 data partition for a few months now. Today I created a new user account for the French people who use my computer (with everything in French, limited rights, etc), but I would like to know how to stop my data partition from automounting under this new account - I don't want anyone stuffing anything up. I do however want to keep it automounting for me.

So far I've got it so they can't manually mount internal partitions, but the data partition still automounts.

Some help on this matter would be greatly appreciated. :-)

P.S. I tried Google already, so far I haven't found the solution on my own.

---

### Post by russlar on 2008-09-24
Can we assume that the entries are commented out of (or removed from) /etc/fstab?

---

### Post by duckgoesoink on 2008-09-24
I was under the impression that the /etc/fstab was used for all users (ie. there was only one fstab for the system). and I don't really know a lot about fstab-ing - so I don't know how to arrange it so that it only automounts that FAT32 data partition for me. How would I go about doing this? My fstab currently looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 #/dev/sda2
UUID=4812-2CE3  /media/SHARED  vfat  auto,users,uid=1000,gid=100,dmask=007,fmask=137  0 0
# /dev/sda4
UUID=a1695752-7f2f-4e19-a10a-cef9aede0b29 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a48f4f04-84c2-464d-9169-a39187ba366d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Thanks, I appreciate the help :-)

---

