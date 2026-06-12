---
title: "New Installation /root /swap /home partitions"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by justin_c18 on 2009-02-21
I've just installed Ubuntu Hardy Heron 8.04 onto my laptop with the alternate installation disc. I've made three separate parttions as follows. 1 GB /swap, 14 GB /root, and 64 GB /home. Something similar to that anyway. 

```
sudo fdisk -lu
``` shows:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 


Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     1959929      979933+  82  Linux swap / Solaris
/dev/sda2   *     1959930    31262489    14651280   83  Linux
/dev/sda3        31262490   156296384    62516947+  83  Linux

```

```
sudo nano /etc/fstab
``` says:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bc316f53-8ed0-4160-abac-16c52bb9af6b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b3e909aa-cc20-49d5-a18c-3eada0771274 /home           ext3    relatime        0       2
# /dev/sda1
UUID=0a0902f0-9d06-45b1-b567-4025fc0be5be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Now, I'm not exactly sure if all the partitions are detected or are used. But right after finishing setting up the partitions in Hardy it went straight into the install. I figured I would have had to enable the partitions. 

How can I see if both root and swap are in use, and if everything is setup proper?

I'm possibly trying to be overly cautious, I don't know. But, Chakra was weird, I had to enable the usage of the swap partition for some reason. But I guess ubuntu ~= Chakra. Or, Debian ~= Arch.

Thanks. Looking forward to a response.

---

### Post by ploom on 2009-02-21
By paste'ings yere You appear to have three partitions nicely set up. just direct them the same way with installer...

---

### Post by justin_c18 on 2009-02-21
> **ploom said:**
> By paste'ings yere You appear to have three partitions nicely set up. just direct them the same way with installer...

Thanks dude. Appreciate it, and your time looking at the post. It's all groovy. 

Have a good one.
Thanks again.

---

### Post by vanadium on 2009-02-21
Indeed, all looks good indeed, but if you want to make sure

```

mount

```
will tell you which partitions are mounted and where, and
```

cat /proc/swaps

```
(or "swapon -s") will tell you what swap space is in use.

---

### Post by justin_c18 on 2009-02-28
> **vanadium said:**
> Indeed, all looks good indeed, but if you want to make sure

```

mount

```
will tell you which partitions are mounted and where, and
```

cat /proc/swaps

```
(or "swapon -s") will tell you what swap space is in use.

Thanks a lot. 2nd time this post has helped me since writing it. :D

---

