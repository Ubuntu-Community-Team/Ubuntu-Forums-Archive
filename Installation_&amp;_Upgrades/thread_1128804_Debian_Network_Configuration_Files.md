---
title: "Debian Network Configuration Files"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by thegreatone on 2009-04-18
======================================
Ubuntu Debian Configuration Files:
======================================

======================================
File: /etc/network/interfaces
======================================

Static IP example:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 208.88.34.106
netmask 255.255.255.248
broadcast 208.88.34.111
network 208.88.34.104
gateway 208.88.34.110

======================================
Dynamic IP (DHCP) example:
======================================

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

======================================
Interfaces:
======================================

* lo: Loopback interface (network within your system without slowing down for the real ethernet based network)
* eth0: First ethernet interface card
* wlan0: First wireless network interface

Also see "man interfaces"

---

