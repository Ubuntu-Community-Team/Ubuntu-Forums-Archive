---
title: "permanent wireless connection"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by dompie on 2006-10-05
Hello
I had to use ndiswrapper and wifi radar to make my wireless (Belhin54g) router active
Everytime I start dapper I have to open "networktools", select wlan0 (loopback is visible instead) and press Configure

After that all is OK

Is there no way to let this happen automatically during every start?

ACER 1801WSMi-2.3 with IWPRO 2220 modem

---

### Post by iam_foo on 2006-10-05
> auto lo

iface lo inet loopback


auto eth0

iface eth0 inet static

auto eth1
iface eth1 inet dhcp
wireless-rate 11M
wireless-essid NETGEAR


pre-up ifconfig eth1 up

there is a copy of my /etc/network/interfaces file.
you'll have to run "iwconfig" to get your essid etc..
the last line brings up my interface @ startup.

---

