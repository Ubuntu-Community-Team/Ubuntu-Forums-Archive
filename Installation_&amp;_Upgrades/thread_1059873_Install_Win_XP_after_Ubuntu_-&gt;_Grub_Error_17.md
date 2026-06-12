---
title: "Install Win XP after Ubuntu -&gt; Grub Error 17"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by miaerbus on 2009-02-04
I tried to install Win XP on my Ubuntu machine. On boot I get Error 17. So I tried following:

Alt+F2
$ sudo su -
$ fdisk -l /dev/sda

```
omitting empty partition

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Unites=cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x94e494e4

Device     Boot  Start End   Blocks      Id  System
/dev/sda1  *     1     1381  10440328+   7   HPFS/NTFS
/dev/sda2        1382  7752  48162870    5   Extended
/dev/sda3        7604  7752  1124518+    82  Linux Swap / Solaris
/dev/sda5        1382  7455  45913707    83  Linux
/dev/sda6        7455  7604  112 4518+   82  Linux Swap / Solaris
```


$ grub
# root (hd0,5)
# setup (hd0)

```
Checking if "/boot/grub/stage1" exist... yes
Checking if "/boot/grub/stage2" exist... yes
Checking if "/boot/grub/e2fs_stage1_5" exist... yes

Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst" ... failed

Error 12: Invalid device requested
```

---

### Post by caljohnsmith on 2009-02-04
How about trying instead:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
```
Note that Grub's numbering begins with zero, not one, so (hd0,4) is sda5. Let me know how that goes.

---

