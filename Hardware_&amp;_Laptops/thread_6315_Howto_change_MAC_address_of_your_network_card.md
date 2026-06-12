---
title: "Howto change MAC address of your network card"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by macavity on 2004-11-27
If your ISP wants you to call them everytime when you change your hardware (as my ISP does):

$ sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
        [COLOR=Red] hwaddress ether XX:XX:XX:XX:XX:XX (insert here your old MAC) [/COLOR] 
name Ethernet LAN card

auto eth0

---

### Post by knappen on 2004-11-27
I did not know that you could change your MAC address. Though it was embedded in the hardware.

Good to know!

---

### Post by macavity on 2004-11-28
[QUOTE=knappen]I did not know that you could change your MAC address. Though it was embedded in the hardware.

Good to know![/QUOTE]

You are absolutely right!  =D> This method works on software layer, not on hardware - in fact, it changes MAC for interface, not for network card (but it looks like so).

---

### Post by knappen on 2004-11-28
Thats what I thought as well.

---

