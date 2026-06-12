---
title: "Unclaimed interface"
date: 2012-01-10
forum: Hardware
---

### Post by Tormentor2 on 2012-01-10
Hello everyone,
 
I'm having a problem with my HP DL365G1 server, I installed Ubuntu Desktop 64bit on it, it works fine but I'm facing a problem!
The server comes with dual NICs, one of them is "UNCLAIMED" check "**lshw -c network**" output
>  *-network               
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0a:00.0"]pci@0000:0a:00.0[/EMAIL]
       logical name: eth0
       version: 12
       serial: 00:1b:78:77:c6:cc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.1.6 duplex=full firmware=bc 1.9.6 ip= latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:52 memory:f8000000-f9ffffff memory:fc000000-fc0007ff
  *-network UNCLAIMED
       description: Ethernet controller
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 12
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi cap_list
       configuration: latency=64 mingnt=64
       resources: memory:fa000000-fbffffff memory:fc100000-fc1007ff
 
As far as I could dig into google I need to install the driver for that NIC, but ubuntu could actually identify the driver for the first interface which means it already has the drivers needed!
 
any help is appreciated

---

### Post by Tormentor2 on 2012-01-12
C'mon people! no one got any idea?!? this is Ubuntus official forum and no one of the big linux minds can help me??!:(

---

