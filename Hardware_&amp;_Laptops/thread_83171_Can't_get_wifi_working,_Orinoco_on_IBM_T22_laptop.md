---
title: "Can't get wifi working, Orinoco on IBM T22 laptop"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by sharp11 on 2005-10-28
I have a classic Orinoco gold card (rebranded 2Wire) and an old T22. The card works fine under Knoppix livecd, but i've not been able to get it running under Hoary. (Haven't upgraded to Breezy bc i can't risk downtime right now -- I'm nowhere near linux expert.)

I can see the drivers in lsmod:

```
orinoco_cs              8968  1
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
pcmcia                 21380  5 orinoco_cs
pcmcia_core            53568  3 orinoco_cs,pcmcia,yenta_socket
```

And dmsg doesn't appear to have any wifi errors:

```
eth1: Station identity 001f:0001:0008:002a
eth1: Looks like a Lucent/Agere firmware version 8.42
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:B6:0C:59
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
eth1: no IPv6 routers present
eth1: no IPv6 routers present
eth1: no IPv6 routers present
```

Here's my ifconfig (eth0 is my wired connection):

```
eth0      Link encap:Ethernet  HWaddr 00:03:47:BA:92:25
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:feba:9225/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18608 errors:10 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000
          RX bytes:21891783 (20.8 MiB)  TX bytes:4728100 (4.5 MiB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:B6:0C:59
          inet6 addr: fe80::202:2dff:feb6:c59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:87 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

lo [removed from output]

```
Here's output of trying ifup eth1:      
              
```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:02:2d:b6:0c:59
Sending on   LPF/eth1/00:02:2d:b6:0c:59
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Finally, here's my /etc/network/interface: 

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid kaimen

auto eth1

auto eth0

```

---

