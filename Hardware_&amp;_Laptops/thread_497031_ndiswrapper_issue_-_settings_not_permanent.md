---
title: "ndiswrapper issue - settings not permanent"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by shardservant on 2007-07-09
Hi everyone,

I was able to get a Netgear WPN511 card to work on my Dell Inspiron 1000 laptop but the settings do not appear to be permanent.

A reboot of the machine bounces things back to the default driver.

I tried doing a sudo ndiswrapper -m to make things permanent but it fails to do so.

Does anyone have any ideas on how to correct this?

Any help you can provide would be greatly appreciated.

Thanks,
Andy

---

### Post by fredj on 2007-07-09
You also need to do 'sudo modprobe ndiswrapper' to add ndiswrapper as a loadable module

---

### Post by shardservant on 2007-07-10
Good afternoon,

I did:
 
sudo depmod -a
sudo ifdown ath_pci
sudo rmmod ath_pci
sudo modprobe ndiswrapper
sudo ndiswrapper -da

The last command should have written the aliases to the required files but I continue to have a problem with the card after a reboot.

Any ideas?

---

### Post by fredj on 2007-07-10
Open a terminal type 'sudo lshw -class network' and post the result here.
Also type 'ndiswrapper -v' and post the result here.

---

### Post by shardservant on 2007-07-11
After a reboot, I have to do the following manually to get the WPN511 card to run at full speed.

sudo rmmod ath_pci
sudo depmod -a
sudo rmmod ndiswrapper 
sudo modprobe ndiswrapper 


sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:bf:01:eb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: ioport:1800-18ff iomemory:e4003000-e4003fff irq:22
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       logical name: ath0
       version: 01
       serial: 00:18:4d:85:2a:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=NETGEAR, Inc.,03/23/2006,4.2.2. ip=192.168.1.3 latency=128 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:34000000-3400ffff irq:16

ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by fredj on 2007-07-11
Well the first thing that I can see from this is that you have the problematic version of ndiswrapper but that
may not necessarily be the cause of the problem. The standard commands for installing a windows XP
driver are 
1. Use the latest windows XP version of the driver files and make sure you are in the directory where the
driver files are located.
Type 'sudo -i' (to make yourself a root user)
Type 'l's' ls to make sure that you are still in the right directory.
Type 'ndsiwrapper -i (driverfilename).inf'
Type 'ndiswrapper -l' to make sure that the previous command worked
Type 'ndsiwrapper -m' to make the driver a permanent part of ndsiwrapper.
Type 'modprobe ndiswrapper' to add ndiswrapper to the modules loaded at bootup.
The problem is that if you have the defective version of ndiswrapper (and it seems that you do) then 
all these commands may appear to work but they sometimes they don't.
The only answer to this is to downlaod the latest ndiswrapper source, install the build-essential
package and recompile and install diswrapper.

---

### Post by zipperback on 2007-07-14
Also you should make sure you are using the current ndiswrapper.

Here is the direct link to the current version.

http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz

- Jack
- zipperback :popcorn:

---

