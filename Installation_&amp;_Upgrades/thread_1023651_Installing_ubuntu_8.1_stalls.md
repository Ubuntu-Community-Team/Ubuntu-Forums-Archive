---
title: "Installing ubuntu 8.1 stalls"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by alastair roy on 2008-12-28
I am the newest of the new to Linux, trying to load Ubuntu 8.1 on to Compaq Presario currently loaded with Win Millennium Edition.  Downloaded cd is ok and checked, Ubuntu initial screen appears but after working for some minutes it all stops.  On checking 'other options'  (F6) I have removed  silent splash, and am trying alternatives recommended in [https://help.ubuntu.com/community/BootParameters?action](https://help.ubuntu.com/community/BootParameters?action).
But it always stops at line no [91.647564], apparently a sign-off line by the developer.  When it stops at this point cd drive remains active for some minutes but then stops and system sleeps. Line no quoted above is preceded by sequences of timeout errors, warnings that failed to IDENTIFY, revalidation failed, 'link is slow to respond - be patient'.

I am probably getting something absolutely basic wrong!  I'd be v grateful for any advice.  I have assumed I do not need to format partition C (I want to keep exiting partitions to give me a route back to original installation backed up on partition D)

---

### Post by skullmunky on 2008-12-28
The first thing I usually try is burning another copy of the installer CD, using high-quality media and on the slowest speed my burner will allow (like, 8x instead of 52x).  Sometimes that will really make a difference, particularly on older machines.  A Presario with Windows ME ... if it still has the original CD drive it could be a bit finicky.  Also of course make sure the specs are good enough to actually run ubuntu (enough RAM and hard drive space).  I tried for a while to put ubuntu onto a compaq of similar vintage and had to switch to Damn Small Linux, since it only had like 128 MB of memory in it :)

---

### Post by alastair roy on 2008-12-30
Thanks skullmonkey.  I'm pretty sure it's not the cd - I have made two copies, after checking the iso file is ok, both burned at 4x.  The cd drive is reasonable quality sony rewrite drive, hardly used. I have tested it on other things inc Compaq's diagnostic disc with no adverse results.I doubt if the hard drive is below its _original _spec because the pc has hardly been used.  But maybe current ubuntu demands a better drive.  Memory on the pc (also tested) is 256mb which according to ubuntu specs shd be ok.

Any views on whether the existing state of the hard drive cd be relevant?  It is a 20gig drive partitioned about 18:2, the 2 containing Compaq's restore routines which my daughter (owner of the pc!) does not want to lose.  I am tempted to see if I can get a cheap replacement drive that I can install, format and leave unpartitioned before attempting to load ubuntu.  Any views on that?

---

### Post by oldos2er on 2008-12-30
The LiveCD requires a minimum 384MB of RAM to run. You might want to try the alternate CD.

---

### Post by alastair roy on 2008-12-31
Ann

Many thanks.  Will follow yr advice  & hope it works (It's a fairly crucial limitation which shd perhaps be more fully advertised given Linux's claims to low demand for memory & storage.  But having started with a BBC B machine and 32kb of memory I am v conservative.  A US citizen might not know what a BBC machine is, but they are still around and good training for BASIC programming to enable children to understand what lies behind complex applications.)

---

### Post by oldos2er on 2008-12-31
"given Linux's claims to low demand for memory & storage."

 Not all distros are optimized for older hardware and/or low end machines. You might want to visit [www.distrowatch.com](www.distrowatch.com) to find a more suitable distro. Good luck.

---

