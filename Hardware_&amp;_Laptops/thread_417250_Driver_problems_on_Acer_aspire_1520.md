---
title: "Driver problems on Acer aspire 1520"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by WsfWarlord on 2007-04-21
okay i just managed to install ubuntu 7.04 on my laptop and it didn't recognize my wifi card
i also tried turning on desktop effects and i got a nice white screen now :/
can someone help?

edit: checking the network:

warlord@wsf-laptop:~$ sudo lshw -C network
Password:
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: a
       bus info: pci@00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:1c00-1c1f iomemory:c0006000-c000601f iomemory:c0005000-c00057ff irq:10
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:a4:a8:56
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.50 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:1000-10ff iomemory:c0006400-c00064ff irq:22
warlord@wsf-laptop:~$ 

looks like my wifi card is "unclaimed" how can i "claim" it? ^^

---

