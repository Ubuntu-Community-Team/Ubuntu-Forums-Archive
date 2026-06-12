---
title: "Qutie odd wireless issues in Hardy"
date: 2008-11-03
forum: Hardware
---

### Post by Sonolin on 2008-11-03
First thing's first: wireless DOES work on my machine, but it is very glitchy.  First of all, the I cannot (CANNOT) use the command line to set up my network for the life of me.  Nor can I manually configure the network in the GUI (roaming mode MUST be on).  The problem is.. roaming mode sucks.  It keeps disconnecting me every few hours, then I come home and it is asking for a hex password for the network.  I cannot have this happen as clients usually need updates for their code (which sometimes is on my local machine).  

I had manual command line configuration working before I applied updates to hardy (and this is the only single thing I did that may provoke this.. I am pretty sure because this is the second installation of hardy on this machine in the past few days and it did not work before either, and just after reformatting barely worked before updates).  Here is the output of the command "lshw -C network":

```

  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:ec:74:74:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:0d:20:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=99.139.255.200 multicast=yes wireless=IEEE 802.11g

```

I have the drivers installed fine to my knowledge.  I am not sure if the two wireless entries may have to do something with it (am not a linux guru), being that one is "*-network:1", and the other just "*-network".

In any case, here is the code in my rc.local file that SHOULD connect the network.. and this is the code I execute when attempting to connect from the command line:

```

ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid MY_ESSID
iwconfig wlan0 key MY_KEY
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

```

I have tried this a variety of ways.. with ifconfig wlan0 up at the top (after releasing dhclient), then tried leaving out key open/mode Managed... NOTHING I seem to do helps.

Any help would be greatly appreciated, this is more than an annoyance,

Michael

EDIT: BTW just so you know before this I had Gutsy installed for maybe half a year running fine, same hardware, drivers, everything, with roaming.. for some reason Hardy must not like my card or something

---

