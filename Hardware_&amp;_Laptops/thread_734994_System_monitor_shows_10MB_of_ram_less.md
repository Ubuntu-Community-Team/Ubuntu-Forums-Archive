---
title: "System monitor shows 10MB of ram less"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by giuspen on 2008-03-25
I have a laptop with 512MB of ram and 32MB of ram are used from the intel video card.
The system monitor of windows shows 480MB of ram, and so made ubuntu in the past, but lately on my ubuntu 7.10 I started to see only 470MB. Windows continues to show 480, I thought it was a bug but with the new installation of 8.04beta I still see 470MB.
Does anybody experienced something similar? Is this a bug or there is a reason for this?
Thanks and bye.

---

### Post by Oldsoldier2003 on 2008-03-26
> **giuspen said:**
> I have a laptop with 512MB of ram and 32MB of ram are used from the intel video card.
The system monitor of windows shows 480MB of ram, and so made ubuntu in the past, but lately on my ubuntu 7.10 I started to see only 470MB. Windows continues to show 480, I thought it was a bug but with the new installation of 8.04beta I still see 470MB.
Does anybody experienced something similar? Is this a bug or there is a reason for this?
Thanks and bye.

from a terminal type ```
free -m
``` and paste the output here

---

### Post by giuspen on 2008-03-31
> **Oldsoldier2003 said:**
> from a terminal type ```
free -m
``` and paste the output here

beppe@beppe-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           470        465          5          0         38        166
-/+ buffers/cache:        259        210
Swap:          988         37        951
beppe@beppe-laptop:~$ 

he tells me total 470 :(

---

