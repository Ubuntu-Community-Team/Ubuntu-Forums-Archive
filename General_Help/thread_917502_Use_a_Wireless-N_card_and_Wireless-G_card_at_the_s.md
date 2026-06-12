---
title: "Use a Wireless-N card and Wireless-G card at the same time?"
date: 2008-09-12
forum: General Help
---

### Post by ubuntuforums on 2008-09-12
I have a Linksys Wireless-G card, and a Linksys Wireless-N (WMP300N) card, if I install Ubuntu with the Wireless-G card installed in the computer, then it is recognized and used immediately. To get my Wireless-N card working I have to use ndiswrapper.

Now I'd like to have them both working and be able to connect to a different wireless network with each one. But if I have the Wireless-G card in my computer when installing Ubuntu, then my Wireless-N card will not work no matter what I've tried. So I install Ubuntu with the Wireless-N card then use ndiswrapper and it works. But when I put in the Wireless-G card, its not recognized automatically anymore...

Anyone have any suggestions/comments/insults/lol?

---

### Post by Zorael on 2008-09-12
What is the output of the following, when you have both cards connected?
```
$ lshw -C network
```

---

### Post by ubuntuforums on 2008-09-12
```

  *-network:0 UNCLAIMED   
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
  *-network:1
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wlan0
       version: 01
       serial: 00:1a:70:31:3a:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,06/25/2006, 4.80.2 ip=192.168.1.102 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
Alright, well it looks like both are recognized. I see my Wireless-G card (network:0) says "unclaimed", how can I "claim" it?.. or obviously you know where you're going with this, so I'll just listen. lol, ty

---

### Post by ubuntuforums on 2008-09-13
Sorry to bump my thread, if it's not allowed delete this post (@moderators). If anyone can help me out, I'd really like to get this going soon. Thanks so much.

---

### Post by Zorael on 2008-09-14
This is actually curious.

Do you know what the module name is of your other card? Perhaps the same command will say if you boot it up without the other card connected.
```
*-network:1
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wlan0
       version: 01
       serial: 00:1a:70:31:3a:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+bcmwl5** driverversion=1.52+Broadcom,06/25/2006, 4.80.2 ip=192.168.1.102 latency=32 link=yes **module=ndiswrapper** multicast=yes wireless=IEEE 802.11g
```
Like so but for the first card.

---

