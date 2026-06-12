---
title: "Gateway M505B - Wireless networking recognition"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by Sarcas on 2006-10-14
I've recently install Dapper Drake on a friend's laptop as a replacement for a dying XP install (for which she has lost the discs). The only trouble I'm having with it is the configuration of the onboard wireless device.

I've run through both of the Wiki's wireless troubeshooting guides, trawled the net via Google but seem to have encountered an unusal problem, and am seeking some help.

Some details: the laptop itself is a [Gateway M505B1]("http://support.gateway.com/s/Mobile/Gateway/M505/3501764nv.shtml") with a Pentium 4M chip. The details of the wireless chip are unknown to me; [the Gateway tech spec sheet]("http://support.gateway.com/s/Mobile/Gateway/M505/3501764sp42.shtml") isn't helpful on the manufacturer, although the laptop page suggests one of the Intel devices.

When running lspci, only the Realtek wired networking card shows up. If I run sudo lshw -C networking, I get
```
 *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:6a:7f:c9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.68 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e8007000-e80070ff irq:10
  *-network
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 1
       resources: irq:10
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:82:30:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=8.10.1 multicast=yes wireless=IEEE 802.11b

``` 

This suggests to me a Lucent driver would be useful, but it also tells me the laptop is treating the single wireless device as *two seperate* devices.

The confusion continues: *ifconfig* shows: 
```
eth1      Link encap:Ethernet  HWaddr 00:02:2D:82:30:D9
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:51320 (50.1 KiB)
          Interrupt:10 Base address:0x100

wifi0     Link encap:UNSPEC  HWaddr 00-02-2D-82-30-D9-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:50858 (49.6 KiB)
          Interrupt:10 Base address:0x100

```

lsmod shows that *orinoco_cs* has been chosen as the appropriate driver for one of these interfaces, but I can't cajole either of them into functioning as I would expect (ie routing packets through a wireless network). I should say the network I'm trying to connect through is WPA encrypted (which was valid for the Windows driver of this wireless card), so I'm attempting to connect with NetworkManager.

Errr...so, I guess I need to ask if anyone has any ideas? Sorry to flood the forum with information (especially of a wireless nature..but I thought it might be more of a hardware rather than a software/connection problem).

Sarcas

---

### Post by Sarcas on 2006-10-15
So, since no one has ben able to give me any clues about this so far (and I don't blame anyone - it's a tricky question and no doubt), do people feel this question might be better suited to the Wireless forum? I don't like to cross post, but maybe that's a better place for it.

Thanks in advance,
  Sarcas

---

