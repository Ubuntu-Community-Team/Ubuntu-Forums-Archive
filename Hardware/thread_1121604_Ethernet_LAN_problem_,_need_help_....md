---
title: "Ethernet LAN problem , need help ..."
date: 2009-04-10
forum: Hardware
---

### Post by Dragon6 on 2009-04-10
Hi 
I have ubuntu 8.10 installed on my laptop dell vostro 1510 which has Realtek RTL-8100C Ethernet LAN , I already used those commands to see the problem but still didn't know what the real problem is :
by the way , I'm using DHCP 


user-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

user-laptop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:1f:e1:1b:37:c4
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:133638 errors:0 dropped:0 overruns:0 frame:1012017
TX packets:136121 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:172606068 (172.6 MB) TX bytes:14263962 (14.2 MB)
Interrupt:19

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:640 errors:0 dropped:0 overruns:0 frame:0
TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:29485 (29.4 KB) TX bytes:29485 (29.4 KB)

pan0 Link encap:Ethernet HWaddr d6:d8:1d:ee:55:f7
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Thank you ...

---

### Post by pbpersson on 2009-04-10
It appears that eth0 has no IP address.

If that is the port you are attempting to use, post the output of the following command:

 sudo dhclient eth0

---

### Post by Dragon6 on 2009-04-10
Thanks for responding ...
the output is as appears below : 

harith@harith-laptop:~$ sudo dhcclient eth0
[sudo] password for harith: 
sudo: dhcclient: command not found
user-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:e1:1b:37:c4
Sending on   LPF/eth0/00:1f:e1:1b:37:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Dragon6 on 2009-04-11
I noticed that no one replied after my last thread :D
can anyone help me please with this ethernet lan ?
I already showed the outputs

---

### Post by pbpersson on 2009-04-11
No DHCP server answered.  Is the DHCP server up and running?  Will it send IP addresses to other machines on the network when they ask for a new address?

---

### Post by Dragon6 on 2009-04-11
Yes of course the other machines ask for Ip addresses and when I connect to the internet wirelessly , it goes well but when i need to connect to the internet wirely using this Ethernet lan , these situations above happen 
Thanks for responding ...

---

### Post by szarywilq on 2009-04-21
I have exacly same problem. Everything works for few months, ans suddenly yesterday problem mentioned above. I've tried everything...

On DHCP: NO DHCP OFFERS RECIEVED
on static - just do not work.

But there is something I have found out. I can't even ping router... On this pc I also have xp and on 2 other pc's also xp, and I tried ubuntu from live CD - all of these works fine.

---

