---
title: "ATI fglrx and T400"
date: 2009-03-13
forum: Hardware
---

### Post by david.birch on 2009-03-13
I have a t400 causing pain getting the ati drivers to run properly, i never seem to get DRI loading. I have tried to uninstall all i can think of that might conflict, but never seem to get intel-agp/agpgart loading with intrepid 8.10 - X just never loads DRI with restricted driver set, but latest ati drivers just seem to cause a screen corruption. On my old HP Compaq nx8220 with Radeon X600 (where 8.10 & fglrx worked fine) i get some modules loaded as per:

 lsmod | grep fglrx
fglrx                1813960  23 
agpgart                42184  2 fglrx,intel_agp

but not similar on my t400 (ati HD 3400)

Should the agpgart module be loaded on this hardware?

thanks

---

