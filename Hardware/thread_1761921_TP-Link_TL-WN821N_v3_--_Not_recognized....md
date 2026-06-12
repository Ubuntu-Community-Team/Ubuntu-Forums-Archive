---
title: "TP-Link TL-WN821N v3 -- Not recognized..."
date: 2011-05-18
forum: Hardware
---

### Post by Mirddyn on 2011-05-18
Hi!

I have bought TP-Link TL-WN821N wireless USB adapter. Sadly, I found out too late, that it is v3, that means, that it uses Atheros ar9287 chipset...

Even though it isn't difficult to find guides on how to install this kind of chipset all the guides somehow fail to work with the USB.

I have been searching more then a month (really) for any kind of info and I haven't got any at all....

It looks, like the problem isn't with the actual drivers, but with the system recognizing the card. I can use it, but instead of light speed internet I get maximum of 1mb/s (on network, where I have usually 30++mb/s) + the connection often falls down.

Here is output of airmon-ng:
```
Interface    Chipset        Driver

wifi0        Atheros        madwifi-ng
ath0        Atheros        madwifi-ng VAP (parent: wifi0)
wlan1        Unknown     usb - [phy2]

```

As you can see, the chipset isn't recognized...

ifconfig output:
```
wlan1     Link encap:Ethernet  HWaddr 54:e6:fc:87:04:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thank you VERY VERY VERY much for any kind of help :)

---

### Post by Mirddyn on 2011-05-21
*bump* sorry, but I really need help

---

### Post by runesvend on 2011-11-23
TL-WN821N v3 works fine for me in Oneiric. It seems stable in Oneiric while in Natty it sometimes crashes the computer and I have to restart to get it working. It autodetects for me both in Natty and Oneiric and sees networks without problems. It claims to get only a 1Mb/s connection speed, but I can download from the internet with 1.2MB/s so that isn't true.

```
wlan0     Link encap:Ethernet  HWaddr f4:ec:38:89:73:ef  
          inet addr:192.168.2.111  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f6ec:38ff:fe89:73ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:346734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:522359724 (522.3 MB)  TX bytes:14625810 (14.6 MB)

```

---

