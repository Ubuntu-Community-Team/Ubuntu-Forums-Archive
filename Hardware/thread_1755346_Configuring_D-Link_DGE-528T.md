---
title: "Configuring D-Link DGE-528T"
date: 2011-05-11
forum: Hardware
---

### Post by uaebuntu on 2011-05-11
I have just clean installed Ubuntu 11.04 on 3.06 GHz Dual core P4 with 2GB RAM

```
jim@venus:~$ uname -r
2.6.38-8-generic
```

At the same time I purchased a Gigabit NIC from D-Link, mostly because D-Link is a reputable brand and it said on the box compatible with 2.6.x linux kernal. Had I seen the number of posts with people having trouble I guess I would have got something else! Non of the posts I've seen help.

The original NIC is still in the system and can be seen and is functioning as eth0. The system can see the new driver and the card, here is an extract from dmesg:

[    1.401350] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.401390] r8169 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.401437] r8169 0000:02:02.0: (unregistered net_device): no PCI Express capability
[    1.403219] r8169 0000:02:02.0: eth1: RTL8169sb/8110sb at 0xf8016c00, 5c:d9:98:45:8b:cc, XID 10000000 IRQ 18

and lspci:

02:02.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
02:04.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)

and ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:58:9a:1b:0e  
          inet addr:192.168.11.65  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:fe9a:1b0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79683300 (79.6 MB)  TX bytes:2518122 (2.5 MB)
          Interrupt:17 Base address:0x2800 

eth1      Link encap:Ethernet  HWaddr 5c:d9:98:45:8b:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x6c00 

so as you can see dead as a door nail, no lights on the card and not picked up by the switch.

---

### Post by uaebuntu on 2011-05-11
Ooops.... bought a new cable and the whole thing came to life.

> so as you can see dead as a door nail, no lights on the card and not picked up by the switch.

sort of gave it away if I hadn't been having so many problems with the upgrade earlier I would have gone straight for the hardware solution before blaming Ubuntu!

---

### Post by black&amp;white on 2011-06-19
You've done the thing I want to do...     

Like you I have been put off with the comments on the forums.  

unfortunately I bought 2 of these (what looked like great cards) but have been left in this unsure state and waiting for some time I can throw at it. 

I wanted to add another a card to my box as eth1  leaving the old one that works in as eth0.   once I get eth1 working I'll swap eth0 with my 2nd D-Link card.

What did you do to get it to work?  
let me know the versions of the stuff etc...

Please help...any help from someone who has done it is very much appreciated.
cheers...
BW

---

### Post by uaebuntu on 2011-06-19
All I did was put a new cable in, the one I was using was faulty! 

As a bit of a linux newbie and experiencing a lot of problems with the 11.04 upgrade because of old hardware being used on my test box I automatically assumed the worse (i.e. it was an Ubuntu/D Link problem).

When I fixed the cable and did a clean install of ubuntu 11.04 it all worked fine. To save the fuss, and given the fact it what I did was successful, (I just didn't believe the results and made a basic error on the hardware cable), I would not hesitate in putting two cards in on day one rather than a two stage approach.

I'm not at home at the moment (11.04 & Wireless on my Lenovo N200 laptop) but will send you the driver versions as soon as I am. The info from dmesg "r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded" is however the driver I believe still to be loaded.

---

### Post by black&amp;white on 2011-06-19
So what you recommend is that I fit the D-Links in (eth0, and eth1) and install Ubuntu 11.4 and it all works fine.

I'm installing from afresh

if this is true - I'm very grateful...

it will have to be next week when I try this out... 

many thanks

---

### Post by uaebuntu on 2011-06-20
Back at home and yes,  the Drivers shown in the dmesg section are the current ones used from the fresh install of 11.04 with no problems.

Best of luck and let me know how you get on, any problems I'll do my best to help.

---

### Post by skipi-gz on 2012-07-11
has anyone been able to install the driver? i bought two of these cards. one i installed on an XBMCBUNTU 11.10 machine and was just plug-and-play. the second one i installed on UBUNTU server 12.04 but is not working. i installed the card on the server machine when it was 11.10 and then upgraded hoping that it would help. lspci displays the card.

---

