---
title: "Performance problems"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by markelhas on 2007-08-29
Hi,
I've a Asus M3N with a Pentium M Centrino 1.6Mghz, 1gb mem, 60gb hd.
Trying to install ubuntu 7.04, but the performance is to low. Every time that a try to execute a simple task (open a terminal) the cpu jumps to 100% a takes to long to open it.
The booting process takes +- 12 - 15 min.
I don't have any other os in my laptop. Is this distro to much for my machine or i'm missing something?

---

### Post by merlinus on 2007-08-29
Did you actually install ubuntu, or are you running it from the live cd?

If the latter, that is probably most of your problem.

-merlin

---

### Post by markelhas on 2007-08-29
Nop, i've installed the ubuntu to my hd

---

### Post by markelhas on 2007-08-29
very very crazy problem.
I've removed a 512 sim and the os is working just fine. I've made the test mem and it was ok.
I've put a different 512 sim a the same slow os problem. I've put a 256 and os working just fine.

Is there any mem issues/limitation? Can i solve this problem?

---

### Post by slouck on 2007-08-29
markelhas this sounds it is more a function of the hardware than the OS based on what you are subscribing.  Do other operating systems (windows) have the same issue?  Have you checked for a BIOS update?

---

### Post by markelhas on 2007-08-29
i've the last bios update. Using windows xp no mem problems. Can't solve this situation. ](*,)](*,)](*,)](*,)](*,)

---

### Post by markelhas on 2007-09-04
After some net search i've found this

[B]The mysterious 880 MB limit on x86

By default, the Linux kernel runs in and manages only low memory. This makes managing the page tables slightly easier, which in turn makes memory accesses slightly faster. The downside is that it can't use all of the memory once the amount of total RAM reaches the neighborhood of 880 MB. This has historically not been a problem, especially for desktop machines.

To be able to use all the RAM on an 1GB machine or better, the kernel needs to be recompiled. Go into 'make menuconfig' (or whichever config is preferred) and set the following option:
Linux Kernel Configuration: Large amounts of memory

Processor Type and Features ---->
High Memory Support ----> 
(*) 4GB

This applies both to 2.4 and 2.6 kernels. Turning on high memory support theoretically slows down accesses slightly, but according to Joseph_sys and log, there is no practical difference.

Also, the ck-sources kernel has a patch for 1gb high memory support. [/B]

Is this a problem in ubuntu distro also?
Can i check if the kernel that i have witch parameters where used?

---

### Post by markelhas on 2007-09-05
So just for remark i've solved this problem adding to the boot line mem=1000M
:)

---

