---
title: "Can't connect to internet after updating to 8.04"
date: 2008-05-14
forum: Hardware
---

### Post by gejzik on 2008-05-14
Hello,

I upgraded to 8.04 and after reboot internet connection was gone. I can't connect even to my router.
My computer is ASUS A6M-Q046 notebook with BCM4318 wireless and Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller.
When I try to configure eth0 interface using Network Tools, I get a message that this interface doesn't exist.

Also in Restricted drivers manager was wifi card with not used status. After I tried to enable it, downloading began. With internet connection not working it failed. After restarting the system, this driver disappeared from RDM.

Here are some more information from terminal:

gejzik@saksik:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:18:f3:39:65:92
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:402 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:335 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:104094 (101.6 KB) TX bytes:0 (0.0 B)
Interrupt:220 Base address:0xa000

eth0:avahi Link encap:Ethernet HWaddr 00:18:f3:39:65:92
inet addr:169.254.7.24 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:220 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:391 errors:0 dropped:0 overruns:0 frame:0
TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:110681 (108.0 KB) TX bytes:110681 (108.0 KB)

gejzik@saksik:~$ sudo dhclient eth0
[sudo] password for gejzik:
There is already a pid file /var/run/dhclient.pid with pid 8763
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:39:65:92
Sending on LPF/eth0/00:18:f3:39:65:92
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

gejzik@saksik:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth2
#iface eth2 inet dhcp


auto ath0
#iface ath0 inet dhcp


auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp


iface eth0 inet dhcp


auto eth0


gejzik@saksik:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
fuse
lp
sbp2



I would really appreciate if someone of you guys could have a look at it. I tried to solve this by myself but unsuccessfully.

---

