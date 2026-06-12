---
title: "initramfs unpacking failed"
date: 2020-10-12
forum: Hardware
---

### Post by jca4658 on 2020-10-12
Computer: Dell 9020, newly installed Lubuntu 20.4, console screen at startup "initramfs unpacking failed  failed code" (or something like that). Starts up OK but slow (> 30 sec). How to fix? TIA

---

### Post by CelticWarrior on 2020-10-12
Welcome.

~30 seconds isn't a problem at all. And depending on the hardware it may be considered excellent even. Of said hardware we know nothing. "Dell 9020" is almost meaningless - is it the desktop Dell Optiplex 9020? If so, how old? - and we know nothing about that one piece responsible for the performance or lack of it when booting, the drive where the OS is installed. HDD or SSD?

---

### Post by VMC on 2020-10-12
On the unpacking failed, see my bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660)

---

### Post by jca4658 on 2020-10-12
Fixed with:
   [B]sudo nano etc/initramfs-tools/initramfs.conf, changed "COMPRESS=lz4" to "COMPRESS=gzip", then, sudo update-initramfs -u.
Many thanks @[/B]**[[B][COLOR=#000000]VMC[/COLOR]**]("https://ubuntuforums.org/member.php?u=566482") 

[/B]

---

