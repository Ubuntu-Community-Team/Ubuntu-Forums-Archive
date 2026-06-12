---
title: "Ubuntu 11.04 on a Lenovo U165 ThinkPad"
date: 2011-05-18
forum: Hardware
---

### Post by ewpaisley on 2011-05-18
Hello Ubuntuists, 

I recently bought a little notebook, which I wanted to run the new Ubuntu on, but I ran into a number of compatibility problems which seem to be related. 

First of all, the Fn/function keys don't work. Not only do they not work, trying to use one (just pressing Fn and f5 to turn on the wireless network card, for instance) instantly freezes the computer and then crashes it. 

Secondly, Ubuntu couldn't run the wireless card. I tried activating it using the the network connection manager, but to no avail.

Is there any way to fix this problem? I'd really love not to be stuck with Windows on it. 

The computer in question is, as the title says, a  Lenovo U165 ThinkPad purchased in Beijing. I understand it isn't available in a lot of markets, but I thought Lenovos were generally Linux-compatible?

---

### Post by ajgreeny on 2011-05-18
Can you show the output of ```
sudo lshw -C network
```which will show what network card you have.

---

### Post by ewpaisley on 2011-05-21
> **ajgreeny said:**
> Can you show the output of ```
sudo lshw -C network
```which will show what network card you have.

OK,

Here we go:

> 
sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:2f:29:3e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: ac:81:12:23:4f:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0300000-d0303fff


Any idea about the Function-buttons?

---

### Post by ewpaisley on 2011-05-22
Anyone?

---

### Post by mahdiar on 2011-06-22
hi go to 
[http://askubuntu.com/questions/43529/my-lenovo-ideapad-u165-wireless-doesnt-work](http://askubuntu.com/questions/43529/my-lenovo-ideapad-u165-wireless-doesnt-work)

---

