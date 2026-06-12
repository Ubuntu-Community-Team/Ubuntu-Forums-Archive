---
title: "Can not get Gigabit speeds on Attansic L1 &amp; Asus P5K"
date: 2015-05-30
forum: Hardware
---

### Post by catolh on 2015-05-30
Hello there

I have been having some some trouble with my Ubuntu server. I have exchanged my router with one wich has Gigabit capabilities (Asus RT-N56U), but i can not get my server to use gigabit speeds for some reason. I have been playing around with ethtool but nothing seems to work.

Some info:
 lshw -C network output:
```
*-network
       description: Ethernet interface
       product: Attansic L1 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1b:fc:8e:99:c6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff
 
```

ethtool output:
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x0000003f (63)
                               drv probe link timer ifdown ifup
        Link detected: yes

```

I have tested the CAT6 cable on another computer (Running Windows 8.1) and it shows Gigabit within seconds of plugging it in.

I have tried to run:
```

sudo ethtool -s eth0 speed 1000
Cannot advertise speed 1000

```

lsmod |grep atl1:
```
mii   13934  1 atl1

```

I have tested all four ports on my router but nothing changes. All of this leads me to believe that the driver wich is bundled with ubuntu is not working properly. I have tried to download the driver from asus support (Asus P5K motherboard), but when i try to install it only gets insanely complicated for me:

```
make install
Makefile:102: *** Linux kernel source not configured - missing version.h.  Stop.

```

I hope someone experienced can shed some light on this issue, as i really want to take advantage of higher network speeds.

*edit*
I see now i have posted this in the hardware section, when it should of been in the network & wireless. Sorry about that.

---

### Post by tgalati4 on 2015-05-31
Check your cabling.  You need Cat5e or Cat6 to get gigabit speeds.  Most (if not all) gigabit cards are auto-detecting and will drop to 100 mbit/sec speeds if the cabling or port on the other end is having problems.

---

### Post by catolh on 2015-05-31
Hi, and thanks for replying.

I am aware of this, and i have tried two Cat5e cables and one Cat6. All of them gives me gigabit speeds on my laptop wich has windows 8.1 installed. This leads me to believe that it is a driver issue.

---

