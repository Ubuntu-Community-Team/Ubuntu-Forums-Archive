---
title: "Hard Disk clicks every few seconds on hp laptop"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by p2bp2b on 2008-01-10
I recently bought a hp dv2617us laptop (Intel Core 2 Duo)
I set it up to dual boot Ubuntu 7.10 

The laptop has a FUJITSU 160 GB SATA hard drive.

I have noticed that the hard disk clicks every few seconds.
After reading some of the other posts, i disabled the Advanced Power Management
(hdparm -B255 /dev/sda). It has still not eliminated the clicks completely.

When I boot into Vista, I do not get the same problem.

Any suggestions on how this can be eliminated.

---

### Post by Z_o-s-o on 2008-01-10
Ive got a DV6125 with a 120 gig HDD.

Doing the hdparm 255 thing totally fixed the clicks / load cycle accumulation for me.  I'm assuming you made a script and placed it into the acpi folders?

You can also try changing 255 to 254 and so on. Some people have better success at different numbers.  The lower the number, the more active the power management.

---

### Post by jespdj on 2008-01-10
Your are suffering from the famous load cycle problem.

See the central thread about the issue: [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

