---
title: "WiFi on Lenovo T400 - OK with 8.10 disk, no good with install"
date: 2008-11-17
forum: Hardware
---

### Post by JWatch on 2008-11-17
My WiFi works fine when I boot the 'live CD' of Ubuntu 8.10 on my Lenovo T400.  However, when I run the installed SW the WiFi is not even present (no icon in the task bar, no connectivity).  

The WiFi light is on.  lshw shows wifi is active.  I tried configuring the wireless through the network settings, but it is as if the wireless is not there.  Again, the WiFi connection and icon works great if I boot from the CD.

Any magic to make it work with the normal install?

  *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:da:20:af
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:b1:43:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:ba:c7:c8:3f:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

