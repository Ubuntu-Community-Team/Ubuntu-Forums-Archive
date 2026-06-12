---
title: "IT9135 install divers"
date: 2011-12-15
forum: Hardware
---

### Post by DJJo on 2011-12-15
Hi

i just bought a DVB-T adapter. I had it working in 11.04. it was not that hard to install then. I think i dit not blidt the drivers.

but becouse of some trouble with my video drivers i had to upgrate to 11.10. nou i can not install then any more.

I tried [this.]("http://linuxtv.org/wiki/index.php/ITE_IT9135") [and this]("http://linuxtv.org/wiki/index.php/Kworld_UB499-2T") but it did not work.
when i am building the drivers (with make) it gifs a error.
```
 fatale fout: linux/smp_lock.h: Bestand of map bestaat niet

```
(Dutch translation: file of map does not exists)
I am running x64 on ubuntu 11.10

Update I found the solution, after a kernel update you have toe reinstall the v4l-dvb.
suddenly i found the solution [here]("http://wiki.ubuntuusers.de/v4l-dvb")

---

