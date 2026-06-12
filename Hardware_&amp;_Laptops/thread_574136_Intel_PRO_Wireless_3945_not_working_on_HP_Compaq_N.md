---
title: "Intel PRO Wireless 3945 not working on HP Compaq Nx7300 ubuntu 7.04 Feisty"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by smk666 on 2007-10-12
Hi. As above, I can't get this thing up and running. I tried almost everything found on forums, but there's still no effect. The adapter is running under M$ WinXP, so it isn't hardware issue. Can anyone help me how to set this thing up? Assume that I have freshly installed Ubuntu. Thanks in advance :)

---

### Post by Lambert on 2007-10-12
> **smk666 said:**
> Hi. As above, I can't get this thing up and running. I tried almost everything found on forums, but there's still no effect. The adapter is running under M$ WinXP, so it isn't hardware issue. Can anyone help me how to set this thing up? Assume that I have freshly installed Ubuntu. Thanks in advance :)

Post output of the following terminal commands.

```

sudo lshw -C network

lsmod | grep ipw

dmesg | grep 3945

```

---

### Post by smk666 on 2007-10-12
```
 *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:f4000000-f4000fff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:a4:de:00:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=158.75.236.180 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f4108000-f4109fff irq:16

```
```

smk@smk-laptop:~$ lsmod | grep ipw
ipw3945               118816  1 
ieee80211              34760  1 ipw3945

```
```
[    0.339451] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.564000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.564000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.748000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.640000] ipw3945: Radio Frequency Kill Switch is On:

```
So that's it, but while it's looking good, it doesn't work :/
None of the connection managers finds any wireless card installed :/

---

### Post by Lambert on 2007-10-12
From a terminal move to the sbin directory.

```

cd /sbin

```

Then type ls to show what files are in this directory. Look for a file named ipw3945dsomethingsomethingsomething. type it out and hit enter. What's the output? now open a manager and see if you see the wireless card to configure.

---

### Post by smk666 on 2007-10-13
```
 sudo ipw3945d-2.6.20-16-generic
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-10-13 15:09:43: ERROR: ipw3945d already running.  If ipw3945d is not running then you
need to remove '/var/run/ipw3945d.pid' and try again.

```

So... everything should run smoothly, but WiFi Radar isn't even starting and netapplet doesn't see my WiFi card :/
I tried to remove this file and restart daemon, however it haven't helped :/

---

### Post by mkw87 on 2007-10-15
I'm having the same problem, although my output was as follows:

```

matthew@bangarang:/sbin$ ipw3945d-2.6.22-14-generic
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-10-15 19:22:37: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```

Any ideas?

---

