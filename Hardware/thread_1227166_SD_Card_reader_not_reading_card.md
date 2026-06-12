---
title: "SD Card reader not reading card"
date: 2009-07-30
forum: Hardware
---

### Post by billybag on 2009-07-30
I have an HP Pavilion here and everything works fine out of the box with ubuntu hardy, except that i cannot get the SD Card reader to read an SD card. The card is not locked and it works under windblows.

```
 $ dmesg | tail -n 10
[   34.812040] eth1: no IPv6 routers present
[   54.405348] CPU0 attaching NULL sched-domain.
[   54.405353] CPU1 attaching NULL sched-domain.
[   54.407784] CPU0 attaching sched-domain:
[   54.407787]  domain 0: span 0-1 level MC
[   54.407789]   groups: 0 1
[   54.407794] CPU1 attaching sched-domain:
[   54.407796]  domain 0: span 0-1 level MC
[   54.407798]   groups: 1 0
[  155.566798] mmc0: error -84 whilst initialising SD card

```

is this a hardware problem? thanks


EDIT: It appears to be the card. I tried putting another card (SanDisk) and it worked. THe original is a Kingston

---

