---
title: "Wireless loses connection on Macbook 5,5"
date: 2009-11-23
forum: Hardware
---

### Post by theisu on 2009-11-23
Hi,

I have recently installed the 64 bit Karmic on a Macbook 5,5 following the wiki at

[https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic)

The wireless network works after installing the bcmwl-kernel-source package, but the connection to my router (WPA) is lost in irregular intervals, on average maybe every 5 min and networkmanager needs to reconnect.  Sometimes this takes a long time and I need to enter the WPA password.

Has anyone had a similar problem and knows a solution?

Many thanks.

```

lshw -c network

  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:26:bb:16:73:86
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:93200000-93203fff

```

---

