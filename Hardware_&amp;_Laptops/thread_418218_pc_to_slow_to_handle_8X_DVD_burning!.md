---
title: "pc to slow to handle 8X DVD burning?!"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by swejuggalo on 2007-04-22
Havn't been burning that much for a while... but when I do, no matter the software used, the computer just can't keep up with DVD burning higher than 4X anymore. I'm almost 100% sure it have worked just fine before in Ubuntu 6.10. And I'm 110% sure it worked before when running Fedora Core 5.

Tried reading about hdparm and stuff. Things seem normal when running -tT (comparable performance as in FC5). But commands like -c1 and most other stuff can't be used. Claims to be a "Invalid argument".

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 398297088, start = 0

Normal right?

---

### Post by swejuggalo on 2007-04-22
Might be nice to know that it is a p3 1GHz, 512GB ram and a i815-chipset ;)

---

### Post by swejuggalo on 2007-04-22
think I made it better with settings on multcount, enable IO_support and unmaskirq. Tried to set hdb2 and stuff...when it should be the physical harddrives hda and hdb...

---

