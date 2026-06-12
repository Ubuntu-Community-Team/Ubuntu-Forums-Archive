---
title: "How to enable check disk for error during booting"
date: 2010-11-13
forum: Hardware
---

### Post by darshan123 on 2010-11-13
Hi,

I want to check my disks for errors during boot-up time. How do I enable  it so that Ubuntu does it the next time I restart ?

I heard that there is a reboot count that ubuntu keeps so that it can start disk check automatically. How can I access the count ? Maybe i will set the count to 1 and restart.

Thanks,
-Darshan

---

### Post by sikander3786 on 2010-11-13
It is done in /etc/fstab.

See this page for an entry of <pass num>. Thats what you are looking for.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This is important,

> Controls the order in which fsck checks the device/partition for errors at boot time. **The root device should be 1. Other partitions should be 2, or 0 to disable checking.** 

---

### Post by Elfy on 2010-11-13
```
sudo touch /forcefsck
```
should force a check on reboot

To change the time between counts - default is 30
```

sudo tune2fs -c *n* */device/to/check*
```

Where *n* is a number and */device/to/check* is the partition you wish to change the count for - _eg_ /dev/sda1

so 

```
sudo tune2fs 100 /dev/sda1
```
would check sda1 every 100 times

```
man tune2fs
```

---

### Post by darshan123 on 2010-11-13
Thanks. sudo touch /forcefsck was very simple.

:P

---

### Post by psusi on 2010-11-13
> **sikander3786 said:**
> It is done in /etc/fstab.

See this page for an entry of <pass num>. Thats what you are looking for.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This is important,

That is the order the different disks should be checked in, not how many boots left before they should be checked.

---

