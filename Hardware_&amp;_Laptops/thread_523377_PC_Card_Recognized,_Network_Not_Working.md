---
title: "PC Card Recognized, Network Not Working"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by 0graham0 on 2007-08-11
Hi,

I have a Dell Latitude LM running Xubuntu (although Xfce is not running yet, so I guess that makes it regular Ubuntu?) I have a Hawking Technology PN652TX Ethernet PC Card plugged in. I enter:```
lshw
``` The PC card appears to be recognized, but the network is disabled.```
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: eth0
...
configuration: braodcast=yes driver=pcnet_cs multicast=yes
```

If i enter ifconfig the eth0 adapter doesn't show up, but if i enter "ifconfig eth0" I recieve```
Link encap:Ethernet HWaddr 00:E0:98:AD:B2:2D
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:3 Base address:0x300
```

Any ideas on how to get the internet/network up and running?

Thanks

---

### Post by moore.bryan on 2007-08-11
*what's the output of ```
lspci
```?*

---

### Post by 0graham0 on 2007-08-11
I'll let you know as soon as I get the system up and running again (next 1/2 hour or so)

---

### Post by 0graham0 on 2007-08-11
LSPCI reads:> 00:00.0 Host Bridge: Intel Corporation 430MX - 82437MX Mob. System Ctrir (MTSC) & 82438MX Data Path (MTDP) (rev 02)
00:01.0 Bridge: Intel Corporation 430MX -82371MX Mobile PCI I/O IDE Xcelerator (MPIIX) (rev 03)
00:02.0 VGA compatible controller: Neomagic Corporation NM2093 pMagicGraph 128ZV] (rev 02)
00:04.0 PCMCIA bridge: Cirrus Logic CL 6729 (rev ee)

---

### Post by moore.bryan on 2007-08-11
*that's it?  you have no network card according to that printout...*

---

