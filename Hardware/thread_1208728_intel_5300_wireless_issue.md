---
title: "intel 5300 wireless issue"
date: 2009-07-09
forum: Hardware
---

### Post by P_S on 2009-07-09
I have a dell e6400 my wireless card is an an intel 5300, the problem I have is when I start my laptop with the wireless switch turned off and after the system boots I switch the wireless to on the wireless doesn't work.  I checked with lshw -C network and I see:

 *-network
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:0d:55:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:fe:91:a7:3c:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

But when I boot the OS with the switch turned on I don't have any problem.

Any ideas ?

Thanks

---

