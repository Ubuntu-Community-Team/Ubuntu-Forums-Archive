---
title: "Netgear WG111 v2(or is it the v1?) works under feisty"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by philcolbourn on 2007-09-26
Others have had success with their WG111v2s. Mine and a few others have had problems. It appears that Netgear made WG111v2s that are actually WG111v1s (which are distinct from WG111s). The netgear site sort-of tells you this on a help page for TiVo from memory.

Mine is a Netgear WG111v2
FCC ID=PY3WG111V2
SN=WG72149ZDXXXXXX
Vendor:Product=0846:4240 (these are the magic numbers)

On my AMD64 I thought I would try it after I had trouble with my ZD1201. To my pleasant surprise it worked.

The driver loaded was prism54usb.

My kernel is currently 2.6.20-16-generic (although I am moving to gutsy so this will not be for long).


It came up with wlan0 and a mystery wmaster0 interface

I am using 128bit WEP.

---

