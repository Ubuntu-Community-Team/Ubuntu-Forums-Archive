---
title: "ethernet card suddenly quit (Inspiron 6000)"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by MoreBikesFewerCars on 2005-08-12
My wired ethernet card (ethh0) has just quit working in Ubuntu. It worked for a few weeks after install (automagically) but won't do anything today. Really... I didn't touch anything before it broke.

Has this happened to anybody? The card is activated, and works fine when I boot the machine into Windows. I have rebooted multiple times in Ubuntu to no avail. I really need a network connection.

The machine is a Dell Inspiron 6000 with an integrated ethernet card.

Thanks.

---

### Post by grj on 2005-08-12
have you tried running

sudo dhclient

---

### Post by MoreBikesFewerCars on 2005-08-13
Well... the network started working again, so I didn't try dhclient. Then it quit working again today, except in Windows. I ran dhclient, and this is what I got:

*******

kcullen@machine:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:13:ce:12:42:d2
Sending on   LPF/eth1/00:13:ce:12:42:d2
Listening on LPF/eth0/00:12:3f:dc:8a:bc
Sending on   LPF/eth0/00:12:3f:dc:8a:bc
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

*********

Any ideas?

---

