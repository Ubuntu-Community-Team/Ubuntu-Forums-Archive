---
title: "Dell Inspiron N7110 WIFI power"
date: 2015-06-22
forum: Hardware
---

### Post by kelvinator on 2015-06-22
My Dell Inspiron has worked really well with Ubuntu with one exception: The WIFI keeps on turning off!

What can I do to keep WIFI on at all times, even when running on battery power?

Currently I am using Ubuntu 15.04, but I have experienced this problem with prior versions as well.

---

### Post by weatherman2 on 2015-06-22
What wireless card do you have?  Open a terminal (Ctrl Alt t) and type this command:

```
sudo lshw -C network
```

---

### Post by kelvinator on 2015-06-22
*-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: 4c:eb:42:08:6e:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-18-generic firmware=18.168.6.1 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:33 memory:d0600000-d0601fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 84:8f:69:c6:84:15
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:29 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
kelvin@Knowledge:~/scripts$

---

### Post by weatherman2 on 2015-06-22
There are a couple of parameters you can try setting for the iwlwifi driver used for your Intel wireless card.  These may help:

[http://ubuntuforums.org/showthread.php?t=2220377](http://ubuntuforums.org/showthread.php?t=2220377)
[http://ubuntuforums.org/showthread.php?t=2208210&p=12943350#post12943350](http://ubuntuforums.org/showthread.php?t=2208210&p=12943350#post12943350)

---

### Post by kelvinator on 2015-06-26
Thank you very much. After the fix from the second link I have been online without problems for 2 hours tonight.

---

