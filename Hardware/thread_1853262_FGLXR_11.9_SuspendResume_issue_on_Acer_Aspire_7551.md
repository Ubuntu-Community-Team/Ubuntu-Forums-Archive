---
title: "FGLXR 11.9 Suspend/Resume issue on Acer Aspire 7551-7422"
date: 2011-10-01
forum: Hardware
---

### Post by TuxIsAwesome on 2011-10-01
Hello, having a serious issue with FLRGX 11.9 and my Acer Aspire 7551-7422, which is sad because I love this laptop to death.

My issue merely stems from my inability to suspend/resume at all. I only get a black screen and nothing else when attempting to resume. It's rather irritating and I am hoping someone has some sort of a fix for this.

I must use the 11.9 FRLGX drivers however, otherwise I get graphical corruption everywhere. Open-source drivers aren't an option either, I need my power management. 

So if anyone has any thoughts on this one, can you please help me?

I'm running Onieric Ocelot, 64-Bit

---

### Post by alenp on 2011-11-03
try this (remove fglrx, use radeon driver): [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

solved the problem for me on an Acer 5253 with a Radeon HD 6310 (and 3D / compositing still work fine).

---

