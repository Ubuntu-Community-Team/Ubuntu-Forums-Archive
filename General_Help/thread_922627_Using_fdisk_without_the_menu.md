---
title: "Using fdisk without the menu"
date: 2008-09-17
forum: General Help
---

### Post by Mardok45 on 2008-09-17
I'm looking for a way to call fdisk without having to use the menu.

What I mean is instead of calling fdisk this way...

```
fdisk /dev/hda
```

... and start typing in the commands through the menu, is there a way to format, create a partition (in NTFS) and flag it as bootable all by calling fdisk and passing some parameters?

The reason I'm asking is that I'm using FOG to reimage PCs at my university and would like to run fdisk when I boot the PC with a Linux kernel (debug mode) after it is wiped.

If this isn't possible, can GParted automatically create a partition as NTFS on boot?

Thanks for any help.

---

### Post by fsmithred on 2008-09-19
Use sfdisk, but be careful, because it doesn't number cylinders the same as fdisk. One of them starts counting at zero, and the other starts at one.

---

### Post by bodhi.zazen on 2008-09-19
fdisk / sfdisk do not format partitions. To create a filesystem you need mkfs, or in your case, mkfs.ntfs

[http://linux.die.net/man/8/mkfs.ntfs](http://linux.die.net/man/8/mkfs.ntfs)

---

