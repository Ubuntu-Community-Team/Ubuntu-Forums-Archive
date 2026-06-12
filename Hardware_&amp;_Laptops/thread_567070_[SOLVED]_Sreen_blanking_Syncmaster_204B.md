---
title: "[SOLVED] Sreen blanking Syncmaster 204B"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by cyb3rj on 2007-10-04
I've been to the nvnews forums, and I'm hoping there is maybe some help here on this issue.

I am again combating "snow" and blanking.  I have a Samsung Syncmaster 204B and an evga 7900 GS KO.  I once had this resolved, but it returned.

$ uname -a
Linux *** 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

There are two distinct changes I made:
1. I reinstalled Kubuntu because reiserfs was not agreeing with me.
2. I updated my kernel from 2.6.20-15-generic to 2.6.20-16-generic.

Maybe another change affected me -- I uninstalled "Powerstrip" from my windows partition. After doing so, I notice that in XP I need to reconfigure the custom timing every time I login. When Powerstrip was installed I did not need to. Does anyone know if Powerstrip does something to flash settings to graphics cards?

I have recompiled cvt under the new kernel and got the exact same modeline. That mode is the only mode I list for each setting (xorg.conf attached).

The actions I see from this point are
1) Boot into the previous kernel and see if the problem persists
2) Reinstall Powerstrip in case it set a persistent setting in the graphics card
3) buy a new monitor (not desirable)

Any help on this would be greatly appreciated.
__
JW
(GeForce 7900 GS KO, SyncMaster 204B)

---

### Post by arch0njw on 2008-03-06
I changed screen names...

The solution I found for this was to go back to DSUB.  I did not resolve the problems with the DVI connection as there is apparently an issue with this monitor if it was made in China as apposed to Mexico.  Lucky me.

---

