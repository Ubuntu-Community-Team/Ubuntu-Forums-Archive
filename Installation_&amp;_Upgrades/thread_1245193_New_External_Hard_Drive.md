---
title: "New External Hard Drive"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by CarlosinFL on 2009-08-20
I purchased a new 500 GB external hard drive enclosure which has a USB 2.0 interface to my 9.04 PC. The hard drive is fresh and unformatted. I know how to format the hard drive via 'fdisk' and then create the file system using:

```
mkfs.ext4 /dev/sdd1
```

My question is when I have the drive powered on and connected to my PC, I don't want to see it as a removable device on my desktop. I want it to be added to /etc/fstab and mounted to a directory I just created called /share.

Can someone please tell me what I need to do to mount this permanently on my system?

---

### Post by ronparent on 2009-08-20
Just add it to /etc/fstab as you said. The form of the line is very simular to the arguments in a mount command without the mount. The mounting options need not be entered if you can live with the defaults - otherwise you can experiment with using options simular to mounting instructions already present in fstab. Just be sure you have created a '/share' for each partition you want to mount.

---

