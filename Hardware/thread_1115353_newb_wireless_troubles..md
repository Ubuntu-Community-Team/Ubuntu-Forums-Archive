---
title: "newb wireless troubles."
date: 2009-04-03
forum: Hardware
---

### Post by wicked circuits on 2009-04-03
So I just reinstalled ubuntu on my toshiba laptop again, and for some reason, my wireless is not working.. It was working fine on the first install. but now there is no wireless networks found. 
when i go to system>admin>hardware drivers, it shows two drivers for the wireless:
   Support for atheros 802.11 wireless lan cards
   Support for 5XXX series of atheros 802.11 wireless lan cards.

pkelly@pkellylinux:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:83:7c:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:38:27:90
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=199.120.25.142 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:8d:ed:30:2c:6c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

>>I hope this helps!

---

### Post by j-wilcox on 2009-04-03
Run the hardware driver app. and see if it pulls up a driver to activate.

System
Admin.
Hardware driver

Other than that hopefully someone else will chime in.

---

### Post by wicked circuits on 2009-04-03
okay, so I turned "Support for atheros 802.11 wireless lan cards" off and left "Support for 5XXX series of atheros 802.11 wireless lan cards." on, rebooted  and now it will recognize that there is wireless, but no matter how strong the signal is, it will not connect... I have never encountered this before... any ideas?

---

### Post by Ceyx on 2009-04-05
I had this problem too.

Check this page out - about half way down..."Atheros ath5k wireless driver not enabled by default"

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

I loaded the generic backport mentioned and it worked just fine.

Ciao

---

