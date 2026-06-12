---
title: "Beating Dead Black Screen"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Billxyzzy on 2008-12-19
I have gone through the previous posts about the  black screen problem.
I summarize the results as: smoke, mirrors, waving arms, and W. A. G.
I have two systems both dual boot Win XP and Ibex 64 bit.
The first system has been running with no problems for a while now.
System 1.  Elitegroup C51GM-M motherboard, ATI display, installed the
ATI/AMD proprietary FGLRX graphic driver, tested by the Ubkuntu developers.
4Gb of ram.

System 2. Elitegroup AMD690GM-M2 motherboard, ATI display,  installed the
ATI/AMD proprietary FGLRX graphic driver, tested by the Ubkuntu developers.
2 Gb or ram.  Has been running well.  Yesterday I upgraded to 4 Gb or ram.
S**t hit the fan.  Now have the famous black screen.

I have gone thru the menu.lst adding iommu=noaperture, iommu=soft,
nommu, noapm  in various combinations.  No changes to problem.
I went into root and removed compiz and compiz-core and their dependencies, no change to the problem.

Went into the bios and Changed memory hole enabled
result: PANIC: early exception 0c rip 10:ffffffff8022d601 error 0 cr2
ffffffffff5fc0f0
Changed memory hole back to disabled,  no more panic.

I would like to know if there is a suggested way to set break points
in the boot loader and single step?  The only way to see the problem
is to see what instruction is failing.

Using recovery mode:
    options:
             resume
             clean
             dpkg
             fsck
             root
             xfix

Choosing dpkg, fsck, and resume in that order allows the system to boot
with three stops to battery state and finally to default minimal 
graphics mode.

I have no clue as to why this works.
To solve this problem the offending instruction must be found.

---

