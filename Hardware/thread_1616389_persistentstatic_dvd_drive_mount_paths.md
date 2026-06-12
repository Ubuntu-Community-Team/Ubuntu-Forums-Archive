---
title: "persistent/static dvd drive mount paths"
date: 2010-11-08
forum: Hardware
---

### Post by rhorstkoetter on 2010-11-08
Hi,

I'd like to share my dvd drives across my LAN and I'm terribly failing due to the automount mechanism in Ubuntu 10.10 (afaik introduced with Ubuntu 10.04). 

Problem is: I obviously need the mount paths to be persistent/static in order to utilize net usershare, i.e. /media/sr0 for /dev/sr0 and /media/sr1 for /dev/sr1 respectively. In earlier Ubuntu releases I've been able to easily control this with HAL fdi, which obviously has been replaced by devicekit-disks/udisks.

I don't want to hack my /etc/fstab, but looking forward to a working udev/udisks configuration to achieve this.

Any experiences? Thanks in advance,
R

---

