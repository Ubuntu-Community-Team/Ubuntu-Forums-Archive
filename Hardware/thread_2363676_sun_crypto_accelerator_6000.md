---
title: "sun crypto accelerator 6000"
date: 2017-06-13
forum: Hardware
---

### Post by fuzzyworbles on 2017-06-13
I got a Sun Crypto Accelerator 6000 off ebay. $50 for 1gbit aes128, as per the data sheet, seemed like a steal, so I swooped up on it. I intend to use it for webdav over ssl, ipsec, and openvpn. Turns out it's not very out-of-the-box happy. After HOURS of googling, I managed to find the RPMs that the Sun documentation refers to, containing the module, firmware, and apparently closed source management utilities (scamgr). I think it's for CentOS and kernel 2.6 or so. Promising, but useless.

Some literature seems to point toward using it with opencryptoki, but for the life of me I can't figure out how. The openDNSSEC config has a blurb on it, some some people out there seem to use this crypto card with that, but the rabbit hole led me nowhere. 

lspci says:  Network and computing encryption device: Oracle/SUN Crypto Accelerator 6000 [mca]

if anybody has any hints, that would be more than what i'm working with now. Thanks.

---

### Post by fuzzyworbles on 2017-06-21
Shameless bump

---

