---
title: "[SOLVED] Undeterministic device allocation for my disks"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by manemannen on 2008-01-06
Hi,

I have three disks. 1 SATA and 2 PATA disks. The SATA disk is always mounted as sda. The problem I have is that the two PATA disks are mounted as sdb and sdc which would be no problem if they get the same device name each time - **but they don't**!

Pata disk A is sometimes on /dev/sdb and pata disk B is then on /dev/sdc and sometimes it is the other way around. This becomes a problem since I have these defined in the fstab and I get errors in the final boot stage (if they don't match the fstab setup - so the error doesn't always occur).

Is there some way to enforce that disk A is always found on /dev/sdb and disk B on /dev/sdc? Can I use the UUID to mount the disks instead of the device name? If so, how do I get the UUID of the disk?

Any help appreciated.

---

### Post by manemannen on 2008-01-21
Ok I figured it out. Guess I should've search on the web a little bit more first. Just as well that nobody bothered to answer.

The way to do it is to mount the partitions with the UUID instead. The UUID can be find by typing:

ls -l /dev/disk/by-uuid/

The output could look like this:

lrwxrwxrwx 1 root root 10 2008-01-21 16:49 34f79a4d-4cb0-4147-8b20-9f4fdacb0c67 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2008-01-21 16:49 5e137833-b072-416c-9a25-35ab41450095 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-01-21 16:49 6d839c50-e01e-4ca6-888a-7db34b6c9b1b -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-01-21 16:49 7153f70a-5d90-4159-95b7-737239d65c44 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-21 16:49 b43b8430-ee74-45de-a48e-b3b22923b96d -> ../../sda1


You just have to figure out which partition is which and mount them where you want them.

---

