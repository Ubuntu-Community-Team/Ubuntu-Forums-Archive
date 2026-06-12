---
title: "wireless on HP Pavilion zv6118ea"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by TheManu on 2005-11-01
Hi there,
I've got a new laptop, HP Pavilion zv6118ea, and nearly everything works with Breezy (with Hoary, the ide controller was too sloooooow).

I'm still not able to make a wireless connection with my laptop: I've tried everything :-) I've found online - even here on ubuntu forums -, but still no connections with ubuntu (yes, the card is working because I can connect with XP).

The network card is (from lspci):

0000:03:02.0: Network controller: Broadcom Corporation: Unknown device 4218 (rev 02)

Obviously I'm using ndiswrapper:

# ndiswrapper -l
bcmwl5 driver present, hardware present

# dmesg | grep wlan0
[4295286.482000] wlan0: ndiswrapper ethernet device 00:14:a5:17:95:d0 using driver bcmwl5, configuration file 14EA:4318:103C:1356.5.conf
[4295286.482000] wlan0: encryption modes supported: WEP, WPA with TPIK, WPA with AES/CCMP

/etc/network/interfaces shows:

iface wlan0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.2
wireless-essid default # it's just because I'm trying to make the wlan working ;-)
auto wlan0 

Everything seems correct... but still no ping :-( What can I do?

Thank you!

---

### Post by Salane on 2005-11-03
what happens when you give the command 
dhclient wlan0

Never mind you are not using dhcp to get ip address. 
are you sure that the router is set up properly. I just upgraded my lynksys with a new revision. Iit set the wireless default to auto configure with my win xp, Those settings wouldn't work with my ubuntu. I had to set the router up properly. I am not at home now to get the configs but do double check how the router is set up.

---

