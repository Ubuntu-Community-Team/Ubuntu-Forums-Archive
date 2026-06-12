---
title: "Qualcom Atheros QCA8172 wake on lan problem"
date: 2014-08-18
forum: Hardware
---

### Post by rklauco on 2014-08-18
Hello all.
I bought extremely cheap Lenovo G500 and it has fantastic value-to-price ratio and running trusty with no problem (kernel 3.13.0-32-generic x86_64).
I have one small problem - the Wake on lan feature is not working.
I cannot find BIOS setting for enabling WoL and ethtool spits no WoL line:
```
Settings for p2p1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x000060e4 (24804)
			       link ifup rx_err tx_err hw wol
	Link detected: yes

```
Does anyone have some hacks I can try to enable WoL? I googled everything, but I was not successful.

---

