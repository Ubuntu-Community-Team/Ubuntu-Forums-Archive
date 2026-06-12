---
title: "Startup automount troubles"
date: 2009-12-03
forum: Hardware
---

### Post by restart on 2009-12-03
Hi there.

History: one day I noticed that my old 100Gb hard drive has TOO many bad sectors (every file I download\copying\creating on my drive had a 50% chance to get Input\output error after trying to read it after), so I decided to buy a new one.
I bought a 320GB new perfect hard drive, and started to move all the data from old one to new one.
Everything gone good (except huge amount of i\o errors, but it's okay, coz most of them are on /home partition, not system dangerous). After all, I switched my old HD to new one.
I copied data with "dd", so after I manage with the partitions' sizes a little bit.

Problem: the system starts okay, except one thing! Totally I have 4 partitions: boot, swap, root and home. Boot and root paritions mounts okay, but home don't. System offers me to enter the recovery mode pressing ESC. I do it, then type
```
mount -t ext4 /dev/sda4 /home
```
and magically it mounts! Then I type Ctrl+D and system continue to boot up. Then everything goes normal.

fstab prints:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=53a14b6b-0ec1-4b01-b32c-434bc093879e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b8046b9a-014d-4b46-a852-1ef5d6b489c6 /boot           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=e20af57d-5c34-47b9-b6c7-df1c29caec29 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=ed420fc3-34e2-424f-be70-1b2414713805 none            swap    sw              0       0

```

UUIDs are correct.

Any suggestions?

---

### Post by restart on 2009-12-03
OOps! Sorry! :)
There is a wrong UUID was in fstab for /dev/sda4 (/home) partition.
Thank you everyone :)

---

