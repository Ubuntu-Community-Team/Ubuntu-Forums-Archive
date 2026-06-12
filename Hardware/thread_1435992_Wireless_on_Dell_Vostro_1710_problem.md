---
title: "Wireless on Dell Vostro 1710 problem"
date: 2010-03-22
forum: Hardware
---

### Post by lostone on 2010-03-22
Hello all,
I could really use any help you guyz can give me regarding the following problem.

I have recently installed 9.10 un my laptop (dell vostro 1710) and everything worked just fine until an update 3 days ago, when my wireless drivers (detected, installed ok and working) went crazy.

Long story short - no errors, no messages, just that my ubuntu now detect wireless networks in the area totally random. I mean sometimes in doesn't detect any networks, but after a reboot it detects them all right.

I don't know if it's from the update i'm talking about or else. But i haven't change any config files or something...

**lshw -C network** returns the following:

[HTML]lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth2
       version: 03
       serial: 00:1f:e1:83:bf:81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f4000000-f4003fff memory:fc000000-fc0fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:59:06:06
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.159 latency=0 multicast=yes
       resources: irq:29 ioport:6000(size=256) memory:f8410000-f8410fff(prefetchable) memory:f8400000-f840ffff(prefetchable) memory:f8420000-f842ffff(prefetchable)[/HTML]

Any help/ideeas would be greately apreciated.

Thanx.


//update

new informations available :)

if i do an
[html]sudo iwlist scan[/html]
i can see the list of available wireless networks in my area.
so it seems that the networkManager applet is the problem...

let's see how i can get rid of that :)

---

### Post by lostone on 2010-03-22
solution: wicd

works like a charm, turns out the problem was not in the divers or anything else, but in the networkManager applet. 
Uninstalled id, installed wicd and works perfectly.

good to know...

---

