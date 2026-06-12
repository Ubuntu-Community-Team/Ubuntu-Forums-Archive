---
title: "Memory not detected"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by leeportnoff on 2007-05-09
I have an IBM xseries server with 8GB of ram.  All 8GB is detected when I start the computer.  
In Fiesty, system monitor shows max of 3.2 GB.  

Console also shows only 3.2GB:

admin3@admin3-desktop:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          3290       3167        123          0          3       2055
-/+ buffers/cache:       1108       2182
Swap:         5914        510       5404
Total:        9205       3677       5527

Can I use all 8GB?

---

### Post by jpeddicord on 2007-05-10
Ouch.

I can already tell you are using a 32-bit install. 32-bit systems/installs only support up to 3.2 GB of RAM, which is why you are seeing that. You will have to install the 64 bit edition to get the full capacity out of it. :-k

(It is a 64-bit server, right?)

Jacob
UAResolved + Subscribed

---

### Post by leeportnoff on 2007-05-17
Correct!  I will try the 64 bit install.
Thanks.

---

### Post by keldrum on 2007-07-10
I've got a xSeries 360 (32 bit 8 way Xeon) with 8GB ram and wonder if there is a way to get access to the full 8. Currently running 32 bit w2k3 ent server which can address all the RAM using the /PAE (physical address extension) boot switch. Is there an equivalent for linux or perhaps an ubuntu server kernel for this purpose?

---

