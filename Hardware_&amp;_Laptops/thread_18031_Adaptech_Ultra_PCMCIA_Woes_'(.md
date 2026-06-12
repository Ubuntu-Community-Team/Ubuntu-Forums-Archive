---
title: "Adaptech Ultra PCMCIA Woes :'("
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by Skid on 2005-03-04
Hi Folks,

I've posted in the networking forum: [http://ubuntuforums.org/showthread.php?t=17687](http://ubuntuforums.org/showthread.php?t=17687)

with a problem of trying to get my card working..  Just to update, if I restart or unplug/plug back in the pcmcia card; I get the follow output in syslog:

> 
Mar  4 11:30:59 localhost cardmgr[6550]: unsupported card in socket 1
Mar  4 11:30:59 localhost cardmgr[6550]:   product info: "Adaptec", "Wireless PC Card V3.0", "", ""
Mar  4 11:30:59 localhost cardmgr[6550]:   manfid: 0x9005, 0x0021  function: 6 (network)


However, looking online apparantly this card is supported.

Is it a pcmcia configuration error?  Should I re-compile a kernel by hand and include it?

Thanks in advance,

Skid

---

