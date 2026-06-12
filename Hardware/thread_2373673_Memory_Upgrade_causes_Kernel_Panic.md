---
title: "Memory Upgrade causes Kernel Panic"
date: 2017-10-08
forum: Hardware
---

### Post by rsteinmetz70112 on 2017-10-08
I have 16.04 LTS AMD64 on an older AMD64 processor the software is up to date as of yesterday. The Motherboard has 4 memory slots each of which can take 1GB. I had 2 GB in it. I added 2 more GB if identical memory (same brand Kingston and part number) now the system won't boot. The POST memory check passes. During the boot process I get a kernel panic, although not the same on each time.

It is not the memory, the system will boot properly with either set of memory in either pair of slots. I also have tried using 2 1GB sticks with 2 256MB sticks I happen to have and that works properly. I have tried booting using mem=2G in the boot command line, that has no effect.

Possibly some of the boot parameters might help but I'm not sure which to try.

---

### Post by ian-weisser on 2017-10-08
Run memtest to be sure about the RAM. POST misses a lot.
If one RAM stick comes up bad, trade slots to determine if the culprit is bad RAM or a bad slot.

---

### Post by Autodave on 2017-10-09
Also try putting the new sticks in the first 2 slots and the older in the last 2. Or if you already had it that way, reverse it.

I have a computer here that will only function with up to 3 gig in it. It is supposed to take up to 64 gig. 3 or less and all is well. Go over 3 g in any way and it won't work. You may have a bad board or CPU.

---

### Post by rsteinmetz70112 on 2017-10-10
> **Autodave said:**
> Also try putting the new sticks in the first 2 slots and the older in the last 2. Or if you already had it that way, reverse it.

I have a computer here that will only function with up to 3 gig in it. It is supposed to take up to 64 gig. 3 or less and all is well. Go over 3 g in any way and it won't work. You may have a bad board or CPU.

Already tried that. Moved them around in every possible combination. any two will work all 4 in any configuration won't.

---

### Post by Autodave on 2017-10-10
You just may have the same problem as this one that I have. At this point, with everything that you tried, I do not believe it to be a memory stick problem but rather a mobo or CPU issue.

---

### Post by efflandt on 2017-10-11
Have you tried 3 sticks in any positions? My old single core early Athlon64 3200+ (2 GHz) supposedly used a method to access 2 chunks of memory in each cycle without using the dual-channel method that Intel uses. It was finicky about RAM at first. I bought some OCZ PC-3200 RAM on sale that would sort of work for a while in Linux, but not very long in Windows. OCZ told me they would send me RAM that they guaranteed would work, and it did. Many years later when I upgraded RAM I got PNY RAM and it simply worked.

I have not had an AMD desktop since then, so I do not know if newer ones work fastest with matched pairs of RAM or would work as well with 3 slots filled.

---

### Post by rsteinmetz70112 on 2017-10-11
> **efflandt said:**
> Have you tried 3 sticks in any positions? 

Yes.
It would not recognize the 3rd stick but it worked showing 2GB. I also tried some 256MB sticks I had and they worked. I can use 2 1GB sticks and 2 256MB  and get 2.5GB. I'd try some 512 Sticks but that I don't have any.

I also swapped the CPU for an identical one with the same result.

I think I have some other stick of a different brand. I'll try those next.

---

### Post by Autodave on 2017-10-12
Sounds like MOBO is going south on you.

---

