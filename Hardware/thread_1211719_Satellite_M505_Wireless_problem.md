---
title: "Satellite M505 Wireless problem"
date: 2009-07-12
forum: Hardware
---

### Post by Duke Let on 2009-07-12
I run xubuntu on a Toshiba satellite M505-S4940 and I've attempted to install compat-wireless. However I'm not entirely certain it's even recognizing my wireless

leto@dict-tab:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:5d:ee:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:b3:fd:a8:ed:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Has anyone made wireless run in a Toshiba Satellite M500-series computer?

If so please post details, also, anyone who might now how to help solve this problem, please post your .02$.

---

### Post by Duke Let on 2009-07-13
bump

---

### Post by artmendez on 2009-10-01
I've the same problem with an M505 under Ubuntu 9.04
Any success?

Regards.

---

### Post by wafflemelon on 2009-12-07
How did you manage to get past the heating problem? My unit's fan doesn't work on Ubuntu, making it overheat.

---

### Post by derekmbarnes on 2009-12-31
Use this code:

```
lspci -v | less
```

Scroll through the list until you find your network controller; if your card is an 8172, I've got your solution right here:
[URL="http://ubuntuforums.org/showthread.php?t=1367871"]
http://ubuntuforums.org/showthread.php?t=1367871[/URL]

---

