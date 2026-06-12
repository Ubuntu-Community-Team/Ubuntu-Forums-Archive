---
title: "wireless driver"
date: 2012-06-10
forum: Hardware
---

### Post by TheRacerX on 2012-06-10
I have a Toshiba Tecra S4 laptop with a Broadcom 4311 chipset wireless adapter and i just install Ubuntu 12.04 64bit, but for some reason when i activate the wireless driver it doesnt work, ive tried everything to get it working but nothing works, anyone have any ideas

---

### Post by johnathansmith on 2012-06-10
What do you mean "doesnt working ", you didn't see the networks?

---

### Post by TheRacerX on 2012-06-10
no the OS doesn't see the hardware even though i activated the driver in the additional drivers application

---

### Post by johnathansmith on 2012-06-10
What gives 

```
 lshw -C network 

```

---

### Post by TheRacerX on 2012-06-22
theracerx@Dante:~$  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:b7:91:54:57
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.5-1 latency=0 multicast=yes port=twisted pair
       resources: irq:45 memory:ffce0000-ffcfffff ioport:cfe0(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:ffafc000-ffafffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan1
       serial: 30:46:9a:2f:aa:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.2.0-26-generic firmware=1.3 ip=192.168.0.103 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

