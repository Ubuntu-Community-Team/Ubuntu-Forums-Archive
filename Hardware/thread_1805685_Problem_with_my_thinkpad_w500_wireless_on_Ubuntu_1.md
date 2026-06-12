---
title: "Problem with my thinkpad w500 wireless on Ubuntu 11.04"
date: 2011-07-16
forum: Hardware
---

### Post by kieubang on 2011-07-16
Hi,
I am having wireless problem on my thinkpad W500. I can see wireless but I am unable to connect.
My Thinkpad W500 wireless version is: Intel Wireless WiFi 5100AGN, 5300AGN, and 5350AGN
Could you please help me resolve the problem.
Thanks

---

### Post by kieubang on 2011-07-17
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:27:13:65:80:93
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.8-3 ip=192.168.1.3 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fc200000-fc21ffff memory:fc224000-fc224fff ioport:1800(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:92:60:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=8.83.5.1 build 33692 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f4200000-f4201fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

