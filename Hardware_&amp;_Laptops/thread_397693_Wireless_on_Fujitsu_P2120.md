---
title: "Wireless on Fujitsu P2120"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by jhugery on 2007-03-31
I have a Fujitu P2120 and am attempting to get the wireless working on it...  I'm obviously having some issues on it..  When performing lspci I see the hardware correctly identified as a Intersil Corporation Prism 2.5 Wavelan chipset (rev 01).   The first indication of issue is seen when performing an ifconfig -a.  This displays the device, but the hardware id is all zero's.  I'd expect the MAC address here.  I've reviewed /etc/network/interfaces and it appears with the default 

auto wlan0
iface wlan0 inet dhcp

What can I look into next?

---

