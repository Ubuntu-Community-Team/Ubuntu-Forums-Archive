---
title: "Help upgrade from gutsy now get grub error 2"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by mjetpax on 2009-07-01
I really hope someone can help me with this... I upgraded my server from gutsy 7.10 to Hardy 8.04 and now when it boots I get "Error 2: Bad file or directory type"

then I hit <enter> to continue and I can choose from a list of kernels.

Kernel 2.6.24-16-server
Kernel 2.6.24-16-server (recovery mode)
Kernel 2.6.24-14-server
Kernel 2.6.24-14-server (recovery mode)

The first two won't boot, but the second two boot just fine. I have tried the following with no results.

sudo grub

> root (hd0,0)
> setup (hd0)
> quit

then I have tried with rebooting the computer and with a sudo update-grub then reboot. It's really frustrating. I only have one hard drive so it would seem that if one kernel boots the other should too.

Help....

Thanks.

---

### Post by mjetpax on 2009-07-01
AH HA!!!! I had to edit the grub file /boot/grub/menu.lst and change "default 0" to "default 2" now the kernel on the list that works is the default kernel at boot up.

Thanks Ubuntu online documentation: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

