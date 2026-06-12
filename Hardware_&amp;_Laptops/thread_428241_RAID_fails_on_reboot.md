---
title: "RAID fails on reboot"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by zaziork on 2007-04-30
I'm using Feisty, and successfully created a RAID 5 array using mdadm. It mounts to /dev/md0 after creation, with no issue.

However, every time I reboot the array appears to fail. Not only does it not mount during the boot process, but I'm no longer able to mount manually. I did make the correct addition to /etc/fstab (the initial mount, using mount -a, goes fine).

After reboot, sudo mount -a gives me the following: mount: /dev/md0: can't read superblock

sudo mdadm --detail /dev/md0 gives me: mdadm: md device /dev/md0 does not appear to be active.

If I try to assemble the array: sudo mdadm -A /dev/md0, I get:

mdadm: no devices found for /dev/md0

Any ideas? I can create a new array without problem, and mount it. Everything is fine until I reboot, after which it all goes pairshaped...

---

