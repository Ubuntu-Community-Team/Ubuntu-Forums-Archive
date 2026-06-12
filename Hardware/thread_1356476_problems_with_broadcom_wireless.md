---
title: "problems with broadcom wireless"
date: 2009-12-16
forum: Hardware
---

### Post by agingric on 2009-12-16
hello,

just got karmic installed on my "new" laptop.  

seems like the broadcom wireless card is not being recognized.

i found the following instructions on another (closed) thread.

1) Open Synaptic Pacakage Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh
6) Search for "bcmwl-kernel-source"
7) Mark for installation
8) Install it
9) Reboot computer


i followed those instructions (except i downloaded, not installing from cd) and after reboot i had no network connections at all (even wired).  so i uninstalled the package and rebooted.  this fixed the wired connection.  

still no wireless.  can anyone point me in the right direction?  i am really looking forward to using ubuntu again after an absence of several months due to a broken computer.  

thanks,
andy

---

### Post by mikewhatever on 2009-12-16
The package you installed is not intended for just any Broadcom card out there. Please post the output of <sudo lshw -C network> to verify what you have.

---

### Post by agingric on 2009-12-16
thank you kindly for your assistance.  please note that this is a dual boot machine and wireless is working just fine in windows, so the card is turned on.  

andy

output of  sudo lshw -C network is as follows

 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:b8:92:b5:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.5 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:e0204000-e0205fff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0208000-e0209fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:3d:49:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by agingric on 2009-12-16
solved!  

clicked on--
system
administration
hardware drivers

and it gave an option to download and install the driver.

fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.

i recall trying that series of clicks last night with no results (no drivers listed).  why it did not work before i don't know, but it works now and i'm happily using ubuntu
andy

---

