---
title: "X completely freezes"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by vb7prog on 2005-04-08
Ok, I like the looks of Ubuntu, and am eager to test it out. 

But, my X locks up 100% about 5 seconds after clicking the mouse.
its a bad freeze to cant even get into a console with ctrl+alt+f1

It's the same in

4.10
5.04 RC
and 
5.04

I heard something about an nvidia problem but I couldn't find a clear fix, and don't think it is the problem because even 4.10 locked up ??

I'm running a 2400 amd sempron with an nvidia gforce 4 mx, if this helps?

---

### Post by vb7prog on 2005-04-09
ok, its definately an nvidia thing, because I reinstalled using my ati card and its solid, very nice, but would like to be able to use a nvidia based video card

---

### Post by badriram on 2005-05-27
Well hate to bring up an old thread, but X freezes up on an Athlon 64 machines with X600 too.
I tried 64 bit and 32 bit version of ubuntu and kubuntu with no avail.

There are no error messages in the kernel log or X log after the force restart. What is interesting however is that if i switch to the console right after X pops up, I can continue using my computer without any problems. But the moment i try to switch back to X it freezes are a few seconds....

I also tried the ati driver, vesa, radeon and fglrx... same results. GDM or KDM can also be ruled out as it freezed even if lauch X from command line skipping G/KDM. Also tried disabling ACPI.

I am going to try a few more things, but seems like there are no easy solutions.

---

