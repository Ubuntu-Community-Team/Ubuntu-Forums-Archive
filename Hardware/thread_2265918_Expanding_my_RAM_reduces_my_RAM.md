---
title: "Expanding my RAM reduces my RAM"
date: 2015-02-18
forum: Hardware
---

### Post by swilson11235 on 2015-02-18
I have a system76 Leopard Extreme running Ubuntu 14.04 LTS with 4 x 8 GB Crucial Elite Quad Channel DDR3 - 1866 MHz of RAM. I bought another identical stick of RAM to increase my memory, but when I insert it into the machine, my total available RAM drops to 24 GB. I have four open RAM spots, but they are all colored black as opposed to blue for the spots that always had memory. Anybody know if this is a problem with the OS, motherboard, or something else?

---

### Post by TheFu on 2015-02-18
Not all RAM is compatible. Different sticks have different timing and may not work with other sticks.  Over the years, RAM has become much less picky, but sometimes ... 

Also, some motherboards only support specific RAM configurations. Check the manual for what is supported or not. Usually RAM must be added in groups of 2 or 3 identical sticks.  1 stick is usually only supported when only 1 stick is installed.

---

### Post by tgalati4 on 2015-02-19
What is your motherboard chipset?  Many Southbridge chips have an addressing limitation.  The density/layout of the RAM stick becomes important.  Do you have 8 chips on your stick or 16?  Also there are memory slot limitations.  Black and Blue are normally matched pairs (or triples).  Fill the black and blue evenly.  Uneven slot fills will slow down your memory access.  Try another stick to balance out the slots, but consult with System76 for known limitations.

---

### Post by swilson11235 on 2015-03-10
Thanks for the reply. I currently threw the memory into another computer and have been too busy to get back to the problem, but I'll update when I have time. By the way, the mother board is the [ASUS P9X79_LE]("http://www.asus.com/us/Motherboards/P9X79_LE/"), which should support up to 64 GB, and what I have is 8 identical sticks and 8 slots, so I thought it should work.

---

### Post by TheFu on 2015-03-10
The OP read like you'd added 1 stick to a system that had 4 already for a total of 5.
Can you please clarify?

In the old days, if you didn't buy the RAM all at once (same exact model), it might not work together. Different lots, didn't always work together. 

The MB manual will say which RAM configurations are supported.  If they are all the same size RAM, same exact model and you filled all 8 slots, it could be that 1 of the sticks is bad. Most vendors have a lifetime warranty - so you just need to try them all out until you determine which of the 4 new sticks is the trouble maker.
Pull the original 4 sticks and leave only the new ones - in the same slots as the old RAM used.
Test - if it works - then it is the MB RAM slots, right?
If it fails, pull 2 of them out - they are usually paired in the MB slots and test. If it fails, you know that at least 1 of those two sticks are bad ... test the other 2 sticks - hopefully they will work.  No you just have 2 sticks to test. Insert 1 at a time and test. That should determine which stick or both are bad.

There are lots of ways to eliminate working from non-working RAM. It just takes time, if the issue is intermittent. Hopefully, it isn't the MB RAM slots.

---

### Post by swilson11235 on 2015-03-10
I have a system with 4 sticks, and I added 1 more and booted it up, which caused a drop in memory. I have a total of 4 to add, but I didn't put them all in after the first failed to bring the memory up. I'll try exactly as you suggested and attempt to track down if it is a faulty stick, an unbalanced placement, or something else. Once the jobs on my computer finish running, and I can shut it down, I'll get back to you.

---

### Post by TheFu on 2015-03-10
Most computers only support odd number of sticks if that number is 1.  IME.

---

### Post by swilson11235 on 2015-03-10
Yup, I think that was the problem, everything is working now. I think I tried an even number of sticks at one point, but I bet one of the sticks wasn't seated properly. Thanks so much for the support!

---

