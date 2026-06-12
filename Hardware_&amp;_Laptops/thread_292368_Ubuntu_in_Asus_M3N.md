---
title: "Ubuntu in Asus M3N"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by markelhas on 2006-11-03
Is it possible to run ubuntu or kubuntu in this laptop!? Cause i've  none of them works fine in mine.

I've tried prev release of ubuntu and got a very slow os runnig :(, in live cd and installed on hd.

Also download kubuntu and ubuntu 6.10 running live cd works just fine, but when installed slow os again, Just impossible to use.

Can anyone please help this time solving this problem?!

---

### Post by John.Michael.Kane on 2006-11-03
What do you mean slow?

That machine has mobile cpu in it which has speed step. this slows the cpu down when your not doing anything hardware intensive. As far as support the machine should be fully supported from looking at the specs.

Your going to have be more detailed in explaining your issues other then post it runs slow.

---

### Post by markelhas on 2007-09-05
very very crazy problem.
I've removed a 512 sim and the os is working just fine. I've made the test mem and it was ok.
I've put a different 512 sim a the same slow os problem. I've put a 256 and os working just fine.

Is there any mem issues/limitation? Can i solve this problem?

After some net search i've found this

The mysterious 880 MB limit on x86

By default, the Linux kernel runs in and manages only low memory. This makes managing the page tables slightly easier, which in turn makes memory accesses slightly faster. The downside is that it can't use all of the memory once the amount of total RAM reaches the neighborhood of 880 MB. This has historically not been a problem, especially for desktop machines.

To be able to use all the RAM on an 1GB machine or better, the kernel needs to be recompiled. Go into 'make menuconfig' (or whichever config is preferred) and set the following option:
Linux Kernel Configuration: Large amounts of memory

Processor Type and Features ---->
High Memory Support ---->
(*) 4GB

This applies both to 2.4 and 2.6 kernels. Turning on high memory support theoretically slows down accesses slightly, but according to Joseph_sys and log, there is no practical difference.

Also, the ck-sources kernel has a patch for 1gb high memory support.

Is this a problem in ubuntu distro also?

---

### Post by markelhas on 2007-09-05
So just for remark i've solved this problem adding to the boot line mem=1000M

---

