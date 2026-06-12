---
title: "Solved problem w/ HP LaserJet 3050 (and possibly others)"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Mud.Knee.Havoc on 2008-03-26
I have an HP LaserJet 3050 all-in-one printer.  It worked perfectly from day one under Ubuntu, but one day (after an automatic upgrade), it wouldn't print text.  It would print PDFs perfectly, but not text.  The text would come out in lines, but the letters would be all blurred together as if somebody typed ten sentences out on each line.

I didn't have the time to spend figuring it out, but I got a few minutes tonight to devote to it.  The problem was simple to solve.  I just switched the driver from "Postscript (Recommended)" to "hpijs".

Things seem to be working fine now. 

I just thought I'd throw this out there in case anybody else was having the same problem.  Note: I did initially install the driver from HP's website.

---

### Post by blair on 2008-03-26
Drivers can make a big difference. I have an HP P3005dn printer and the default "recommended" driver by default prints out 5 copies of every print job. lots of extra, unwanted pages printed. Switching to the hpijs driver immediately solved the problem.

---

