---
title: "Root Filesystem problems"
date: 2008-06-30
forum: Hardware
---

### Post by burning_man13 on 2008-06-30
When my system tries to do the automatic check of drives it fails at 4% every time... Then it says that my Root Filesystem is in Read only so it can't do anything and I have to do a manual fsck, first of all I don't know how to do a manual fsck, secondly with my root filesystem being in read only I can't install any other programs or anything of that nature... What can I do to fix this?

---

### Post by vanadium on 2008-06-30
This sounds bad and may suggest a failing hard drive. Anyway, a possibility to do a manual file check is to boot from the live CD. To check a drive, it must first be unmounted. You will need to determine the device name of the partition you want to check. It appears in the output of

```
sudo blkid
```

Assuming it is /dev/sda1, then checking will go like (first unmounting, then checking)

```

sudo umount /dev/sda1
sudo fsck /dev/sda1

```

If you manage to repair all, but the problem reappears, then there is a hardware problem (disk, controller, ...)

---

