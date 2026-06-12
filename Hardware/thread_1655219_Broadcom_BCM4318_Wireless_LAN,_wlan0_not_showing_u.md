---
title: "Broadcom BCM4318 Wireless LAN, wlan0 not showing up"
date: 2010-12-29
forum: Hardware
---

### Post by orphefs on 2010-12-29
Hi everyone,

I am sure you have seen this before, but I've been trying to get it working since two days now, and still no results :(

Some more info to give you a better idea:

Fujitsu Siemens Amilo A1667G laptop

Ubuntu 10.10 Maverick Meerkat 64 bit

uname -r
```
2.6.35-22-generic
```

lshw -C network
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:42:9d:1e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.65 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:17 ioport:e800(size=256) memory:febff400-febff4ff memory:febc0000-febdffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:febfc000-febfdfff

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

I have tried installing the STA drivers via the Ubuntu Software center, no luck.

I have tried using ndiswrapper following the instructions [here]("http://ubuntuforums.org/showthread.php?t=25683"), no luck. Even when the ndiswrapper module seemed to be found when entering 'sudo modprobe ndiswrapper', I still couldn't see wlan0...

I am really frustrated, I am a relative beginner in Ubuntu, don't know what to do! I think I also accidentally removed the wlan0 drivers completely at some point, that's when wlan0 stopped showing up in iwconfig!

Sorry to annoy you with another boring question and I thank you in advance for your help!

Orpheus :)

P.s.: By the way, I have looked at countless posts on Ubuntu Forums and other websites, and none of them did the trick...I may have done something really stupid :S

---

### Post by orphefs on 2010-12-29
anyone?  :confused:

---

