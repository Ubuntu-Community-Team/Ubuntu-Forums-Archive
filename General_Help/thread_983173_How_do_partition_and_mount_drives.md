---
title: "How do partition and mount drives?"
date: 2008-11-15
forum: General Help
---

### Post by grs on 2008-11-15
I have a disk with the following specs:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

What I want to do is create two partitions one of about 100GB and the other to use the rest of the space.
I then want to mount the smaller partition at /mnt/mp3 and the larger one I want to mount at /home
I've looked through a few guides but I can't seem to get them to mount on startup.

---

### Post by drs305 on 2008-11-15
You state you want to create two partitions but can't get them to mount. Have you already created the partitions? 

Do you want them to mount automatically on boot? If so, you can modify your fstab entries.

Please post:
```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

If you haven't created the partitions, ubuntu uses gparted. It is accessed via System, Administration, Partition Editor. (It cannot work on mounted partitions but you can unmount them from within gparted so long as they are not system-related partitions.)

For how to move an existing /home to a new partition, see:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Glubbdubdribian on 2008-11-15
If you go into System>pref>session then add a comand tht says sudo umount -a /partition_name then the should mount at startup i think.

---

### Post by grs on 2008-11-15
Got it working now. Thanks anyway.

---

