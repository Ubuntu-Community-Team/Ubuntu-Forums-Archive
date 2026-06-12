---
title: "How would you configure an E1505n?"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by dara on 2007-05-25
I may end up getting a D830 instead, but I'm going to consider an E1505 anyway.  For anyone else thinking of getting one, how would they configure it?  I know I'd get the densest screen (which unfortunately isn't WUXGA) and probably a 120 GB drive and the DVD writer.  I'm less clear on how to choose processor or memory though.  For processors, speed, cache size, FSB speed all vary:

Core™ 2 Duo processor T7200 (4MB Cache/2.00GHz/667MHz FSB)
Core™ 2 Duo processor T5600 (2MB Cache/1.83GHz/667MHz FSB)
Core™ 2 Duo processor T5300 (2MB Cache/1.73GHz/533MHz FSB)
Core™ processor DUO processor T2350 2MB Cache/1.86GHz
Pentium® dual-core proc T2080(1MB Cache/1.73GHz/533MHz FSB)

I figured I'd get the T5600 but no real logic there.

I've never used 2 GB on a Linux box, so I don't know how much better that makes things, but the memory options are:

512MB Shared Dual Channel DDR2 SDRAM at 533MHz, 2 DIMM
1GB Shared Dual Channel DDR2 SDRAM at 533MHz, 2 Dimm
1GB DDR2 SDRAM at 667MHZ, 2 DIMM
2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 DIMM
2GB DDR2 SDRAM at 667MHZ, 2 DIMM

I'd get at least 1 GB, but I don't know how to choose between the two types.

I won't get a System 76 machine, because I'm unhappy with the maximum resolution on the screen.  I'm not aware of too many other Linux preloaded solutions with at least a 1680 x 1050 screen so if I want to support a company that is going to make Linux available, this is my main chance so far.

Dara

---

### Post by mobasher_helmy on 2007-05-25
hey mate !

about your choice, I have a Dell laptop just as the one you are about to purchase.
It has a 2.0 GHz 4MB cache
120 GB HD
ATI mobility Radeon x1400 
1GB memory (does not matter if you choose 2GB, but keep in mind that you would only use about 300 MB of memory on average with Ubuntu)

it works very well, everything works just fine. there are problems with me with the suspend (standby) but this is my only problem.

Anyway,  Dell is already selling 1505n with ubuntu 7.04 pre-installed....good news, right ?

---

### Post by magicfab on 2007-05-25
In my experience Ubuntu (and Linux in general) just uses less memory than Windows.

A few scenarios where I see you may need more than 512MB:
- Virtualization
- Development
- Gaming or other graphic intrensive apps in a system with shared-mem video
- Audio / video editiing

---

### Post by dara on 2007-05-25
I see they have updated the video card option and now have two choices:

Intel® Graphics Media Accelerator 950 
256MB NVIDIA® GeForce® Go 7300 TurboCache™

I'm inclined to go for the better performance of NVIDIA but I appreciate Intel's effort to be more open.  At a minimum I would use this laptop for displaying HDTV.  The only other graphics intensive thing I would do is Google Earth most likely.  Perhaps I can get by with an Intel 2-d Xserver.

Any other opinions on this choice?

Dara

---

### Post by dara on 2007-05-26
> **magicfab said:**
> In my experience Ubuntu (and Linux in general) just uses less memory than Windows.

A few scenarios where I see you may need more than 512MB:
- Virtualization
...

My guess at choosing 1 GB of RAM (most likely the more expensive of the two options) hinges on the fact that Linux is better than Windows with RAM - otherwise I wouldn't hesitate at getting 2 GB (which is more or less required for Vista as I understand).  

My guess is that 1 GB is going to significantly improve on the default 512 MB for using Ubuntu to: a) display very high quality interpolated HDTV and b) run MATLAB simulations that sometimes need a bit over 1 GB just themselves to run well.

Dara

---

