---
title: "Default Mounting Internal Harddisk Partition?"
date: 2010-11-08
forum: Hardware
---

### Post by cracker89 on 2010-11-08
I installed ubuntu and made 3 partitions. The one for the OS, the swap and the rest into one partition. I did not want my home folder to be formed on that partition, and so I did not set it to home.
Its all good, however, I have to mount the disk once before I can start doing anything on the data therein. Its not too much of a bother, but it would be nice if it could be auto-mounted. 

How can I achieve this?

---

### Post by Hawkoon on 2010-11-08
The file /etc/fstab controls what is being mounted during boot-up, so make an entry there to auto-mount your partition. Also look at the help for fstab.

Just a few pointers...

The format of the entry is:
DEVICE MOUNT_POINT FILE_SYSTEM MOUNT_OPTIONS DUMP_FLAG FS_CHECK_FLAG

The device node (like /dev/sda1) is often used for DEVICE, but using the UUID as reference works more reliable in case you also use removable media. So first you need to find the device node of your partition with
```
sudo fdisk -l
```Now get the UUID of your partition (In my case the device node was sdf7, replace it with your node.)
```
sudo vol_id /dev/sdf7 | grep UUID
```

If you don't know what mount options to use, mount your partition manually and look at the options your system chose
```
mount -l
```Everything else should be obvious from fstab help.

In the end you should have an entry like:
UUID=4A81-2BFC /media/data vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 2

---

### Post by cracker89 on 2010-11-08
Thank you so much! i think its up and working now. that's quite comprehensive. Cheers!

---

