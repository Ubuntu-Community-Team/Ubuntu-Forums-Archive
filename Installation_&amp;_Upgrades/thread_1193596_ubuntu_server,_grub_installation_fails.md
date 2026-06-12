---
title: "ubuntu server, grub installation fails"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by metalfan_ on 2009-06-21
Hi,

ive installed grub with the default installer, ive choosen lvm, partitioning by the ubuntu-installer, encrypted home.

the drive already contained some linux system, but since i did choose to use the full drive for ubuntu i thought this was of no concern.

after rebooting grub stops with some error, so i started the rescue system, mounted the root partition and ran:

```

grub-install /dev/sda
(the system contains one ide hdd, one dvdrom)

error:
the file /boot/grub/stage2 not read correctly

```


what now?

---

### Post by metalfan_ on 2009-06-22
I did the install again, this time it failed with error 2.

After that i disconnected the dvdrom, connected the harddrive to the other ide port and it just booted.

Maybe some weirdness with the bios, its a VIA Epia M-II Board.

---

