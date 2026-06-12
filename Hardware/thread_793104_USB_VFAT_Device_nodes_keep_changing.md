---
title: "USB VFAT Device nodes keep changing"
date: 2008-05-13
forum: Hardware
---

### Post by kon5ad on 2008-05-13
Hi,

I am trying to mount 2 500gb USB external drives formatted as vfat.

They are both auto mounted if I hot plug them but I would like to override the automount to set umask and ownership my way. I tried making fstab entries but the problem is that the device node (sdd1, sdc1,...) to which they get assigned is not guaranteed to be the same each time, and really seems to vary between restarts. They are vfat so I cannot mount them by label. Is there some other way to mount these fatties using some other identifier, or force them to always be assigned to the same device node?

Would really appreciate some help, not keen on going to ext3 as the whole idea is that they are portable and platform independent.

---

### Post by kon5ad on 2008-05-14
Another option would be if someone could tell me how I can override the permissions and ownership the automounter sets up when mouting these devices.

---

### Post by nick_h on 2008-05-14
You should be able to mount them by label, but you could also mount them by uuid.

To get the uuid, type:
```
ls -al /dev/disk/by-uuid/
```

[RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[How to fstab](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by kon5ad on 2008-05-15
Excellent, worked perfectly first time. I had seen this method before but for some reason thought it was only applicable to ext3 filesystems.

I found the UUID by your method above:

```
ls -l /dev/disk/by-uuid/
```

I first tried to mount manually

```
mount -t vfat -U 0090-B78B /media/mountpoint
```

and after it all worked perfectly added it to the fstab

```
UUID=0090-B78B  /media/mountpoint  vfat rw,gid=1006,uid=1000,umask=0007 0 0
```

And now I am all happy. Thanks for the help.

---

