---
title: "changing ownership on HD"
date: 2017-03-26
forum: Hardware
---

### Post by chadrohlfsen on 2017-03-26
Hello, I have a partitioned laptop with 3 HDs. One, is set up at fat32 and is what I'm using to store extra files from Ubuntu. Unfortunately, the owner is set to root and I am unable to save anything there due to permissions. What do I need to do to change ownership and begin saving my data in that HD? Thanks!

---

### Post by TheFu on 2017-03-26
For non-Linux file systems, permissions are controlled by the mount options.

```
mkdir /mnt/$LABEL3
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3

```
where
* UID is my userid (a number - 1000)
* GID is my primary groupid (a number - 1000)
* LABEL3 is the partition label - UUID or device names can also be used, but for portable disks, I find a unique label to be the easiest.

Make sense?

---

### Post by Dennis N on 2017-03-27
If you mount your HD using /etc/fstab, you can set owner and group there so it is ready to go. A guide is here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Something like:
```
UUID=94C3-7016  /mnt/data1       vfat    defaults,uid=1000,gid=1000      0       2
```
should suffice. 
Get your user's uid and gid from the **id** command.

---

