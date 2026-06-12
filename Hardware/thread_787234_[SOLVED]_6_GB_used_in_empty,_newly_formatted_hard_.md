---
title: "[SOLVED] 6 GB used in empty, newly formatted hard drive"
date: 2008-05-08
forum: Hardware
---

### Post by Mike Brennan on 2008-05-08
I just reformatted an external USB hard drive. It was a FAT32 partition. I just reformatted it to be on large (110 GB) ext3 filesystem using gparted. The reformatting went smoothly, but I'm wondering why when I check the properties on the drive, it reports that 5.8 GB are used.

I understand there is undoubtedly some system related stuff written to the disk that I don't see in the filesystem, but 5.8 GB? Is this normal?

Is this related to the fact that I made the whole thing one large partition instead of several smaller partitions?

---

### Post by hermes0710 on 2008-05-09
Is the partition primary or logical?

---

### Post by hallgeirl on 2008-05-09
Hi. By default, ext2 and ext3 reserves 5% of the total disk space for some reason.
You can turn it off by executing:
# sudo tune2fs -m 0 /dev/<yourdevicehere>
For instance
# sudo tune2fs -m 0 /dev/sda3

Hope this helps. :)

---

### Post by jespdj on 2008-05-09
> **hallgeirl said:**
> Hi. By default, ext2 and ext3 reserves 5% of the total disk space for some reason.
The reason is to keep the system running when the disk is getting full. Only root (the superuser) can use the last 5%.

Suppose that the disk was really 100% full, then even root might not be able to login anymore to cleanup things.

If this is a second disk (not the main harddisk that contains your Ubuntu OS installation) then it's no problem to change the settings so that you can use the last 5%. I wouldn't do that on your main harddisk, it might make the system unusable if the disk is full.

---

### Post by hallgeirl on 2008-05-09
Cheers for the explanation. :)

---

### Post by Mike Brennan on 2008-05-09
> **hermes0710 said:**
> Is the partition primary or logical?

I believe it is a primary partition, if I understand the difference correctly. It is not the partition I boot from, though. It's an external hard drive connected through a USB port. I formatted the entire external drive as one ext3 partition.

It looks like I'm getting the answer I was looking for from the other posts, though, so I understand what's going on.

Thanks jespdj and hallgeirl for the info.

---

