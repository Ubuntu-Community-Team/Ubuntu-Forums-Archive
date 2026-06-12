---
title: "Ubuntu LiveCD - EXISITING Raid Array"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by tendo on 2009-08-30
Hi guys, I've done quite a bit of googling this morning and can't find an answer (#ubuntu seems to be sleeping).

My machine is a little older, has a RAID 5 software array (/dev/md0) and a working Gentoo installation.  If I let it boot up I can see my 1TB array just fine.

When I boot up the LiveCD, I can't see /dev/md0 or my /data partition.  

However, I can see all the drives:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   83  Linux

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          13      104391   83  Linux
/dev/sde2              14         141     1028160   82  Linux swap / Solaris
/dev/sde3             142        9729    77015610   83  Linux

```

Is there a way to load up this RAID software array for use in my Ubuntu installation, or does it HAVE to be formatted?  I have most of it backed up, but I'd rather not spend time recovering.

Thanks!   :guitar:

---

### Post by tendo on 2009-08-30
So I've done a lot more research, and apparently what I need to do is use the mdadm tool with the assemble switch.  This is for loading an existing array.  

Should I do this while the LiveCD is in and I'm in this temporary environment, or should I install Ubuntu first, and then 'mdadm assemble'.

I haven't quite figured it out yet, I'm still getting this:
```

ubuntu@ubuntu:/usr/share/man$ mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: failed to create /dev/md0

```

---

### Post by tendo on 2009-08-30
Oh it works with sudo in front of it!  :P

Problem solved!

---

