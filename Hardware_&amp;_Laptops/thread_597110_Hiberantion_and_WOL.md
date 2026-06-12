---
title: "Hiberantion and WOL"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by xkoudyt on 2007-10-30
I have installed Ubuntu Gutsy 7.10 and I have noticed problems with using Wake On LAN (WOL) from hibernate state. If I shutdown the system via Turn off command WOL works perfectly. In case of hibernation, set up of my ethernet card do not keep the 'g' option which has been set by command:

* ethtool -s eth0 wol g *

and after manual switching on, the command 

*ethtool eth0*

generates following list:

[I]Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes
[/I]

So the problem is that option Wake-on is set to 'd' now (disable wake up) and thus the 
ethernet card cannot be waken up. Have you anybody idea what is wrong.

---

### Post by xdefconx on 2008-01-08
I also looking up for this solutions huhuhuhu... can someone resolve this issue related with Wake On LAN (WOL) on Ubuntu?

---

