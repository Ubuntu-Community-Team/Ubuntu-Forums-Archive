---
title: "Kernel Oops when idling: ATI Radeon 9500 Pro memory issue?"
date: 2012-01-15
forum: Hardware
---

### Post by hitsuchi on 2012-01-15
I have an old computer, which runs Ubuntu 11.10 32-bit (originally upgraded from 10.10). I normally use LXDE. Recently I have started getting a Kernel Oops after the computer has been idle for a few hours.  The oops says &quot;Unable to handle kernel paging request at fffffffc&quot;.  In the traceback ttm and radeon were mentioned. I have tested my RAM overnight, and no issues were reported. 

 Specs: Pentium 4, 2.5 GHz.
3 GB RAM. 
ATI Radeon 9500 Pro, 128 MB.

When/if it crashes again, I will copy the entire error message and traceback, for all the good it would do.  

The computer is too old for me to want to buy a new GPU. But is there a way to let graphics run on the CPU instead, or to prohibit the driver from using problematic memory spaces? Is this even the problem? It wouldn't be an issue, but I sometimes leave the computer compiling overnight. And I'd like to keep it that way.

---

### Post by Mark Phelps on 2012-01-16
Sorry, but with that old a graphics card, you are relegated to using the open-source drivers -- which provide minimal support.

AMD/ATI dropped Linux driver support for that card years ago.  So, the config features previously offered with their drivers, and associated catalyst control center, are no longer available with that card -- and have not been since Ubuntu 9.x versions.

---

### Post by hitsuchi on 2012-01-17
I'm not surprised that they dropped support. It is an old card in an old computer. I suspect that it may be failing. When it died the first time, Ubuntu saved it. I was just wondering if anyone knows how to shut it down, so the entire computer doesn't crash when I leave it. If that is even possible. It's just for fun, to see if it can be done.

---

### Post by Mark Phelps on 2012-01-17
> But is there a way to let graphics run on the CPU instead

Sorry, no.

> or to prohibit the driver from using problematic memory spaces?

Also sorry, no.

Crashing the way you describe could be caused by the card failing -- but that's more likely to be experienced while you are using the PC, not when it's idling.

I would suspect that the hard drive, especially if its the same age as the card, is in the process of wearing out.

---

