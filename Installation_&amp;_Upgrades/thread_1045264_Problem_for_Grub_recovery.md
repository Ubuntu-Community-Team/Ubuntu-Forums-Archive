---
title: "Problem for Grub recovery"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by seraphlz on 2009-01-20
Hello everyone, I reinstalled windows xp and tried to recover Grub by live dvd (ubuntu 8.04 x64). But it failed as follows:

grub> find /boot/grub/stage1
find /boot/grub/stage1
(hd0,11)
grub> root (hd0,11)
root (hd0,11)
grub> setup (hd0)
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,11)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition  

How to solve this problem?

---

