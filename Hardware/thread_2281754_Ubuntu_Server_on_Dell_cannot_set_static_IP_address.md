---
title: "Ubuntu Server on Dell cannot set static IP address"
date: 2015-06-09
forum: Hardware
---

### Post by david398 on 2015-06-09
We have a Dell Power Edge T320 and have installed Ubuntu Server 14.04.2 along with MySQL 5.6.  I cannot set a static IP address on the server.  So far I have modified the file /etc/network/interfaces to the following but still cannot get it to work.  Any help would be much appreciated.

auto eth1
iface eth1 inet static
   address xxx.xxx.xxx.x
   netmask xxx.xxx.xxx.x
   gateway xxx.xxx.x.x
   dns-nameservers xxx.xxx.xxx.x xxx.xxx.xx.xx

---

### Post by TheFu on 2015-06-09
Is eth1 the correct device?
**dmesg|grep eth** to see if that is the situation.  **sudo lshw -C network** will let us see all the network devices AND the drivers used too.

Also - is the loopback really missing? If so, put it back.
```
auto lo
iface lo inet loopback
```

---

### Post by david398 on 2015-06-09
-Sorry, it's setup for eth0.
-When typing dmesglgrep eth it returns 'command not found'
- sudo lshw -C network returns the following:

PCI (sysfs)
*-network:0 DISABLED
description: Ethernet interface
product: NetXtreme BCM5720 Gigabit Ethernet PCIe
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00:0
logical name: emp
version: 00
serial: 20:47:47:7a:57:e6
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-df 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 fireware=FFV7.10.59 bc 5720-v1.36 latency=0 link=no multicast=yes port=twisted pait
resources: irq:16 memory:d90a000-d90affff memory:d90b0000-d90bfff memory:d90c0000-d90cffff memory:dd000000-dd03ffff

There is a similar printout for network:1

---

### Post by TheFu on 2015-06-09
a) that isn't an l (EL), it is a | (pipe).
b) the device is "emp" - see the logical name?  That is the device to be used.

The emp device is disabled and has a driver I've never seen before. Hopefully, everything just works. Good luck!

---

### Post by david398 on 2015-06-09
Changing the device name from eth0 to emp worked.  Thank you very much for your help.

---

### Post by TheFu on 2015-06-09
Please mark the thread as "**solved**" using the *thread tools*.

---

