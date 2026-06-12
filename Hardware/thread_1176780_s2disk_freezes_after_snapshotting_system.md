---
title: "s2disk freezes after snapshotting system"
date: 2009-06-02
forum: Hardware
---

### Post by Joojo on 2009-06-02
Hi, I have a problem with uswsusp. When I'm trying to Suspend to disk everything seems well but then, after snapshotting system, it stops. It says that it's writing image file but it stays on 0% forever.

I'm using a swapfile not a partition, but s2disk is supposed to work with files too, no?

less /etc/fstab gives me:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/sda2 /media/Drive_C     ntfs    defaults,umask=007,gid=46 0
/dev/sda5 /media/Drive_E     ntfs    defaults,umask=007,gid=46 0
/swap/.swap.img       none            swap    sw       pri=0       0       0 0

```

less /etc/uswsusp.conf
```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/loop0
compress = y
early writeout = y
image size = 1000000000
RSA key file = /etc/uswsusp.key
shutdown method = platform
resume offset = 970752
compute checksum = y
suspend loglevel = 2
max loglevel = 4

```

Any ideas anyone? Will be highly appreciated :D

/Joojo

---

