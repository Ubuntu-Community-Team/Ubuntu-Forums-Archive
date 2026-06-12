---
title: "[SOLVED] The Strangest RAM Breakdown I've Ever Seen"
date: 2008-09-13
forum: Hardware
---

### Post by James_the_dude on 2008-09-13
Just recently my memory completely failed. But first, a little history:

About three months ago I bought 2GB if Kingston DDR2 laptop RAM (two sticks, 1gb ea.) to replace the two 512meg sticks which my computer came  with. The RAM worked great. About a week ago I installed Vista (just to watch *Lost* on abc), I do not know if this is a cause of the problem, or just a coincidence.

Yesterday, while using Vista everything started crashing, first firefox, then Windows Defender, then explorer. I know this sounds like a Vista help request so far, but bear with me. I started troubleshooting: booting into safe mode, scanning for viruses, etc. Basically a lot of weird Vista malfunctions such as blue screens and whatnot lead me to test my memory for problems. The windows memory checker told me "there are hardware problems." It's not very informative, so I used linux's memtest (or whatever it's called) because it's more detailed. About 2048 errors came up during the scan.

At this point I knew a RAM module was broken, but I needed to know which one. I experimented by removing one at a time and running memtest. The very strange thing is that memtest found no errors on either module, no matter which slot it was in, so long as there was only one RAM module in my laptop. Conclusion, this RAM only has errors when both modules are installed.

This made little sense to me. Why would a RAM module be okay on it's own, yet absolutely useless with it's partner? This led me to belive that the problem may not lay with the RAM itself, but with the laptop's hardware which uses the RAM. In order to test that this was true, I took my old RAM and installed *it*. Memtest found no errors with the old RAM, no matter which slot it was in, or weather I had one, or both modules installed. This let me conclude with (I hope well warranted) certainty that the problem was with my newest 2gb RAM, not the computer itself.

The mystery:

Why would one module test ok. And the other test ok. Yet combine the two and they fail with 2048 errors(maybe more, but I stopped the test at that point)?

I don't understand what could be wrong with the RAM, however if the problem were with the mother board itself (or some other component), why does my older RAM work and test out fine so far?

Hypothetical Causes:

Vista fried my new RAM :mad:
A freak power surge destroyed my ram, yet seemingly nothing else.
Gamma ray emissions from a super nova 53.0(10)^6 light years away nuked my RAM.
My RAM is fine, however due to some quantum entanglement, the two modules fail to behave within close proximity of each other because they cannot distinguish between each other (ok, BS pseudoscience, I know...).

Any thought on the matter? Similar experiences?

---

### Post by IntuitiveNipple on 2008-09-13
I'd go with a Lost~Vista entanglement, probably with some reverse spin :)

The old and new memory-modules - are they identical specifications (CAS, bus-speed, etc.) and only differ in capacity?

BIOS - have you checked for any BIOS settings related to setting memory access parameters, and possibly reset the BIOS to defaults. It isn't unknown for BIOS settings to get randomly changed causing knock-on effects like this.

Do you know someone else with a system that will take those 'new' memory modules that you can test them in? That would help determine if there is some motherboard influence at work.

---

### Post by ronnielsen1 on 2008-09-13
>  About a week ago I installed Vista (just to watch *Lost* on abc), 

This works in Linux

[http://www.cucirca.com/2007/05/12/watch-lost-online/](http://www.cucirca.com/2007/05/12/watch-lost-online/)

---

### Post by James_the_dude on 2008-09-13
As far as I know, both my old ram and my new ram have the same clock rates. As far as CAS and bus speed, I don't know. My broken RAM is now about 50 miles away from me, I could probably look at some serial numbers and look up some facts about it in three days. The packaging for my new RAM only told me the amount of ram and clock rate. The clock rate is the same as my old ram. Also remember my new RAM worked for ~3 months before dying.

BIOS Settings: my BIOS does not offer a lot of advanced options but I will check it out and see if anything has changed. I'm installing ubuntu over my entire disk right now, so I couldn't check now.

---

### Post by IntuitiveNipple on 2008-09-13
> **James_the_dude said:**
> Also remember my new RAM worked for ~3 months before dying.
Yes, that is the bit that suggests something in the RAM settings has changed, and why I suggest the BIOS checking.

Some BIOS advanced menus have an option to over-ride the memory's SPD (Serial Presence Detect) settings... I'm wondering if that has happened here, or some similar setting that might affect it such as the FSb (Front-Side Bus) speed (which affects DRAM bandwidth).

Check for things like Interleaving, since you reported that the individual modules pass the tests but together they fail.

---

### Post by James_the_dude on 2008-09-13
I just went through my PhoenixBIOS Setup Utility and there are no options at all which correspond to RAM. Like I said, my BIOS does not allow for many advanced settings.

Is there some way to enter BIOS setup in a sort of "super user mode" with advanced options?

---

### Post by James_the_dude on 2008-09-15
Situation Update:

I tested the faulty RAM modules in another laptop, and the RAM was still faulty. I breathed a sigh of relief, as this further indicated to me that the issue was with the RAM itself, and not my laptop.

I guess I'm still posting about this because I want to know, does anyone know how this sort of thing could of happened? Is it normal for RAM to simply stop working after a couple of months? This was Kingston Value RAM, however it's still supposed to be reliable. Is this sort of problem typically caused by a power surge? Should I be worried about the possibility that my laptop may be prone to frying more RAM?

---

### Post by IntuitiveNipple on 2008-09-15
That sounds like just plain bad luck. Depending on your local laws you should have good cause to return the RAM as faulty and expect replacement units.

---

