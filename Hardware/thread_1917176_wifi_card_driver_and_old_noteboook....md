---
title: "wifi card driver and old noteboook...??"
date: 2012-01-29
forum: Hardware
---

### Post by xv12 on 2012-01-29
Hi, I need help - I have an older notebook (6 years?) [B][SIZE=2]IBM Lenovo ThinkPad T43 (GAI1030) 
[/SIZE][/B]and I installed latest Ubuntu 11.10, which cannot recognize my wifi card (intel ??) , when I open "Network settings" it says "firmware missing".... So how can I install correct driver or firmware for wifi card? Can I download it somwhere on USB and install it? 
Or is it easier install older version of Ubuntu, for example 8.10 or so.. ?
 What do you think? What would be the easiest way or solution of my problem..?

Thx a lot, Tomas

---

### Post by wolfen69 on 2012-01-29
Post the output of
```
sudo lshw -C network
```

---

### Post by xv12 on 2012-01-30
Thx, m8, so:

omas@tomas-ThinkPad-T43:~$ sudo lshw -C network

[sudo] password for tomas: 

  *-network               

       description: Ethernet interface

       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 11

       serial: 00:16:41:a7:7e:83

       capacity: 1Gbit/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5751m-v3.46a latency=0 link=no multicast=yes port=twisted pair

       resources: irq:16 memory:90100000-9010ffff

  *-network

       description: Network controller

       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 2

       bus info: pci@0000:04:02.0

       version: 02

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master

       configuration: driver=b43-pci-bridge latency=64

       resources: irq:21 memory:90300000-90301fff

  *-network DISABLED

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:19:7e:02:6f:32

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

tomas@tomas-ThinkPad-T43:~$

---

### Post by wolfen69 on 2012-01-30
You have a Broadcom wireless card. Check *Additional Drivers* for the driver. You will need to be plugged into the net to get these.

---

### Post by xv12 on 2012-01-31
i'm not sure if i got your response correctly...do i have to find someone else who uses linux and do it through his computer, i can't plugg into the net which is the problem. By the way i'm the beginner as you can see so sorry for silly questions.]]

---

