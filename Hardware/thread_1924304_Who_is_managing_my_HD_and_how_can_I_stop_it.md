---
title: "Who is managing my HD and how can I stop it?"
date: 2012-02-12
forum: Hardware
---

### Post by bartoldo on 2012-02-12
I've added a second hard drive to my machine with Kubuntu oneiric and I've partitioned it (using sfdisk) in order to move there a Mandriva installation from another machine. (Both disks are internal SATA. All partitions are ext4, except one that is ext3.) I've copied there my fsarchiver images, done fdisk -f and it all went OK. But, when I tried to mount those partitions, I was told they were already mounted or in use. (Either if I try to mount them as /dev/sdbX or via UUID.) Mount command didn't show they were mounted and I've discovered they became /dev/dm-0, /dev/dm-1 (the first primary partition sometimes appearing as dm-0 and sometimes as dm-1, the others seem to be constant) and so on, or /dev/mapper/a_string-part1, /dev/mapper/the_same_string-part2 etc. I can mount them so, but, it seems they're read-only even if I mount them explicitly as rw. After a LiveCD boot they are perfectly writable. If I try to save a file (from a text editor, for example) it complains that the filesystem is read-only. If I try some cp/mv operation in terminal, it usually appears to be done, but, as soon as I unmount that partition and mount it again, I can see it didn't, it has probably been only done somewhere in a cache. So, I am assuming there is some daemon or something that's appropriating with that disk and tries to manage it. The most obvious guess would be LSV. But, lsdisplay says there aren't logical volumes. How could I find out what it might be and how could I be able just to mount /dev/sdbX (or UUID), or, at least, to have those partitions rw? Thanks in advance.

---

### Post by 2F4U on 2012-02-12
Devices named /dev/dm-x are usually part of a logical volume and managed by a logical volume manager (LVM).

---

### Post by bartoldo on 2012-02-12
> **2F4U said:**
> Devices named /dev/dm-x are usually part of a logical volume and managed by a logical volume manager (LVM).

Yes, but, as you could've seen above, lvdisplay says there aren't logical volumes (precisely, it says "no volume groups found"). So, how can I find out what LVM (if it's LVM) is doing with these devices? (And how to stop it doing that?)

---

