---
title: "Conky/htop dont give same info as top"
date: 2008-11-22
forum: General Help
---

### Post by m0ntels on 2008-11-22
I've been using conky for a while now, but recently I noticed that some things didn't look right.  The thing that tipped me of was the number of running processes it showed.  

Right now conky shows 201, htop shows 171, and top shows 112.  All I Have running is Firefox, 2 terminals, and conky.  Also for CPU usuage, htop says 7.9% and htop shows 3.7%.  Conky has RAM at 310MB, hop also shows 310, but top says 806.

Any ideas as to why none of the tool are showing the same info?  I'm running an Athalon XP3000 w/ 1GB RAM and Mint 5.0/Hardy.

---

### Post by Bruce M. on 2008-11-22
> **m0ntels said:**
> I've been using conky for a while now, but recently I noticed that some things didn't look right.  The thing that tipped me of was the number of running processes it showed.  

Right now conky shows 201, htop shows 171, and top shows 112.  All I Have running is Firefox, 2 terminals, and conky.  Also for CPU usuage, htop says 7.9% and htop shows 3.7%.  Conky has RAM at 310MB, hop also shows 310, but top says 806.

Any ideas as to why none of the tool are showing the same info?  I'm running an Athalon XP3000 w/ 1GB RAM and Mint 5.0/Hardy.

WoW! That doesn't look good, but without seeing your conky code it's difficult to tell.

Repost your question in: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865"). It's turned out to be one of the biggest conky help threads here. Also show your code when there so people can see it, a screenshot would be nice too.

Have a nice day.
Bruce

---

### Post by sdennie on 2008-11-22
There is no definitive way to report those two values so it's not surprising that they differ between programs.  For example, in the case of memory, top is reporting the cache as used memory (which, technically it is but, not really) whereas other programs may not.  My guess is that if you typed "free -m" you'd see the 310M number and the 806M in the output.  With regards to the process count, do you count kernel spawned "processes" or not?  top does whereas htop doesn't.  These are differences you are seeing.

---

