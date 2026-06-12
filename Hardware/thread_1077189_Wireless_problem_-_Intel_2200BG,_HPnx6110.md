---
title: "Wireless problem - Intel 2200BG, HPnx6110"
date: 2009-02-22
forum: Hardware
---

### Post by Dumpling on 2009-02-22
Hello,

I am new user of ubuntu. I have a problem with my wireless. I tired to solve it with this what I have found in other posts, but it still not work.

My laptop : HP nx6110
Ubuntu : 8.04
jarek@jarek-laptop:~$ uname -a
Linux jarek-laptop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux


Please see some data below:

jarek@jarek-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 05
       serial: 00:0e:35:e6:15:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=64 maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:12:79:be:27:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.2 latency=64 module=ssb multicast=yes


jarek@jarek-laptop:~$ sudo iwlist scanning
[sudo] password for jarek: 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results

Please help me. Sorry for my English.

Thanks in advance.

I put the same post in Networking and Wireless. Can somebody delete this post from this category? Thanks.

---

