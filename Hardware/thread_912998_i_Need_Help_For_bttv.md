---
title: "i Need Help For bttv"
date: 2008-09-07
forum: Hardware
---

### Post by ynn_foxman on 2008-09-07
[PHP]root@ynnfoxman-desktop:~# dmesg | grep bttv
[   49.870420] bttv: driver version 0.9.17 loaded
[   49.870425] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   49.870483] bttv: Bt8xx card found (0).
[   49.870529] bttv0: Bt878 (rev 17) at 0000:03:07.0, irq: 21, latency: 32, mmio: 0xfdbff000
[   49.870609] bttv0: subsystem: fefe:0001 (UNKNOWN)
[   49.870613] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   49.870632] bttv0: gpio: en=00000000, out=00000000 in=00f5fffe [init]
[   49.870660] bttv0: tuner absent
[   49.870672] bttv0: add subdevice "dvb0"
[/PHP]

and program me tv say no tuner now what can i do ?

---

### Post by ynn_foxman on 2008-09-07
no body can help me

---

### Post by ynn_foxman on 2008-09-16
please any help

---

### Post by Tim Prosser on 2008-10-20
> **ynn_foxman said:**
> [PHP]root@ynnfoxman-desktop:~# dmesg | grep bttv
[   49.870420] bttv: driver version 0.9.17 loaded
[   49.870425] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   49.870483] bttv: Bt8xx card found (0).
[   49.870529] bttv0: Bt878 (rev 17) at 0000:03:07.0, irq: 21, latency: 32, mmio: 0xfdbff000
[   49.870609] bttv0: subsystem: fefe:0001 (UNKNOWN)
[   49.870613] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   49.870632] bttv0: gpio: en=00000000, out=00000000 in=00f5fffe [init]
[   49.870660] bttv0: tuner absent
[   49.870672] bttv0: add subdevice "dvb0"
[/PHP]

and program me tv say no tuner now what can i do ?


I have the same tuner - in fact I have two - and they've been working for a looooong time with Mythtv/Ubuntu.

This weekend, however, they stopped working after I updated to the latest kernel for Hardy (2.6.24-21), and I can't for the life of me work out why.  I've tried reverting to 2.6.24-19 but that had no effect.  Same message - "tuner absent".

So can I say....me too!  Will let you know if I get it working - will try Intrepid first...

---

