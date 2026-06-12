---
title: "help on a laptop dule boot drive"
date: 2009-03-04
forum: Hardware
---

### Post by Cahan on 2009-03-04
Howdy and sorry on my spelling at times here and now to my problem

a number of weeks ago I was setting the mount point for the windows side of my hard drive and typed in the wrong info now I can not even mount it how can I get and where to find the settings so I can undo what I did so I can get the windows side back and what I did was copy what was in the info window when the drive was mounted

what I get when I go to mount 

mount_point cannot contain the following charaers: newline, G_DIR_SEPARATOR (usually /)

Thanks for any help that I may get
Pat

---

### Post by khelben1979 on 2009-03-04
```
df -h
```
lists all your devices.

From there you should see what the device the harddrive is on and then you use the:
```
mount -t [filesystem] /dev/[harddrive] /mnt/[mountpoint]
```

Also:
```
man mount
```
describes how you use the mount command and what filesystems which is available for you.

Did that help?

---

