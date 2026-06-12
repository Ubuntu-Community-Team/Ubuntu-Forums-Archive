---
title: "Wireless connection drops"
date: 2005-11-12
forum: General Help
---

### Post by LinuxWiz83 on 2005-11-12
I been loosing my networking connection a lot with my wireless LAN, some not for hours but some times within minutes, it even does it on bootup sometimes. Here is the message i get when i do theses commands and when it gives me that message i have to reboot to get my connection back. So i was wondering if anyone knows if there is a fix for this?

scott@UNIT4:~$ sudo modprobe -r ndiswrapper
scott@UNIT4:~$ sudo modprobe ndiswrapper
scott@UNIT4:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:c0:49:ee:f8:71
Sending on   LPF/wlan0/00:c0:49:ee:f8:71
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
Trying recorded lease 192.168.2.6
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

---

### Post by dbott67 on 2005-11-12
A couple things:

1. Reset your wireless access point.  The cable/DSL routers are just dedicated application servers running some variant of linux (in most cases).  Anyhow, they are prone to having some services stop functioning (DHCP, etc.).  Try cycling the power of the router/AP and then try to obtain an IP.

If this cures it, check your AP-vendor's website for an updated firmware.

2. Do you have any other wireless devices in the vicinity of your AP (or are you close to someone who might, such as an apartment building)?  At my house, using the cordless phone kills my wifi access.  Many consumer electronics (such as cordless phones, microwave ovens, etc.) run in the same frequency range as wifi routers (2.4 GHz).  Make sure that they are not in use when trying to connect.

3. Some people have posted issues with their laptops connecting to other APs (such as a neighbour) instead of their own.  At a terminal, type:
```
iwlist wlan0 scanning
```
and post the output here.  If you see other APs in addition to yours, it could be that your computer is trying to connect to a different AP.

Could you also post the output of:
```
sudo cat /etc/network/interfaces
```

-Dave

---

### Post by LinuxWiz83 on 2005-11-12
This is only happening on Ubuntu not on a Windows or Linspire system.

1 - done , 2 - doesn't happen , 3 - none show accept me because there mostly senior citizions around here

> File: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Murrow-Network
	wireless-key1 b47c1a307727a0ec356844cc49
	wireless-key b47c1a307727a0ec356844cc49

auto wlan0

---

