---
title: "Is Ubuntu OK in  building Freemat?"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Darktrax on 2009-07-03
Freemat - the open source replacement for Matlab

Its a very powerful package, so we were astonished to find a basic function broken in our Ubuntu 8.10. The log10() function is supposed to be there, according to the help manual.

y = log10(2) yields an error message about a missing file.

So we checked the same package in a Debian Lenny (Mepis) installation.

--> y = log10(2)
    y = 
        0.3010

So might the Ubuntu build of Freemat be something a bit special?
Have you found any applications that actually run, but with some features "missing"?
I find this a bit hard to understand, because its not like a proper crash-'n-burn bug. The program actually works! Its just without some of what is supposed to be there.

---

