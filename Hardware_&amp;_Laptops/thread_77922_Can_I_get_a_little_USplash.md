---
title: "Can I get a little USplash?"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Xiata on 2005-10-17
Oh yes, time to revive this thread.

USplash is naturally broken because I am using a laptop. VesaFB works properly (albeit the /lib/modules/2.6.12-9-k7/initrd/vesafb.ko: File not found during boot) but what's this? Usplash doesn't support vesafb? Sure vga16fb is the only framebuffer compatible with software suspend, but come on! At least build vesafb support as an optional module and actually have the sources where someone can find it! I don't really move this laptop all that often since it is no longer my primary laptop, but that little eye candy during start would be nice to hide all the console messages I have seen too many times!! That and my roommate laughs that he has it and I don't. Not everyone has the capacity to use vga16fb, in fact, most ati laptop users cannot at all.

I've tried these major bootsplashers:
USplash: Mmmm total darkness... Oh wait thats vga16fb screwing up!
UPower: DirectFB? Init a null device? How? WHY?! *die* (Yes, I filed a bug report over this). Oh yes, building from source and using the deb packages were fun.
Splashy: Pretty picture... magically do nothing! (The init scripts appear to be dead)
Bootsplash: Static image isn't really what I am going for. USplash IS what I want, IF it would work.

PLEASE add vesafb support to USplash. It would make a hell of a difference for everyone who can't use vga16fb.

Alternative bootsplashers would be nice until then (please, no kernel modification splashers). Or a fix to this problem.

---

### Post by matthew on 2005-10-17
[quote=Xiata]USplash is naturally broken because I am using a laptop...

Not everyone has the capacity to use vga16fb, in fact, most ati laptop users cannot at all.[/quote]

I'm sorry I don't have a cure for your problem. 

I wanted to mention that I have 2 laptops, one of which has an ATI card. One is older, PIII and the other is fairly new. USplash works fine in both. 

You definitely could use some help and I hope it comes for you. I felt the need to point out that perhaps the basis for the problem is not the fact that you have a laptop nor that you have an ATI card so that you would feel free to explore other potential causes.

---

