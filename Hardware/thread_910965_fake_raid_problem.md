---
title: "fake raid problem"
date: 2008-09-05
forum: Hardware
---

### Post by nikkon on 2008-09-05
hello everybody.
i'm a new ubuntu user (in the past i used centos and freebsd).
my problem is this:
i have an asus a8v MB with promise raid controller.
i tryed to install ubuntu 8.04 lts on a strip raid configuration.(2x sata hdd)
unfortunately was imposible to make it.hare are my steps:
-i booted from the livecd and i installed dmraid.
-i started fdisk on/dev/mapper/pdc_xxx and i made 4 partitions,including swap (82)
-i restarted te computer and i started the installer
- when hes trying to format the partitions the installer crashes.

in the end i installed on another sata hdd,was ok, but now it's imposible to mount the /dev/mapper/pdc_xxx on it.

any ideas?

---

