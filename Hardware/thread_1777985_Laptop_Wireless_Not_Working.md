---
title: "Laptop Wireless Not Working"
date: 2011-06-08
forum: Hardware
---

### Post by Rozatroz on 2011-06-08
Hi guys, I have a acer aspire 3610 and am currently running Ubuntu 11.04 dual booted with vista. For some reason ubuntu is not finding my wireless card which works fine on the windows boot :S i am using a wired LAN connection for now but it wont be much use in Wifi hotspots for work...

Any help will be greatly appreciated. Many Thanks

---

### Post by matt_symes on 2011-06-08
Hi

Open a terminal and type (case sensitive)

```
sudo lshw -C network
```

Enter your password. It will not be echoed to the screen.

Copy and paste the results back here between code tags like this.

[noparse]```
 text 
```[/noparse]

Kind regards

---

### Post by Rozatroz on 2011-06-09
matt_symes

Thanks for the repyl. Here is the info...

```
PCI (sysfs)  
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:21 memory:b0100000-b0101fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e3:7e:d3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:3000(size=256) memory:b0102000-b01020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:2c:5d:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

Regards

---

### Post by TBABill on 2011-06-09
From your lshw output it looks like the machine has enabled the b43 driver, but the firmware may be missing. Can you go to Additional Drivers and see if the system offers you the opportunity to "activate" the driver? It'll download firmware (while connected via wired connection) and install or reinstall the driver if needed.

---

### Post by Rozatroz on 2011-06-09
solved it using firmware download.

thanks

---

