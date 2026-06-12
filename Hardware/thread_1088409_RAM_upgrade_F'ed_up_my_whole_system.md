---
title: "RAM upgrade F'ed up my whole system"
date: 2009-03-06
forum: Hardware
---

### Post by DigiTan on 2009-03-06
Has anyone ever heard of this before?  Details are below, but long story short: a 1GB -> 2GB upgrade killed my ability to use more than 512MB RAM.



I had two 512MB RAM sticks and added two more identical ones this week so I could get a full 2GB (4x512MB). [see signature]

When I was done, the system wouldn't POST, and I heard long repeating beeps (the beep code for "DRAM failure/DRAM insertion problem").  I'm positive this is no DRAM defect because I've MemTested them all individually.  I was able to fix that by removing one of the new sticks, but only 0.5GB was detected.  Not the 1.5GB that was actually in.  The BIOS also reverted to safe mode a few times, but I couldn't find any settings that fixed the 0.5GB problem.

After more failed re-arrangements, I got sick of that BS and arranged my original RAMs exactly like they were before the mess.  Only I **still** got POST errors!  Now my PC only starts if I **only** use slot #1.  

I've tried everything.  I hard-reset the BIOS and used compressed air, vacuums, brushes, and contact cleanser on the RAM sockets.  The manual says you can plug RAMs in *any* position and *any* quantity--and I tried every position.  But now I can't even get my original 1GB back!  What the hell is this crap?

---

### Post by prshah on 2009-03-06
> **DigiTan said:**
> 
I've tried everything. 

Looks like you've really tried everything I can suggest; however, here's a couple more tips:

a) Try resetting the BIOS; you'll find a jumper on the board that does this (usually next to the "silver coin" / CR2032 battery). 

b) If your board is dual channel capable, you may need to use ALTERNATE RAM slots; eg, if your slots are A B C D, you will have to use A & C. Usually, dual channel slots are colored differently Eg, BLUE WHITE BLUE WHITE or referred to as Channel A / B, eg; Channel A 0, Channel B 0, Channel A 1, Channel B 1.

c) When attempting to insert the RAM, you may have used excessive pressure, causing a short with the case; try very slightly reverse flexing the board (opposite to direction of force when inserting RAM), or try to visually inspect and confirm that the back of the board is not touching the mounting plate in the case.

d) GENTLY rock the seated RAM clips back and forth; in case of contact "spring" errors.

Hope some of these help you clear up the problem;

---

