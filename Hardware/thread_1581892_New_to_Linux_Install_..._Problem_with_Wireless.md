---
title: "New to Linux Install ... Problem with Wireless"
date: 2010-09-25
forum: Hardware
---

### Post by worven on 2010-09-25
I am new to Linux, I just started playing with it yesterday.

I installed the 10.04 Server version on DELL VOSTRO 1520.  Everything works fine, I was able to install Acrobat reader (Which was quiet the challenge, before I found the right package for the Intel 64 Bit Architecture).  I installed all other applications I plan to use as well.  

My Only outstanding task is to Make the wireless card work.  I have googled and tried various recommendations, one suggested checking the BIOS version and the BIOS version was higher than the recommend A03.

I can't see the interface for wireless, I see the device and the driver loaded, now why want the Radio turn on?

I am posting some output, for anyone willing to help me in this regard:

TIA

Worven

Executing Uname...
 
Linux myubuntu 2.6.32-24-server #43-Ubuntu SMP Thu Sep 16 16:05:42 UTC 2010 x86_64 GNU/Linux
 
 
Executing ifconfig...
 
eth0      Link encap:Ethernet  HWaddr 00:26:b9:9c:2d:d6  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe9c:2dd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29808558 (29.8 MB)  TX bytes:2029931 (2.0 MB)
          Interrupt:31 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27480 (27.4 KB)  TX bytes:27480 (27.4 KB)

 
 
Executing lshw...for Network
 
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:9c:2d:d6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff
 
 
Executing lsmod for broadcom driver b43
 
b43                   182290  0 
mac80211              238416  1 b43
cfg80211              148546  2 b43,mac80211
led_class               3764  2 b43,sdhci
ssb                    45092  1 b43
 
 
Executing cat /etc/network/interface
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by davidmohammed on 2010-09-25
Your trace mentions a b43 wireless  - usually, you just need to activate the driver suggested in - System - Administration - Hardware drivers n.b. connect to the internet first via your ethernet connection.

---

### Post by worven on 2010-09-25
> **davidmohammed said:**
> Your trace mentions a b43 wireless  - usually, you just need to activate the driver suggested in - System - Administration - Hardware drivers n.b. connect to the internet first via your ethernet connection.

Sorry I installed the server edition, i also installed gdm for desktop, how do i get the system - administration - hardware drivers   menu item?

As I install new packages my desktop gets updated, so what package do I need for the hardware drivers gui?

Thanks

Worven

---

### Post by davidmohammed on 2010-09-26
from the command line you would run

jockey-gtk

if you dont have it installed try

sudo apt-get install jockey-gtk

then run jockey-gtk.

---

