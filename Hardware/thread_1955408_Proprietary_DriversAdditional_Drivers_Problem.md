---
title: "Proprietary Drivers/Additional Drivers Problem"
date: 2012-04-09
forum: Hardware
---

### Post by DreamWeaverM on 2012-04-09
I am having problem getting my proprietary drivers working properly. Currently, I am using Ubuntu 11.10 64-bit on an Acer Aspire 5100. I'm new to Ubuntu (pretty much all linux distros :) ) and would your answers to be in layman terms (if possible!). Anyways, I installed Ubuntu 11.10 just over springbreak and noticed my wireless internet didn't work. I figured it was no biggy and so I ignored it and went back to using Linux Mint 12 for a while. I told a relative of mine and he said to enable your proprietary drivers. So, I went into system setting>Additional Drivers and there is pretty much nothing there. 'Enable' is grayed out and unable to click on. I noticed an orange box near the top but it is empty also. Right now I am connected directly to my router and have no problem there. Again my laptop specs are this: OS= Ubuntu 11.10 64-bit
                                                                                                 Processor= AMD Dual core 64-bit Turion TL-50
                                                                                                 R.A.M= 4gbs.
If you need more info please post in the comments!
 


             -Michael

---

### Post by lukeiamyourfather on 2012-04-09
What wireless device does it have? If you're not sure run this command to get the network devices.

```
lshw -class network
```

You might have to use sudo in front of the command to run it as root, can't remember though.

---

### Post by DreamWeaverM on 2012-04-10
@lukeiamyourfather, here is all the code i got from running that command (i ran it as sudo/root anyways just to be sure) > *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:15:0a:2b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:f0300000-f03000ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:29:9d:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.2.3 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:f0310000-f031ffff

---

