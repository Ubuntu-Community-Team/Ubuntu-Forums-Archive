---
title: "Suspend not working since Intrepid install"
date: 2009-04-04
forum: Hardware
---

### Post by prostar on 2009-04-04
I had everything working fine with Hardy, including ACPI alarm wakeup, suspend, hibernate, etc... I figured since it wasn't broke, I'd upgrade and see if I could fix it.

I've read many of the suspend issue posts dating back to 2007. I remember I did have to do some work in Hardy to make it suspend, but it was a very simple change. I can not seem to reproduce that success. I believe it may be related to the s2ram removal. I have my previous /etc/* if someone knows the magic parts to look at. Here is the dmesg output that seems to be important, but I don't know what tty* would have to do with anything:

```
[    1.476442] cpuidle: using governor ladder
[    1.476444] cpuidle: using governor menu
[    1.476858] TCP cubic registered
[    1.477132] registered taskstats version 1
[    1.477281]   Magic number: 5:619:225
[    1.477315] tty ttyu9: hash matches
[    1.477324] tty ttyrc: hash matches
[    1.477439] rtc_cmos 00:04: setting system clock to 2009-04-04 11:12:29 UTC (1238843549)
[    1.477442] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.477443] EDD information not available.
[    1.477482] Freeing unused kernel memory: 540k freed
[    1.477743] Write protecting the kernel read-only data: 4352k
[    1.621155] fuse init (API version 7.9)
```

Specs:
Intrepid, fresh install
AMD 64 Dell E521
Gnome
2.6.27-11-generic
It was all working in Hardy!

---

