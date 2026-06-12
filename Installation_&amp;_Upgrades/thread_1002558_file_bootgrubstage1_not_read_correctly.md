---
title: "file /boot/grub/stage1 not read correctly"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by nicholasbgr on 2008-12-05
Well, basically I screwed my ubuntu instalation. I resized 2 partitions and then I rebooted, but grub was not loading and giving error 17. I booted the Live CD and tried reinstalling grub, but every attemp resulted in "file /boot/grub/stage1 not read correctly". Any idea how can I get it to work again?

Ps: I tried to fix the boot using the SuperGrub live cd, but it didn't work. At least I've got to boot my windows partition lol.

---

### Post by caljohnsmith on 2008-12-05
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo fsck -y /dev/sdXY
```
And please post the results. If that completes successfully then also post:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```

---

