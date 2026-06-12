---
title: "Ethernet adapter Atheros AR8132 don't work"
date: 2010-02-03
forum: Hardware
---

### Post by ibonciecho on 2010-02-03
Hi,

I have a quite new Toshiba laptop (Satellite P505-S8980). I have installed ubuntu 9.10 64 bit. Everything seems to work fine except the internet connections. I have tried to configure both wired and wireless devices but I can't. For the moment I will be very glad if I could configure the wired connection.

```
lspci
``` gives this:

```
Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
```Following these instructions I have been able to install the driver: [http://jan.ucc.nau.edu/wal2/atheros_attansic.html](http://jan.ucc.nau.edu/wal2/atheros_attansic.html)

And now, when I type: ```
dmesg |grep Atheros
```I get this line:

```
[9.029365] Atheros(R) AR8121/AR8113/AR8114/AR8131/AR8132 PCI-E Ethernet Network Driver - version 1.0.1.4
[9.029369] Copyright (c) 2007 - 2009 Atheros Corporation.
```So it seems that the driver is now installed. However, when I try to configure the internet connection I can't.

When I type ```
ifconfig eht0
``` it says:

```
eth0: error fetching interface information: Device not found
```

And any wired connection appears in network-manager. So, I don't really know what's going on and why this device doesn't work. Does someone have ideas for this type of issue?.

I appreciate much your advices.

Thanks.

---

