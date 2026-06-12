---
title: "Lenovo Z570 wireless networking and 12.04 - previous solution not working"
date: 2012-05-01
forum: Hardware
---

### Post by justinbic40 on 2012-05-01
Hey everyone.

I have a Lenovo Z570 with the Intel Centrino wireless networking adaptor. I just upgraded to 12.04 with a full wipe and it seems to have broken my wireless. I was running 11.10 previously and I had to blacklist acer_wmi and bmca to allow the wireless to be enabled. This is no longer working.

```
justin@justin-Ideapad-Z570:~$ rfkill list all
0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
``````
justin@justin-Ideapad-Z570:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:13:3b:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:79:ab:d8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.114 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff


```

---

### Post by sam4 on 2012-05-02
Oh no i am facing the same problem :( , let me know as well.

---

