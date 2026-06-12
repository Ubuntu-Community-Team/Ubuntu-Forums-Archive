---
title: "HowTo: Ubuntu 7.04 (Feisty) on Toshiba Satellite A215-S4807"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by mameisam on 2007-09-12
Spent 3 days installing Ubuntu on my Toshiba AMD Turion 64 Dual Core with ATI Radeon Mobility Xpress 1200 (x1200) graphics chipset and Atheros AR5007EG wireless, so thought it might be helpful to put the links in the same place. I tried the procedure below for both 64bit AMD version and 32bit x386, though in the end settled with 32 bit version cos wireless stopped working on 64bit version for some reason.

0. Choose alternate ubuntu install CD (32 or 64 bit), cos the graphical install will not recognize the card.

1. Installing Windows XP drivers for Atheros AR5007EG wireless chipset:

Do the Compiling Latest Version of Ndiswrapper section here to update the headers and remove old version:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Download drivers for XP (not vista!) from here (32 or 64 bit, accordingly): 
[http://www.atheros.cz/download.php?atheros=AR5007EG](http://www.atheros.cz/download.php?atheros=AR5007EG)

Install Ndiswrapper and drivers:
[http://docs.google.com/View?docid=dtvgpkz_46fv8dwf&pli=1](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf&pli=1)

Update /etc/network/interfaces:
add the following (in case you gonna use DHCP), If you have eth0 section, comment it out.

auto wlan0 
   iface wlan0 inet dhcp
  wireless-essid network-name-here
  wireless-mode managed
  wireless-channel 1


2. Installing the ATI Radeon Mobility Xpress 1200 fglrx driver. (VESA/radeon/ati driver does not appear to work):

[http://help.ubuntu.com/community/BinaryDriverHowto/ATI](http://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Good luck!

---

### Post by thinkcow on 2007-09-27
Just for info:

This HowTo can also be used for the Packard-Bell EasyNote MX52-B-009!

:KS

---

