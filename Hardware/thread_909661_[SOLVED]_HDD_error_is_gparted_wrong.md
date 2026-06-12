---
title: "[SOLVED] HDD error is gparted wrong?"
date: 2008-09-03
forum: Hardware
---

### Post by Lateforgym on 2008-09-03
is gparted wrong? It takes 1 seconds for it to claim my HDD has a bad sector, without even scanning the drive. That doesnt sound right. 

This is getting really annoying. Gparted says I have a bad sector so it wont load, yet windows says there is no errors. I went to use the Seagate utility for my Seagate drive and it cant identify any of my seagate drives (several motherboards are having this issue). So I yanked the HDD out of my desktop and am running it in my laptop where it almost can identify the HDD (as the drive color shows up) but then the identify program doesnt work and thus the Seagate tools dont work. The Seagate forum is dead with very few questions answered.

---

### Post by tact on 2008-09-03
be more specific about the error.  post a screenshot for example.

Is the HDD in question formatted NTFS?  If a NTFS partition is not shut down properly, cleanly, it leaves a "dirty" flag set and this is instantly recognisable to any disk partitioning tool thats smart enough to look for it.  gparted is smart enough.

without clearer information from you it is impossible to know for sure - but it could be that you are talking about a NTFS partition and it has not been cleanly shut down.

if so - solution is to boot into windows, and do a proper shutdown.  do it 2 or 3 times.  then boot the ubuntu liveCD and run gparted

cheers

---

### Post by Lateforgym on 2008-09-03
I was able to confirm 1 bad sector. Do you think I need trash this drive?

---

### Post by Lateforgym on 2008-09-03
Well, after screwing around for hours on this, I solved the gparted error vs. windows no-error. Windows error checking does not go as deep as other programs do. Unfortunately I was thrown off as Seagate's "Windows" version error checker has a few bugs. Some being conflicts where on some motherboards, it would detect all the HDD. In my case it would not detect any of the HDD's and freeze they system. Yet its "generic" testes only listed "fail" with no other info. 

Seagates other "DOS" version has no problem reading my system. They dont explain that in any stickies, but it became apparent after digging deep into their archives.  I guess they figure most people will just spend the $60 for a new HDD. Also the DOS version was able to give me a repair option that fixed the drive which the Windows "generic" option did not.

---

### Post by tact on 2008-09-03
every HDD has bad sectors, they are just marked as such so they are not used by the operating system (or should be if you run a disk checker over the drive).  so you got bad sectors?  no biggie.  :)

---

