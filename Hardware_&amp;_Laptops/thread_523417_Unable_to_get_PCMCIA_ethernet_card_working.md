---
title: "Unable to get PCMCIA ethernet card working"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by asundaresan on 2007-08-11
Hello,

I tried looking for solutions on the forum, but didn't find any successful one. My problem is this. I have a PCMCIA ethernet adapter which I am using on an old laptop with Feisty. 

The card is recognized and I can see eth0 which has the same MAC address as printed on the card. However, when I connect an ethernet cable to the card and try  dhcp, I don't get an IP address. I have tried it on another laptop with the same results. When I connect the cable to a built in ethernet port, it works perfectly. In short the card seems to be detected and so is the eth0 device, but I am not able to dhcp. Is this a card problem or am I missing something. 

The following is some output that may help diagnose the problem.

Aravind.

root@uberwald:/home/aravinds# lspci 
...
03:00.0 Ethernet controller: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

root@uberwald:/home/aravinds# ifconfig eth1 
eth1      Link encap:Ethernet  HWaddr 00:0A:CD:0E:E5:E4  
          inet6 addr: fe80::20a:cdff:fe0e:e5e4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000 

root@uberwald:/home/aravinds# dhclient eth1 
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0a:cd:0e:e5:e4
Sending on   LPF/eth1/00:0a:cd:0e:e5:e4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16

---

### Post by moore.bryan on 2007-08-11
*what's the output of ```
lspci
```?*

---

### Post by asundaresan on 2007-08-21
Hi Bryan,

Thanks for responding. I was on vacation and troubleshooting a friends computer. It seems that he has junked the card. 

Aravind.

---

