---
title: "xD card on Ubuntu 8.10?"
date: 2008-12-15
forum: Hardware
---

### Post by NightBat on 2008-12-15
Hello all!

I install Ubuntu 8.10 on laptop Acer Extensa 5630.
I has found out that a microphone and xD cards reader do not work.
Both these things completely work in Win XP which installed as second system.

The system see cards reader as:

> lspci -nn | grep 'O2 Micro'

0d:06.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 01)
0d:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0d:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 03)


I have only xD card from my Olympus Camera, any advice how get it work?

---

### Post by bobya on 2009-05-07
Hi I have the same problem but on MSI GX700 laptop.
the command you used issues the following:

> 01:04.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
01:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
01:04.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)

I am using jaunty(9.04) and the card reader still doesn't recognize my SD-card. I remember it working in 7.04.
Does anybody has a solution?

---

### Post by devter on 2009-05-07
Hello, i have the same problem , have Thosiba Satelite U-400. 
S.O: Ubuntu Jaunty 9.04.



```
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```

Gretings.:(

---

### Post by iSoc on 2009-05-17
Yes = problem.

> 0a:01.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
0a:01.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0a:01.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)

---

### Post by Zoltair Wright on 2009-05-17
I have the exact same hardware in an EeePC 900 running 9.04, and my card reader isn't working either. It won't even show up in the file manager.

```
0a:01.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
0a:01.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0a:01.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01) 

```

---

### Post by NightBat on 2010-05-31
Hello all!

Now for this problem I opened a bug report! :)
Please, if you want this problem solved, join to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518465](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518465)

---

