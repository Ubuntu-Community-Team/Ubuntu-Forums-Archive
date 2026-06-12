---
title: "Multicast Routing with 2 network interfaces"
date: 2005-12-02
forum: General Help
---

### Post by skyboy on 2005-12-02
Hi,

I have a very specific question regarding multicast routing with 2 NIC, one WIFI card (wlan0) and one LAN card (eth1).
Also I have to mention that both use DHCP and that wlan0 use WPA-PSK encryption.
Now I want to receive :
239.252.10.1  from eth1
239.252.12.1  from wlan0

both are mpeg2ts streams.
when I use the routing table to associate specific host with specific address, it doesn't work.
It seems I can only receive multicast streams from only one NIC at a time.
Here is my routing table:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
239.252.10.1    0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
239.252.12.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
130.230.50.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0
130.230.50.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         130.230.50.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         130.230.50.1    0.0.0.0         UG    0      0        0 wlan0


what am I doing wrong ? Is it even possible to route specific multicast address on non symetric NIC ??

---

### Post by skyboy on 2005-12-05
Up :) !

---

