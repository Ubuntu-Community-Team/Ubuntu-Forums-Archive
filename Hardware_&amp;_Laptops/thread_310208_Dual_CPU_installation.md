---
title: "Dual CPU installation"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by Ndyanabo on 2006-11-30
I'm setting up an old (2001) Dell workstation I found in an attic with Edgy.

The motherboard has a spot for a second CPU, which arrived today from ebay. Same Intel Xeon 1.7 GHz as the first CPU. I put it in, hit the power button, and NOTHING happened, as if it were unplugged.:(  

Do I assume I bought a faulty CPU?

Any suggestions? Would it be a bad idea to take out the original CPU and try the new one in it's place?

I'm a total newbie at both Linux and hardware.

thanks.

---

### Post by partsdale on 2006-11-30
maybe a BIOS setting to be adjusted?

I'm not any kind of expert, that was just the first thing I wondered about.

---

### Post by Mike'sHardLinux on 2006-12-01
> **Ndyanabo said:**
> I'm setting up an old (2001) Dell workstation I found in an attic with Edgy.

The motherboard has a spot for a second CPU, which arrived today from ebay. Same Intel Xeon 1.7 GHz as the first CPU. I put it in, hit the power button, and NOTHING happened, as if it were unplugged.:(  

Do I assume I bought a faulty CPU?

Any suggestions? Would it be a bad idea to take out the original CPU and try the new one in it's place?

I'm a total newbie at both Linux and hardware.

thanks.

Switching the cpu's as you suggest is not a bad idea as long as you know what you are doing. It is a common step in troubleshooting.

One thing about dual processors, is that you can't just get any processor, even if it's the same type(Xeon) and speed(1.7GHz). In the past (and I assume they still do), cpu's had a spec called "stepping", and both cpu's had to have the same stepping, or at least compatible steppings ([http://www.intel.com/support/processors/sb/CS-007878.htm]("http://www.intel.com/support/processors/sb/CS-007878.htm")).
But I don't know if/how that applies to Pentium IV class processors. You might want to do some research on that.

---

### Post by zgornel on 2006-12-01
Does the mobo start with the old CPU (new one removed)? It might be a power supply problem, short circuit somewhere or something badly damaged.

---

### Post by the bioengineer on 2007-08-16
I too have the same issue, only with two Pentium 3's.  When I previously had Win2000 installed everything worked fine.  When trying to install Ubuntu from disk I found that I had to actually remove one CPU for it to even boot-up.

I am an avid builder of machines, and am familiar with "tweaking" the BIOS.  Mike'sHardLinux is correct, you need not only to insure that the stepping is in synch for such an outdated mobo, but that the core voltage is the same for both.  Not all Xeon's are the same.  I found that my P-3's were not the* exact* same voltage and so had to find another (when I was installing Win2000).

At the time I am writing this I am running from disk, with one CPU pulled out.  I do not know what the exact problem is, but plan on installing with one CPU and then trying to pop the other in and see if she boots up.  Will post results here, wish me luck!

Ubuntu edition - Ubuntu Ultimate V 1.4
mobo - ?
CPU(s) - P-III 1Gb 933/256/133/1.7V

---

