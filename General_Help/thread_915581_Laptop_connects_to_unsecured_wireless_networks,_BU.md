---
title: "Laptop connects to unsecured wireless networks, BUT doesn't connect to secured ones"
date: 2008-09-10
forum: General Help
---

### Post by etereo on 2008-09-10
Hi,

I've recently bought a laptop (hp dv2000) and I have an issue connecting to secured wireless networks using Hardy.

If I set my wireless modem security to "none", I can connect fine, but when I switch the security on (WPA personal), I still see the network listed in network-manager, and it's recognized correctly as a secured (WPA personal TKIP).  However I can't connect to it.

It seems to try to, the icon turns to 1 green circle (which I guess is trying to get the IP from my DHCP) but never gets connected.

Any help would be appreciated!



PS: Here's the output of "lshw -C network"
PPS: I'd be happy to provide any other output



etereo@etereo-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:4d:df:77
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.116 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:fe:c8:32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

