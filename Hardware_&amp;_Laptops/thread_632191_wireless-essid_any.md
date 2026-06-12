---
title: "wireless-essid any"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by Minilek on 2007-12-05
I am using Gutsy on a Lenovo T61 Thinkpad with an Intel PRO/Wireless 3945ABG wireless card.  I can connect to wireless networks just fine if I put that network's name in my /etc/network/interfaces.  However, I would like to be able to put "wireless-essid any" in my /etc/network/interfaces so that the wireless card just connects to any wireless network it finds without me having to specify one.  I used to do this on my old laptop in Dapper without any problems, but it doesn't seem to be working with this laptop in Gutsy.  Does "any" no longer work as a wireless essid?  Below is my /etc/network/interfaces:
> 
auto lo
iface lo inet loopback

auto eth0

auto eth1
iface eth1 inet dhcp
wireless-mode managed
wireless-essid any


As is, this doesn't work (running sudo ifup eth1 tells me that no dhcpoffers are received).  Replacing "any" with the name of the network makes things work.

---

### Post by Minilek on 2007-12-06
Well, at the very least, has anyone managed to use the essid "any" successfully in Gutsy (or is there anyone expericing my same problem)?

---

