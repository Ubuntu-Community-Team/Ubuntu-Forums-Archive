---
title: "ALIM5229 says DMA active but mouse stutters, slow reponse"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by mathezer on 2005-11-11
I just installed Breezy on an A7A133 motherboard which has an ALI M5229 IDE interface.  The alim15x3 module is loaded.  hdparm -t returns around 50-60 MB/s.
The problem is that whenever the hard drive or cdrom is accessed, everything pretty much hangs until the ide r/w is finished. The mouse, even interactive typing totally stutter during HD access.

The one last thing that I have to try is building a kernel without ide_generic support as mentioned by somebody somewhere, but beyond that I am out of ideas.

Does anybody have any idea what else to try?  

thanks

-Steve

---

