---
title: "Compaq V5000 wifi card will not show"
date: 2013-05-28
forum: Hardware
---

### Post by Bryant777 on 2013-05-28
I installed Ubuntu 12.04 on a Compaq Presario V5000 but can't get the wifi card to work.  I do not have enough experience to figure this out.

I tried installing b43-fwcutter_015-9_i386 and firmware-b43-installer_015-9_all but that did not work.

I have no idea what to try now.

thanks for any help.

---

### Post by ahallubuntu on 2013-05-28
~

---

### Post by Bryant777 on 2013-05-28
*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fe:49:cc
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:7e:98:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
stu@stu-Presario-V5000-ET820UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Bryant777 on 2013-05-28
I hit the wifi button an repeated and got this:

*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fe:49:cc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.110 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:7e:98:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
stu@stu-Presario-V5000-ET820UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by ahallubuntu on 2013-05-28
~

---

### Post by Bryant777 on 2013-05-29
Thanks, now the wifi light is blue.  But when I try to enter the wireless network password, it only accepts 7 characters.  I need to enter 8.

How do I fix that?   I only installed the first b43 package from Software Center.  Is there another I need.  I see three more b43 packages.

---

### Post by Bryant777 on 2013-05-29
I now have it working.  I installed the legacy b43 drivers.

Thanks for you kind help!!

---

