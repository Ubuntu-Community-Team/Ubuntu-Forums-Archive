---
title: "No wired connection after upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by GabrielWolff on 2009-10-30
After upgrading my wired connection (eth0) is greyed out and says "device not managed". Before, I just had to plug in and it would run.

Any suggestions?

Thanks :)

G

P.S.: Just in case:```
gabriel@gabriel-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e4:ee:e8
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:98:2f:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.2.11 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:edf00000-edf00fff
gabriel@gabriel-laptop:~$ 

```

---

