---
title: "Slow fsck for Dell 1420N"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by teich on 2007-10-03
Hi All,

Every 25 mounts of the os_part partition on my Dell 1420N results in a fsck, as it should. However, fsck takes upwards of 30-45 minutes.  This is sometimes not OK.  Is there a way to skip it if there is something important going on for which I need my laptop right away?  Cntrl-C doesn't seem to do it.

Thanks.

---

### Post by dcstar on 2007-10-03
> **teich said:**
> Hi All,

Every 25 mounts of the os_part partition on my Dell 1420N results in a fsck, as it should. However, fsck takes upwards of 30-45 minutes.  This is sometimes not OK.  Is there a way to skip it if there is something important going on for which I need my laptop right away?  Cntrl-C doesn't seem to do it.

Thanks.

The default count for an EXT2/3 filesystem is 30 mounts, you can change this with:
```

sudo tune2fs
```

If it takes this long, then perhaps there is another issue that need to be addressed, are there any messages while fsck runs?

---

### Post by klabog on 2007-11-01
I have the same problem. fsck runs every 23 mounts but not such a long time. About 5 to 10 minutes. It's only the os partition.
I repartitioned this partition hoping that it will take less time on 30% of original length but there is no change. The new created (nearly empty) partitions (each about 30% of the original partition) are checked in some seconds.
Here is what I found in /var/log/fsck/checkroot

Log of fsck -C -a -t ext3 /dev/sda6 
Thu Nov  1 12:21:26 2007

fsck 1.40-WIP (14-Nov-2006)
os_part: clean, 218255/7681024 files, 33915306/61440560 blocks

Thu Nov  1 12:21:26 2007

What could be the reason?

edit: forgot to say that I have a Inspiron 6400 (equal 1520n)

Thanks, Klaus

---

