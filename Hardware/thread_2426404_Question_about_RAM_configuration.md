---
title: "Question about RAM configuration"
date: 2019-09-08
forum: Hardware
---

### Post by dora5 on 2019-09-08
I want to put 2 sticks of 4 GB 12800 DDR3 RAM, and 2 sticks of 8 GB 12800 DDR3 RAM, on my motherboard.   

The configuration of RAM slots is shown on the screenshot below from the motherboard manual.   A paired black dimm3 and blue dimm1, a aired black dimm4 and blue dimm2, and the instructions say there must be a stick of RAM in Dimm1 and if using two sticks of RAM they must be in DIMM1 and Dimm 2 - the two blue slots.

This is confusing.  If I'm supposed to pair the RAM by slot color for dual channeling to work, why are black and blue slots physically paired together?    

So, if I put two 8 GB sticks of identical RAM in the blue slots, and two 4 GB sticks of identical RAM in the black slots, will the dual channeling work?   

I'm using Ubuntu 18.04.  The board is Intel DH67BL.   The sticks of RAM are identical except for capacity.  I'm running stuff in Windows in VirtualBox and it lags if I don't give it 8 GB of RAM, and the rest of my system often actually uses more than 12 GB of RAM.

---

### Post by CatKiller on 2019-09-08
> **dora5 said:**
> 
This is confusing.  If I'm supposed to pair the RAM by slot color for dual channeling to work, why are black and blue slots physically paired together?     

The memory channels are represented on your board by each of the sets of two slots: for dual channel to work, you need memory in each channel. 

You should see that you have one blue and one black as one memory channel and one blue and one black as the other memory channel. 

So a matched pair in the blue slots would have half in channel A and half in channel B, so you can access the memory through both channels at once. 

>  So, if I put two 8 GB sticks of identical RAM in the blue slots, and two 4 GB sticks of identical RAM in the black slots, will the dual channeling work?   

That's what the manual says.

---

### Post by dora5 on 2019-09-08
Thanks!   But intuitively one would expect both slots in the same location and of the same color to be the same channel.

What manual are you referring to?  Or are you inferring this from the page I posted?

I thought maybe somewhere there is actually something that explains it.

But I don't actually understand.  Are you saying you need memory in all four slots for dual channel to work?   I thought you had to fill a single channel at a time.

---

### Post by CatKiller on 2019-09-08
> **dora5 said:**
> Thanks!   But intuitively one would expect both slots in the same location and of the same color to be the same channel. 

Before dual channel became a thing, electrical compatibility meant that you had to, in this kind of arrangement, put both in A and then both in B. It was *very* confusing during the changeover. I guess that's why they started colour coding them rather than relying on what was printed on the motherboard. 

>  What manual are you referring to?  Or are you inferring this from the page I posted?

I thought maybe somewhere there is actually something that explains it. 

[This one](https://www.intel.com/content/dam/support/us/en/documents/boardsandkits/desktop-boards/DH67BL_ProductGuide.pdf). I couldn't see what you'd posted because I'm reading on my phone. 

>  But I don't actually understand.  Are you saying you need memory in all four slots for dual channel to work?   I thought you had to fill a single channel at a time.

No and no. If you have one stick of RAM, it doesn't matter which channel you put it in. If you put a second stick in the *same* channel, you can only access one at a time. If you put the second stick in the *other* channel instead, you can access them both at the same time; that's what dual channel access means.

You also need each channel to have the same amount in, so a 4 GB stick in one channel and 2×2 GB sticks in the other channel will work, but 2×2 GB sticks in one channel with 2×1 GB sticks in the other won't. And you need them to all have the same timings so that everything stays in sync.

---

### Post by Skaperen on 2019-09-08
the old way was so you could grow your RAM in increments of any size you want.  now days you are limited to doing that in each channel with an exact match in the other channel.  in some cases, not matching just makes it work in single channel mode.  in other cases, not matching just does not work at all.  perhaps in a few cases, not matching can damage the board, RAM or even the CPU as the memory controller misdirects the power.

---

### Post by Yellow Pasque on 2019-09-09
> **dora5 said:**
> This is confusing.  If I'm supposed to pair the RAM by slot color for dual channeling to work, why are black and blue slots physically paired together? 

Some mobo manufacturers found it more intuitive that way, while others thought the opposite. I'm not sure if they ever got together on one standard color scheme.  

> So, if I put two 8 GB sticks of identical RAM in the blue slots, and two 4 GB sticks of identical RAM in the black slots, will the dual channeling work?  

Partially. Intel has a specific name for this type of operation: Flex Mode [https://www.intel.com/content/www/us/en/support/articles/000005657/boards-and-kits.html#flex](https://www.intel.com/content/www/us/en/support/articles/000005657/boards-and-kits.html#flex)
In your case, the lower 4 GB of each stick will be mapped in dual channel and the upper 4 GB of the 8 GB sticks will work in single channel. So 16GB total would work in dual channel.

---

