---
title: "[Problem] Asus A8N-E How to run 3 sticks of RAM?"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by PPPP on 2008-03-10
I have been running dual channel 2x512MB on A8N-E.  I just got one stick of 1024MB and I wanted to stick it in.  I've tried a few configurations but each time when I have all three in, my system wouldn't boot.

The one way I can get 2 of them in and booted is when the 1024 one is in B2 and one stick of 512 in B1.  Any idea how I can get this to work?

---

### Post by 4l13n666 on 2008-03-11
Hmm...

Maybe you should try to get exactly the same RAM's in all slots? Ex: 2 Kingston 1GB. Don't put RAM's with different memory capabilities together, it never has a good outcome.

---

### Post by PPPP on 2008-03-11
hmm...I guess I'm too much of a n00b...I bought the 1 stick of RAM hoping to add the total to 2GB..:(

---

### Post by 4l13n666 on 2008-03-11
Well if you have two RAM sticks with the same memory range and capabilities, there should not be any problems. I had the same problem. I bought two 1GB RAM sticks but i put them in the wrong slots so i didn't get to enjoy dual channel until i figured it out :)

---

### Post by PPPP on 2008-03-11
I have 2 sticks that are vendor-dual channel which work perfectly.  But my problem is when I wanted to add a single stick of 1 GB.  Was that what you ran into as well?  It would suck if I can't use all three :(

---

### Post by 4l13n666 on 2008-03-12
So are you saying that you already have 2 GB ram and you want to add one more stick so that you get 3GB?

If so, you need to keep some things in mind.
First off, an odd number off memory modules will not work for example, if you have 2GB in dual channel mode, and then you add another 1Gb stick in a third slot, it will not work. The reason for this is that you have two slots filled which creates the "dual channel" mode, but one stick which is not in dual channel mode. What this means is that your computer will not run dual channel mode because it has an uneven number of memory sticks.

Something that you could try in order to solve your problem is to have two 1GB sticks in the slots which creates the dual channel mode, and then in the remaining two slots you can put two x512MB sticks. You also need to consider that all the memory sticks have to run at the same speed. For example, you cannot have two x512MB sticks at different speeds and two 1GB sticks at the same speed. They all need to be at exactly the same speed.

On windows machines, there is no point of using more than 2GB of ram since Windows doesn't detect more than 2GB UNLESS you want to overclock.

And finally, there is no real differance between running on 2GB dual channel or 3GB dual channel, the only differance is that you will have more memory at your disposal.

---

### Post by PPPP on 2008-03-12
No, I originally have 2 sticks of 512MB.  Now I bought a stick of 1GB.  From the looks of it, it doesn't seem like I could get all 3 to work...:(

---

### Post by egalvan on 2008-03-13
> **4l13n666 said:**
> So are you saying that you already have 2 GB ram and you want to add one more stick so that you get 3GB?

If so, you need to keep some things in mind.
First off, an odd number off memory modules will not work for example, if you have 2GB in dual channel mode, and then you add another 1Gb stick in a third slot, it will not work. The reason for this is that you have two slots filled which creates the "dual channel" mode, but one stick which is not in dual channel mode. What this means is that your computer will not run dual channel mode because it has an uneven number of memory sticks.

Depends on motherboard and BIOS. Dual channel REQUIRES even numbers of RAM sticks, but some mb's will default to non-dual if they find odd number, and some mb's need BIOS setting set;

I run mb's with odd numbers all the time. I find that server-class boards tend to be strict with "pairs-only".

And the old conundrum... do I want MORE memory? Or FASTER memory? Do I want to rich, or famous?

> **4l13n666 said:**
> 
You also need to consider that all the memory sticks have to run at the same speed. For example, you cannot have two x512MB sticks at different speeds and two 1GB sticks at the same speed. They all need to be at exactly the same speed.

Need to differentiate between "rated" speed and "running" speed. Most memory can run one or two steps slower than labeled, few can run faster than labeled. The speed that memory runs at is set by both mb and ram. The mb can't run faster than rated (assuming no O/C)  and the memory will run at the SLOWEST ram the mb finds. One PC3600 paired with a PC2100 will run at PC2100.
Again, I run mb's with mixed memory, although I TRY to have matched ram for reliability.

> **4l13n666 said:**
> On windows machines, there is no point of using more than 2GB of ram since Windows doesn't detect more than 2GB UNLESS you want to overclock.

Overclocking has what to do with memory SIZE? Overclocking is a SPEED issue, not SIZE.

And Windows XP maxes at  3GB, regardless of speed. And no, it cannot see more.
Linux, XP-64 and Vista are another matter.

And the mb has to be able to see the memory as well. Some chipsets are limited to 3GB max.
Others can be even lower, some as low as 1.5GB, which may be the OP's problem.

And mb's have a limit on max size of ram in each slot. Some top out at 256m, 512m, 1g, 2g, etc. 
Again, this can be a problem/limitation trying to stuff more memory into and older machine. I have a P-III 933mHz machine that tops out at a measly 256MEG, and another P-III 933mHz that is running 4GIG, a 16-fold increase.
I'd suggest a little reading of the mb owner's manual. Should be available on the mb manufacturer's web site, along with the latest BIOS up-date, which can be needed for max ram/cpu usage.

> **4l13n666 said:**
> And finally, there is no real differance between running on 2GB dual channel or 3GB dual channel, the only differance is that you will have more memory at your disposal.

No arguments here, 3 is more than 2. :popcorn:

---

