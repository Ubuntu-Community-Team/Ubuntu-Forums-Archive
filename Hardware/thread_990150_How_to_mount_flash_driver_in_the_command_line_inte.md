---
title: "How to mount flash driver in the command line interface(CLI)"
date: 2008-11-22
forum: Hardware
---

### Post by philidox on 2008-11-22
I have always wondered how in the world do you mount a flash drive in the cli.  It too easy in the GUI enviroment but not so easy in CLI.  I look at the man for mount but I didnt see anything that specifically stated how to.  Please help

---

### Post by taurus on 2008-11-22
Assuming your external drive is /dev/sdb1 and it is fat32 filesystem, you would do something like

```
sudo mkdir /media/external  <-- You only have to run this one to create a mount point.
sudo mount -t vfat /dev/sdb1 /media/external -o umask=000
df -h
```
And if you want to remove it, unmount it first before you unplug it.

```
sudo umount /media/external
df -h
```

---

### Post by philidox on 2008-11-23
Thanks a lot!!! But the only thing is I don't completely understand whats happening.  How do you know what dev to mount from.  In the example you gave me you did /dev/sdb1. Did you just arbitrarily chose /dev/sdb1 or what?

---

