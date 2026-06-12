---
title: "Brother HL-2140 in karmic 64 bit - doesn't show up"
date: 2009-10-31
forum: Hardware
---

### Post by zob on 2009-10-31
My HL-2140 printer doesn't show up in lsusb when I turn it on. What could be the problem?

My lsusb
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0499:1011 Yamaha Corp. P-250
Bus 001 Device 005: ID 0b05:1715 ASUSTek Computer, Inc. 2045 Bluetooth 2.0 Device with trace filter
Bus 001 Device 004: ID 046d:09a6 Logitech, Inc. QuickCam Vision Pro
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It is the same with the printer either on or off.


SOLUTION:

To get a faster boot with a dual-core machine I made a change in /etc/init.d/rc where i changed concurrency=none to concurrency=shell.
Setting it back to concurrency=none solved this problem and another problem I had with Grub.

---

