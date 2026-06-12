---
title: "WakeOnLAN almost working"
date: 2011-07-25
forum: Hardware
---

### Post by Contrast on 2011-07-25
Greets, everyone. I'm very close to having WakeOnLAN working properly (using ethtool and wakeonlan). I'm able to wake the system up from sleep via wakeonlan. The only problem is that once it goes back to sleep after that, it doesn't wake up properly, but rather reboots. It will keep doing this (rebooting instead of resuming) until I properly reboot the system. Then, of course, I'm allowed to WOL one time, then no more sleep until rebooting all over again.
Here's the output from "ifconfig eth0":
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:04:03:0e  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe04:30e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1744744 (1.7 MB)  TX bytes:357979 (357.9 KB)
          Interrupt:44 Base address:0x6000
```
and from "sudo ethtool eth0":
```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
                                             1000baseT/Half 1000baseT/Full 
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes
```
Any help at all with this would be greatly appreciated, as I'm tired of being torn between an always-available server and power efficiency. :confused:

---

### Post by Contrast on 2011-07-25
Bump.

---

