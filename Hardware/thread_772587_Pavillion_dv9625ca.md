---
title: "Pavillion dv9625ca"
date: 2008-04-28
forum: Hardware
---

### Post by drew06 on 2008-04-28
I have a pavillion 9625ca and have had trouble getting the wireless card to work.  I am wondering if anyone else has one of these and if so did you get it working.

---

### Post by tayroni on 2008-04-28
Post the result of lspci, please.

Go to console and type

lspci

If the line

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

appears, you can consider using ndiswrapper. It's a good way to make your wireless work on linux

To do that:

1 ) sudo apt-get install ndiswrapper-utils-1.9 ndisgtk zip unzip

2 ) Add the lines

blacklist b43
blacklist b43legacy
blacklist b44

to the very end of /etc/modprobe.d/blacklist

3 ) Reboot

4 ) Download windows driver of your board. If your Ubuntu is *i386*, you can download here

<a href="http://ftp.us.dell.com/network/R151517.EXE">R151517.EXE</a>

5 ) Unzip it

unzip -a R151517.EXE

and type these commands ON DIRECTORY THAT CONTAINS bcmwl5.inf

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

You should see "Driver installed, Hardware present"

6 ) Load driver during boot

Type now

sudo ndiswrapper -ma

and add the lines

ndiswrapper
ssb

to the end of /etc/modules.

7 ) Create new file /etc/init.d/ndiswrapper

sudo gedit /etc/init.d/ndiswrapper

with these lines

#/bin/bash

rmmod ohci-hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci-hcd

save, exit and type on console

sudo chmod a+x /etc/init.d/ndiswrapper
sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper

8 ) Reboot

---

### Post by Yellow Pasque on 2008-04-28
> **tayroni said:**
> Post the result of lspci, please.

Go to console and type

lspci
Better yet, use sudo lshw -C network

---

### Post by drew06 on 2008-05-08
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:cf:d5:17
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt
10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

---

