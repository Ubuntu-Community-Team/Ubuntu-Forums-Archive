---
title: "wake on lan ethtool"
date: 2013-10-19
forum: Hardware
---

### Post by BMA7PhL on 2013-10-19
i just want to have wol and ssh working(ubuntu 13.04) and after reading man and forum pages everything work prefectly also with forwarding on my router and etc. after all those tryings and changing  settings i decide to have new and clear instalation of ubuntu and now my wol is not working. (new instalation is after complete format and changing partitions)

here is the list for: sudo ethtool eth0

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: yes

i want to ask about current message level, is that an error message? and also(i am not sure) when i on my 1. instalation put this "sudo ethtool -s eth0 wol g" to console, i got an answer(something like parameter was set to...), now i got nothing, 
(also my instalation is dual boot(ubuntu,xp), but xp is on its own harddisk actually unplugged)
i am new one so i hope that this will be something simple:-k, but for now i want to try another network card and after that i will be completly lost...

---

