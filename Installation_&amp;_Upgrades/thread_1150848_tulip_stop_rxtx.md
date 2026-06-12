---
title: "tulip_stop_rxtx"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by eeyore357 on 2009-05-06
First off let me say that I am new to Linux. I made the switch about a month ago. OK here is the problem. I upgraded to 9.04 yesterday and today my internet connection is slower than dial-up and seeing 0000:00:0b:0 tulip_stop_rxtx failed (CSR5 0xfc06c012 CSR6 0xff974111)  Anyone know whats going on? I haven't tried restarting or anything yet.

---

### Post by eeyore357 on 2009-05-07
If I restart or disable and then enable networking the issue fixes itself for a little while.:confused:

---

### Post by BOK on 2010-07-28
Any fix yet? Having the same error here on 10.04 with kernel 2.6.34-020634:
```

[   73.922338] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   73.922999] tulip0:  MII transceiver #1 config 1000 status 786d advertising 0501
[   73.935793] net eth0: ADMtek Comet rev 17 at Port 0x1800, 00:30:05:54:fe:60, IRQ 11
[   88.737001] 0000:00:06.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   88.737015] net eth0: Setting full-duplex based on MII#1 link partner capability of 45e1
```
The Tulip-driver is over 3 years old and Launchpad shows lots of related bugreports unresolved (e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500963](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500963))

---

