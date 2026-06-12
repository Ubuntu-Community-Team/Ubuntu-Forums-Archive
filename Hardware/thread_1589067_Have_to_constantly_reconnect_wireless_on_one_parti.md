---
title: "Have to constantly reconnect wireless on one particular network"
date: 2010-10-05
forum: Hardware
---

### Post by Lightbreeze on 2010-10-05
The problem: I'm using wireless to connect to the internet, but it unpredictably stops working. When this happens the network manager shows nothing wrong but no application can access the internet. I have to reconnect to the network before I am able to use the internet. Sometimes, and frustratingly, I will only be able to load a single page before it stops working again. Other computers on this network don't have this problem and my computer works flawlessly on other networks.

I'm using Ubuntu 10.10 RC, but I had this problem before upgrading.

The command lshw -C network gives me
```
*-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:4d:9f:57
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=228.61.2.24 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:fe1fe000-fe1fffff
```

---

