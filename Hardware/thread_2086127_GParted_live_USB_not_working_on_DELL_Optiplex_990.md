---
title: "GParted live USB not working on DELL Optiplex 990"
date: 2012-11-19
forum: Hardware
---

### Post by vksingh on 2012-11-19
Hi All,

I am using GParted live USB (bootable) to partition my "/" partition (want to reduce the size). I have made a bootable USB from GParted live iso.

When I boot this, the GParted gets hung at in the mid and gives following message on console:

**iTCO_wdt : Found a Cougar Point TCO device ..... **

Please let me know how to fix this. Also please tell me if any other ways to shrink the space of a linux partition.

Regards,
Vivek):P

---

### Post by carl4926 on 2012-11-19
So have you been able to verify the Gparted USB boots on another machine.
Have you tried Parted Magic
You could use a Ubuntu live cd/usb as gparted is on it

---

### Post by ahallubuntu on 2012-11-19
Try a different version of Gparted.  Try the version on a Parted Magic Linux CD or just use a Ubuntu live CD, see if there is any difference.

---

### Post by vksingh on 2012-11-20
I tried with Ubuntu live CD. I started GParted. I was able to get/see the details of the partitions on GParted GUI but when i select my partition (/dev/sda5) to resize in move/resize window, i the move/resize button was not enabled.

---

### Post by carl4926 on 2012-11-20
Show us a screenshot and also post result of

```
sudo fdisk -l
```

---

### Post by ahallubuntu on 2012-11-20
> **vksingh said:**
> I tried with Ubuntu live CD. I started GParted. I was able to get/see the details of the partitions on GParted GUI but when i select my partition (/dev/sda5) to resize in move/resize window, i the move/resize button was not enabled.

Are you sure the partition you're trying to resize isn't mounted?  I think the live CD will automatically use a swap partition on your hard drive if it finds one; any chance that is the partition you are trying to resize?  (An extended partition that contains it maybe?)

---

### Post by vksingh on 2012-11-21
yes, swap is also mounted in the same partition

---

