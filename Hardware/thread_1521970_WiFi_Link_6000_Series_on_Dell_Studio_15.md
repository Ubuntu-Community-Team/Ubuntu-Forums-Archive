---
title: "WiFi Link 6000 Series on Dell Studio 15"
date: 2010-07-01
forum: Hardware
---

### Post by Aybara on 2010-07-01
I just installed 10.04 on my Dell Studio 15, and everything beside Wireless seems to work well. sudo lshw -C network gave the following output:

  *-network DISABLED      
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:a3:30:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:37 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:73:7c:9f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.10.108 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:36 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)

---

### Post by Aybara on 2010-07-02
I see that the firmware for this card is included in /lib/firmware, and dmesg gives some iwl prints that seem to indicate that my machine knows how to talk to the wireless (at work now, so I don't have the exact logs).

I downloaded a new firmmware from the intelwireless-pages. I got a file with the same name but a binary diff, but that didn't do the trick either.

Does the output I posted indicate that this _should_ work? Any ideas what I can try next?

---

