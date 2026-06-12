---
title: "memtest killed, what does it mean?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by shelbydz on 2006-06-25
Hey guys, I'm trying to track down my crashing problem with World or Warcraft. When I run 
memtest mem 1G -l 
I get:
Current limits:
  RLIMIT_RSS  0xffffffff
  RLIMIT_VMEM 0xffffffff
Raising limits...
Allocated 536870912 bytes...trying mlock...Killed
wtf does this mean? does this mean my memory is dead? or is my syntax ,wrong?

---

### Post by .t. on 2006-06-25
Well, it happens for me, but eventually it finds an allocation that works and continues. Do you have less than 1G of memory?

---

### Post by shelbydz on 2006-06-25
well. I had 1g in there, running memtest froze the computer to the point where I had to reboot. It would get just as far, but would freeze. 

I removed my 1 512mb stick, reran memtest w/ 
mem 512M and it didn't freeze, but gave me the above message.

---

### Post by .t. on 2006-06-25
Try with only the other stick - may be that it's dodgy.

---

### Post by shelbydz on 2006-06-26
okay, pulled the two 256mb chips out and put in the one 512mb chip in. 
Re-ran memtest mem 512M -l 
and same results
Current limits:
RLIMIT_RSS 0xffffffff
RLIMIT_VMEM 0xffffffff
Raising limits...
Allocated 536870912 bytes...trying mlock...Killed

wtf is going on? is it possible that all three of my RAM chips are dead?

am I running the program wrong? Is there a different program to try?

---

### Post by kylemallory on 2008-03-19
I am having this exact same problem, but on a server with 4GB of RAM.

The problem initially appeared when I would copy large amounts of data between volumes (copying video footage from USB drives to an internal raid, or from another computer using SCP to the internal raid).  After a few minutes of copying, my cache memory usage would skyrocket and slowly the machine would deteriorate until the point it would crash.  Initially windows would be unresponsive, but still active, then I couldn't use any input (keyboard/mouse), but windows would still paint/update.  Eventually everything hangs.  After a little more time, the machine would reboot.

I ran memtest w/ 4 gig, It did the exact same thing as when copying the files.  So, ran memtest86+.   memtest86+ only seems to be able to test 2GB at a time, so I removed half of my ram, and ran memtest86+ again.  No errors.  I installed the other 2GB, no errors.

Back in Ubuntu, I ran 'sudo memtest all', I get the following:

```
kmallory@pandora:~$ sudo memtest all
[sudo] password for kmallory:
memtest v. 2.93.1
(C) 2000 Charles Cazabon <memtest@discworld.dyndns.org>
Original v.1 (C) 1999 Simon Kirby <sim@stormix.com> <sim@neato.org>

Current limits:
  RLIMIT_RSS  0xffffffff
  RLIMIT_VMEM 0x1f400000
Raising limits...
Unable to malloc 4293918720 bytes.
Unable to malloc 4289724416 bytes.
Unable to malloc 4285530112 bytes.
Unable to malloc 4281335808 bytes.
Unable to malloc 4277141504 bytes.
....
....
Unable to malloc 2964324352 bytes.
Unable to malloc 2960130048 bytes.
Unable to malloc 2955935744 bytes.
Unable to malloc 2951741440 bytes.
Allocated 2947547136 bytes...trying mlock...Killed
kmallory@pandora:~$

```

I get the same result with the other 2GB.  If I install all 4gb, it gets to "Trying mlock...", and crashes.

---

### Post by kylemallory on 2008-03-19
Just thought I'd post a little follow-up.

I'm running Dual, Intel 3.4GHz Xeon Dual-Core processors on an Intel SE7520AF2 Motherboard, with a 3Ware 9000 series RAID controller, and an nVIDIA GeForce 8600GTS.  I am running Ubuntu Studio.

I found a couple of topics on other threads that hinted at issues with mlock and SMP, but nothing concrete.  Anyone one else seeing this with SMP boards?

---

