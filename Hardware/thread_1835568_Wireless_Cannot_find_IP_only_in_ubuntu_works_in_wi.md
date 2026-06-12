---
title: "Wireless Cannot find IP only in ubuntu works in windows"
date: 2011-08-29
forum: Hardware
---

### Post by buntu_hugenewbie11 on 2011-08-29
I have a Dell e6510 running Lucid 64 bit. (2.6.32-33
My wireless was working until recently.
The card I have is:
Dell Wireless 1501 802.11b/g/n Half Mini Card
I can see wireless networks but when I connect the networking interface hangs on obtaining an ip address.
I have tried this on multiple wifi networks and have also managed to get those same networks to work on the same machine in windows so it does not seem to be a hardware issue or a network issue.
I really need to have wifi as I will only have a wired connection for the next 24 hours. Please help me if you can.

lshw produces the following output:
     description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 78:e4:00:89:3d:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:e6e00000-e6e03fff

---

### Post by buntu_hugenewbie11 on 2011-08-30
Anybody?

---

