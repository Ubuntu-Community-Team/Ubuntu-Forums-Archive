---
title: "Asus notebook not working after RAM upgrade"
date: 2009-01-18
forum: Hardware
---

### Post by nlz on 2009-01-18
I just upgraded my girlfriends S96J with 1 GB RAM.

Previously, there was only 1 GB in there, so I got the same module and placed it one the other side. When I try to boot, it's starting up (I hear the CD-rom, HD and see the lights, but then i does nothing. All the time there is a black screen.

I tried to change the modules, and that worked. So the RAM modules are OK. 

So it seems like a BIOS problem, but when I looked in the BIOS and on the net, i couldn't find a setting which is should set before I add the RAM.

Any ideas? The system supports 2 GB RAM btw.

---

### Post by nlz on 2009-01-18
Maybe this has something to do with it:


Solution: Memory compatibility issue. Change SODIMM (from a different memory vendor).

>     * Issue: ASmobile S96J (AS96J945PM1) and S96F (AS96F945GM1) systems show the same GUID. These notebooks are supposed to have a unique GUID for each individual SKU. This issue impacts RIS installations of the OS in that the network will be confused as to which device is which if they all have this same GUID.

Solution: Update BIOS to revision v1001 or newer for S96J, and update BIOS to revision v901 or newer for S96F.

from [http://www.asimobile.com/notebook_vbi_support.htm#S96J](http://www.asimobile.com/notebook_vbi_support.htm#S96J)

But then my other RAM module shouldn't work anyhow, isn't it?

---

### Post by nlz on 2009-01-18
hmmmm it seems it has already the newest BIOS: version 0901..

---

