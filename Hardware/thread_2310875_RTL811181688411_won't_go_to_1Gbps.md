---
title: "RTL8111/8168/8411 won't go to 1Gbps"
date: 2016-01-22
forum: Hardware
---

### Post by Youri_van_Mill on 2016-01-22
Hello guys.

I am running Ubuntu 15.10 and it's just wauw.

But i have one problem with my ethernet.

When i connect to my router, i only get a 100 Mb/s connection but both my router and laptop got a gigabyte interface.

```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
```

```
youri@dreamworld:~$ ethtool enp2s0
Settings for enp2s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

Even when i change the speed to 1000 with ethtool it still says 100 Mb/s in networkinformation..

Driver is r8169.

---

### Post by Vladlenin5000 on 2016-01-22
Hi and welcome.

What router are you connecting to?
Are you sure the Ethernet cable supports 1000? Otherwise falling back to 100 should be expected.

---

