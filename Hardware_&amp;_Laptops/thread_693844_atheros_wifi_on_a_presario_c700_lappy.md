---
title: "atheros wifi on a presario c700 lappy"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by kikonoke on 2008-02-11
I have a c700 that i am trying to run linux on, i have tried ubuntu dapper drake and feisty and now mint 4.0 built around fluxbox. my only problem is the wifi card will not work. i have installed the windows driver through ndiswrapper and whatnot but to no avail. i think the main reason for it not working is because there is a button on my lappy to turn the wifi card on and off but linux dosen't seem to recognize it. but when i run
$lspci | grep Ethernet i get:
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 however when i run $ sudo /usr/lib/linuxmint/mintWifi/mintWifi.py i get:
* I. scanning WIFI PCI devices...
-------------------------
* II. querying ndiswrapper...
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:1B:38:EE:68:9E  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1599531 (1.5 MB)  TX bytes:301602 (294.5 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:38:ee:68:9e
Sending on   LPF/eth0/00:1b:38:ee:68:9e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 39432 seconds.
-------------------------
* VI. querying nslookup google.com...
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.187.99
Name:   google.com
Address: 64.233.167.99

if anyone could help me out with this or perhaps know of a better lappy distro to go with i would appreciate the information.

---

### Post by CyberBob on 2008-02-11
Have a look at the following link - the procedure worked for me with an acer aspire laptop and an atheros chip.  I'm not certain of the specific chip I have (e.g. 5006 or 5007) as none of the diagnostics revealed it.  Might be worth a look,  good luck!

[http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros]("http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros")

---

### Post by kikonoke on 2008-02-12
one thing i need some clarity on; the light on the button to activate/ deactivate the wifi card stays amber nomatter what. does this mean that while running linux i am unable to turn the wifi card on, or is it turing on and the light just isn't changing?

---

### Post by CyberBob on 2008-02-17
I don't think these "activation lights" (for lack of a better term) work reliably in Ubuntu.  Mine is always "off" and yet the wireless is currently active.

---

