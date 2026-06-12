---
title: "Building a acx1xx wifi driver for ubuntu 12.04"
date: 2012-09-04
forum: Hardware
---

### Post by macguges on 2012-09-04
I've installed Lubuntu 12.04 on an old Dell Latitude laptop with a Netopia wireless NIC:

02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
        Subsystem: Samsung Electro-Mechanics Co., Ltd. Device b230
[http://www.wikidevi.com/wiki/Netopia_TER/WPC11N1](http://www.wikidevi.com/wiki/Netopia_TER/WPC11N1)

This wifi card needs the acx1xx driver, which was not present with the livecd.

As it turns out there's been legal problems with the linux driver, so it's unsurprising that it's missing.  I originally started this post to ask for advice finding this driver, but I expect now the only way I could have this driver is if I compiled my own.

What is the simplest way to create a build environment to compile a new kernel driver in Ubuntu 12.04?  (And maybe finding another PCMCIA NIC might be easier...)

---

