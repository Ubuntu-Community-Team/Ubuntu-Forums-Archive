---
title: "No Internet, wired or wireless on kubuntu"
date: 2008-10-18
forum: General Help
---

### Post by Dayo6 on 2008-10-18
Hi

I installed kubuntu 8.0.4.1 on my compaq presario c762nr, and now there's no internet.  Help please?

Thanx!

---

### Post by Ayuthia on 2008-10-18
Can you go into the Konsole and type the following:
```
lspci -nn
```
You will need to look for Network Controllers and Ethernet Controllers.  One of them will be your wireless card.  If you are able to get that information, please try to post that information.

---

### Post by Dayo6 on 2008-10-18
> **Ayuthia said:**
> Can you go into the Konsole and type the following:
```
lspci -nn
```
You will need to look for Network Controllers and Ethernet Controllers.  One of them will be your wireless card.  If you are able to get that information, please try to post that information.

OK, I did it.  This is what I got:

> owner@compaq:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


---

### Post by Yellow Pasque on 2008-10-18
Ok. Let's make sure kernel modules are loaded for your cards and check your interfaces. Please post output of:
```
sudo lshw -C network
cat /etc/network/interfaces
ifconfig
```

---

### Post by Dayo6 on 2008-10-19
> **Temüjin said:**
> Ok. Let's make sure kernel modules are loaded for your cards and check your interfaces. Please post output of:
```
sudo lshw -C network
cat /etc/network/interfaces
ifconfig
```

Yep, this is what I get:

> 
owner@compaq:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:25:1a:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
owner@compaq:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

owner@compaq:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:25:1a:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74500 (72.7 KB)  TX bytes:74500 (72.7 KB)


---

### Post by Dayo6 on 2008-10-19
OK since I'm crazy, I uninstalled kubuntu and now have ubuntu.  I like the ubuntu theme better. :)

---

### Post by Yellow Pasque on 2008-10-19
Well, your wireless card doesn't have a driver, but it looks like you should be able to get a connection through your LAN cable. Ubuntu didn't define an interface for your LAN, so:
```
gksudo gedit /etc/network/interfaces
```
Add this block:
```
auto eth0
iface eth0 inet dhcp
```
Save the file and quit. From now on, eth0 will be defined at boot, but for this session, use this command to bring the interface up:
```
sudo ifup -i /etc/network/interfaces eth0
```

---

### Post by Dayo6 on 2008-10-19
> **Temüjin said:**
> Well, your wireless card doesn't have a driver, but it looks like you should be able to get a connection through your LAN cable. Ubuntu didn't define an interface for your LAN, so:
```
gksudo gedit /etc/network/interfaces
```
Add this block:
```
auto eth0
iface eth0 inet dhcp
```
Save the file and quit. From now on, eth0 will be defined at boot, but for this session, use this command to bring the interface up:
```
sudo ifup -i /etc/network/interfaces eth0
```

OK I did what you told me to do... and now I get this:

> owner@compaq:~$ gksudo gedit /etc/network/interfaces
owner@compaq:~$ sudo ifup -i /etc/network/interfaces eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:ec:25:1a:22
Sending on   LPF/eth0/00:1e:ec:25:1a:22
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory


---

### Post by Yellow Pasque on 2008-10-19
Does your internet provider give you a static IP by chance? Are you connecting through a router?

---

### Post by anjilslaire on 2008-10-19
> **Dayo6 said:**
> OK since I'm crazy, I uninstalled kubuntu and now have ubuntu.  I like the ubuntu theme better. :)

```

sudo apt-get install ubuntu-desktop

```
would have done it. No reinstall needed.

---

### Post by Dayo6 on 2008-10-19
> **Temüjin said:**
> Does your internet provider give you a static IP by chance? Are you connecting through a router?

Yep, and yeah.  I'm going to go try your steps when my computer is plugged in now... My brother says that's what I was supposed to do.

> **anjilslaire said:**
> ```

sudo apt-get install ubuntu-desktop

```
would have done it. No reinstall needed.

O OK next I'll try that. :)

---

### Post by Yellow Pasque on 2008-10-19
This page should have everything you need:
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by Dayo6 on 2008-10-20
OK guys I got my internet to work now... but now when I have a WEPE encryption it doesn't work.

(I think I'm using madwifi ar50007)

---

### Post by Dayo6 on 2008-10-20
Thank you for your support!

But I figured it out with my brother.  Thanks again!

I wish all of you a happy Halloween!

---

