---
title: "Problem with internet drivers after installing Ubuntu 9.04 on Dell Precision M65"
date: 2009-08-10
forum: Hardware
---

### Post by Zatarra on 2009-08-10
Hello, hello.
 
I installed Ubuntu 9.04 on my Dell Precision M65 and looking forward to start using the computer. There is still a huge problem, Ubuntu does'nt seem to recognize the internet drivers. I've googled around and do'nt find any help that is with in my confort zone. I picked up the command 'sudo lshw -C network' to get info on the drivers and pasted the result below.
 
I will be really thankfull for any help or guidans on this matter.
 
With thanks in advance........
----------------------------------------------------------------------------
 
*-network:0
description: Ethernet interface
product: NetXteme BCM5705M Gigabit Ethernet
vendor: Broadcom Corporation
physical id: 0
bus info: pci@000:02:00.0
logical name: eth0
version: 01
serial: 00:0f:1f:2a:e7:d1
capacity: 1Gb/s
width: 64 bits
clock: 66MHz
capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10
bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=
3.94 firmware=5705-v3.11 latency=32 link=no mingnt=64 module=tg3 multicast=yes p
ort=twisted pair
*-network:1
description: Network controller
product: BCM4309 802.11a/b/g
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:02:03.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32 module=ssb
*-network:0 DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:90:4b:bf:7e:f5
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: 26:b9:fb:ef:35:f3
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
link=yes multicast=yes

---

