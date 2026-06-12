---
title: "HP System BIOS 786B2 v.2.04"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by dforstmann on 2008-12-05
I have an hp compaq d530 SFF with HP System BIOS 786B2 v.2.04.  I cannot get Ubuntu 8.04 or 8.1 to fully load.  The kernel loads but it goes no further.  I suspect the problem is in the BIOS of this system as I have loaded 8.04 and 8.10 on several other machines without problem.  Does anyone have any ideas here?  It is a pretty much stock business desktop that I got with a wiped drive.  I checked the memory and the ISO images & all was OK.

---

### Post by linux_tech on 2008-12-05
Will the live cd run?
Was another OS on this pc recently?
I checked the ubuntu hcl and the d530 is listed as compatible.  
Have you you tryed loading a different kernal?
Is a bios update an option?
what is output of ```
 dmesg 
```(attach) 
```
fdisk -l
```
```
sudo dmidecode
```(attach file)

---

### Post by dforstmann on 2008-12-09
The live CD will not run with either version that I've tried.  In 8.04 it freezes at the splash screen and on 8.10, right after the kernel loads.  This machine came from my company where it was running XP until it was replaced with newer hardware last month.  The drive has been wiped and there is no OS installed currently.

---

### Post by Mark Phelps on 2008-12-10
How much memory does the HP have? Is it 256MB or less?  If so, try booting from the alternate CD.  It's text-based and uses a lot less memory.

---

### Post by dforstmann on 2008-12-10
It has 2GB of RAM.  I was able to run Damn Small Linux on it but this isn't really a long term solution.  I just wanted to see if it would run.  Oddly, the computer doesn't lock at exactly the same place every time.  I wonder if I have a CPU cooling problem.  Could this do it?  In its prior life the computer ran 24/7.  It never had to boot.  I did clean out the heat sink, which had a lot of dust in it.

---

