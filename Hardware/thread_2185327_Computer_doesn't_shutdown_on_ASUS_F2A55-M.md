---
title: "Computer doesn't shutdown on ASUS F2A55-M"
date: 2013-11-02
forum: Hardware
---

### Post by toast78 on 2013-11-02
Hi folks,

I wanted to use Wake on LAN to run a server that isn't permanently available. To achieve this I enabled the Wake on Ring signal, but the computer didn't wake up. My retailer told and me that I have to enable the Power Management Event (PME). So we tried with Ubuntu 12.04 Desktop AND Server. The result was, that when we wanted to shutdown the computer the computer restarted itself but remained in a state where the computer wouldn't start up but couldn't be switched off by hard reset either. 
When we tried to shutdown the computer with WindowsXP, it was no problem. The Wake on LAN Signal worked, too!
So my problem is now, that the motherboard works correctly for the retailer and I can't get my money back.
So this is my setting for configuration for the network adapter
```
 [TABLE="class: notranslate syntaxtable"]
[TR]
[TD="class: linenos"][/TD]
[TD="class: code"]sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    [mark]Wake-on: g[/mark]
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes[/TD]
[/TR]
[/TABLE]


```
So is there any possibility to get the Wake on LAN running?
Thanks in advance.

---

### Post by toast78 on 2013-11-26
UPDATE: I tried with the 64 bit versions of Ubuntu 10.04 and 12.04, too. A BIOS Update of the motherboard didn't help.

---

