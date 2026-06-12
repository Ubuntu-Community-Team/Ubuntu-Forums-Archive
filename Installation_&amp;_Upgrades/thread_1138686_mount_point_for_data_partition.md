---
title: "mount point for /data partition"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by tyhee88 on 2009-04-26
Having only used Ubuntu and Xubuntu inside Wubi the past few months, it's time to try installing Ubuntu 9.04 to my new notebook, dual booting with Vista HP.  The hard drive is big enough I'd like to break it into partitions and would like, among others, a data partition.

I'm new to partitioning and mount points.  What can I use for a mount point for the /data partition?  Will I need to create an empty folder in it first to mount from?  Sorry, as you can tell from the question my knowledge and understanding of mount points is extremely limited.

Thanks.

                                       Bob C.

---

### Post by cariboo on 2009-04-26
I would suggest the first thing you do is to use Vista's diskmanagement tools to resize it partition, instead of using the LiveCD to do it.

As far as mount points are concerned, you can create them after the installation is done. For instance I have an 160Gb SATA drive I use for storage, I mount it in /home/storage using the following line in /etc/fstab:

```
# storage was on /dev/sda1
UUID=7451e251-cb09-4cda-b433-a2768d81affe /home/storage ext4	relatime	0 2
```

You need to create a mount point by making a directory using the mkdir command eg:

```
sudo mkdir /media/data
```

---

