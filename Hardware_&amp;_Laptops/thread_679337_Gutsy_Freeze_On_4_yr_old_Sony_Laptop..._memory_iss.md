---
title: "Gutsy Freeze On 4 yr old Sony Laptop... memory issue?"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by H-Radical on 2008-01-26
Hi all,

I have recently run into a pretty bad problem with my Sony VAIO PCG-GRT100 laptop running Gutsy Gibbon. I have been using this machine everyday with the exact same configuration with gutsy since the release of 7.10. Since about 10 days ago, I've been getting random freezes on average about once every two days, and its got worse with time. These are "total" freezes... I just have to power down. Even that funny key combo (it was some acronym that I forgot) that's supposed to always properly reboot the machine doesn't work.
From what I've read online and others who've had a similar issue, it seems the main culprit must be my RAM. But I performed a memtest with no errors reported. I've tried to look at the logs but I don't quite know where to look.
I was wondering if anyone knows what checks I can perform to rule out other possibilities before I take the hardware apart to test the memory. (Never opened up a laptop before).


Cheers,
H-radical

---

### Post by HereInOz on 2008-01-26
4 years old?  It could also be a hard disk going off.  Unfotunately, the only really reliable test is to replace (test by substitution).  

I recently had a Toshiba laptop with 2 x 256 modules of RAM, and it was intermittently freezing.  I removed one module - still freezing.  I replaced that module and removed the other one - still freezing.  Tested the memory with Memtest - fine.  Replaced both modules with a single 512MB module. Problem solved.  

Another machine with the same problem.  Nothing I did with the RAM would change it.  Reinstalled the OS, no change.  Replaced the HDD and re-installed. Now running sweetly.

It will either be RAM or HDD as a guess, but which it is will probably only be determined by replacement.

Sorry I can't offer much more enlightenment.

---

### Post by H-Radical on 2008-01-30
Thanks for the help.

 I guess I will be taking it apart soon.

---

### Post by koresko on 2008-02-11
You might also try running the machine off a Dapper LiveCD for a while.  My laptop freezes typically once every couple of hours using the default Gutsy kernel, but it is rock stable with an older kernel (same OS, just different kernel) - in my case the Feisty kernel is stable.

It could still be a hardware problem, but one which is somehow dependent on the kernel.  There are a lot of people having these random freezes on very different hardware, though.

> **HereInOz said:**
> 4 years old?  It could also be a hard disk going off.  Unfotunately, the only really reliable test is to replace (test by substitution).  

I recently had a Toshiba laptop with 2 x 256 modules of RAM, and it was intermittently freezing.  I removed one module - still freezing.  I replaced that module and removed the other one - still freezing.  Tested the memory with Memtest - fine.  Replaced both modules with a single 512MB module. Problem solved.  

Another machine with the same problem.  Nothing I did with the RAM would change it.  Reinstalled the OS, no change.  Replaced the HDD and re-installed. Now running sweetly.

It will either be RAM or HDD as a guess, but which it is will probably only be determined by replacement.

Sorry I can't offer much more enlightenment.

---

### Post by Yellow Pasque on 2008-02-11
I want to second the suggestion of using a LiveCD or an older kernel for a bit. Make sure the problem is hardware related before you spend any money on new hardware. Throwing hardware at a problem that you haven't diagnosed is usually a costly and foolish expedition.

---

