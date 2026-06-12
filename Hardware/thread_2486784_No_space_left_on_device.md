---
title: "No space left on device"
date: 2023-05-10
forum: Hardware
---

### Post by Kova78 on 2023-05-10
Hello,

I replaced an old Seagate 3T HDD with a new 8T model. This HDD I used as storage/backup.

The HDD is for 2/3 empty but, when I try to copy any file, I receive the following error (Ubuntu 22.04.2):

[[img]https://i.ibb.co/8bhZBJB/Screenshot-from-2023-05-10-10-17-09.png[/img]](https://ibb.co/YXrsW6W)

```
sudo du -sh /media/Data3
du: cannot read directory '/media/Data3/.../flac': Input/output error
du: cannot read directory '/media/Data3/../messenger/cache': Input/output error
2.4T    /media/Data3
```

```
sudo df -h /media/Data3
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       7.3T  2.4T  5.0T  33% /media/Data3

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
......
......
#Media2-Data3 partition on /dev/sdc1
/dev/sdc1 /media/Data3 ntfs-3g defaults 0 0

```

[[img]https://i.ibb.co/7jY321L/Screenshot-from-2023-05-10-10-24-19.png[/img]](https://ibb.co/WGxrg2j)

Somebody can help me to understand what's going on?
Thank you in advance

---

### Post by yancek on 2023-05-10
Since it has a windows ntfs filesystem on the partition, does it work in windows?  Do you have windows hibernated?  If so, that may be the problem but I would not expect that error.

---

