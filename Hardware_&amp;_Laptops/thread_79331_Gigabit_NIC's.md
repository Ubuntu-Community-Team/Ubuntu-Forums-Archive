---
title: "Gigabit NIC's"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by gary79 on 2005-10-20
Hi guys,

I am building a small network and file server (FS). I want a gigabit network with samba/Ubuntu 5.10 on an amd 1700+ with a kt333 mobo. Each of current users and the FS do not have a gigabit NIC on-board so require PCI NIC's.

My questions is: From the range of PCI NIC's on these two sites, [DragonPC]("http://www.dragonpc.co.nz/c.aspx?r=&c=Hardware&s=Network+Equipment&ss=PCI+Card+10%2f100%2f1000&ssid=") [ascent]("http://ascent.co.nz/HardwareCategory.aspx?Catname=Network%20cards"), which NIC is likely to net me the best “bang for buck” in terms of speed, stability and value for money.

I've googled info on some of NIC but it hard to find anything of real use. What I am hoping for is someone that has experience or knows good review references.

Cheers,

Gary.

---

### Post by Mathboy on 2005-12-07
It's a shame nobody has answered this yet...

I've managed to get the D-Link DGE-530T working OK with the skge (Marvell Yukon I) driver, and have had trouble with Realtek 8169s cards (they only support jumbo frames up to 7kb). 

Surely someone else out there must be happily using an Ubuntu server on a gigabit network in a mixed Windows/Linux environment.... !

---

### Post by benlen on 2006-03-24
How well did you managed to get it to work Mathboy?


I have a D-Link DGE-530T nic-card in my Ubuntu 5.10 fileserver, but cant get it to perform better than my old 100Mb/s card. 
It's connected to a D-Link DGL-4300 switch, as are my two other pc's. They have great gigabit performens. 600MB in 60 sec.
To or from my server, 600MB would take about 10 minutes.

I'm using skge-driver.


From my server:
```

$ sudo ethtool -i eth0
driver: skge
version: 0.7
firmware-version: N/A
bus-info: 0000:00:07.0

$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x00000037 (55)
        Link detected: yes
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:3D:F3:77:8F
          inet addr:192.168.0.127  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fef3:778f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44188479 (42.1 MiB)  TX bytes:100338333 (95.6 MiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2748 (2.6 KiB)  TX bytes:2748 (2.6 KiB)

```

---

