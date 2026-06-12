---
title: "Instability k7 kernel on sempron 2400+"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by warjowuch on 2006-07-11
Hi there,

I run ubuntu dapper 386, and on regular bases I try the k7 kernel, for this should run better on my sempron 2400+ processor.
But this crashes quite often, in contrary (?) to the 386 one. IO don't understand why.
My memory is ok in memorytest. No (much less) crashes occur on 386 kernel.

Anyone having the same problem? Anyone knows what the problem is?

My hardwareconfig:
sempron thoroughbred-B (Little overclocked from 166 FSB to 175)
MSI KT6-LSR
512 (2x 256) MB Twinmos pc3200, CAS 2, instead of 2,5. Works ok on 386 also, this shouldn't matter in kernelswitching...

Thanks!

---

### Post by tseliot on 2006-07-11
> **warjowuch said:**
> Hi there,

I run ubuntu dapper 386, and on regular bases I try the k7 kernel, for this should run better on my sempron 2400+ processor.
But this crashes quite often, in contrary (?) to the 386 one. IO don't understand why.
What do you mean by "crashes"? Does it freeze? Please describe your problem.

> **warjowuch said:**
> No (much less) crashes occur on 386 kernel.
If it crashes also with kernel i386 there might be a problem of compatibility with your motherboard.

You can try compiling a new kernel (the latest is 2.6.17.4) so as to see if it solves the problem.

You can follow this guide:
[http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)

Or my guide (follow the part about compiling vanilla kernels):
[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

### Post by warjowuch on 2006-07-11
With crashes I mean, I can only get rid of it by pressing the reset-button, so yeah, it freezes.

It almost never crashes on the 386 kernel, sometimes but rarely, but no complete freezes.

Thanks for your advices in kernelcompiling, but I'd rather wait a little while...

---

### Post by tseliot on 2006-07-11
> **warjowuch said:**
> Thanks for your advices in kernelcompiling, but I'd rather wait a little while...
It's not as scary as it sounds. My guide is aimed at newbies.

---

### Post by warjowuch on 2006-07-14
Ok, I will take a look at it in a while, thanks

---

### Post by handy on 2006-07-15
**Hi tseliott**, I have a question for you if you don't mind?

Is there a noticeable difference in performance between the i386 & the K7 kernels?

I have run my 64bit athlon on both 64bit (initially) & then 32bit i386, & really I can't notice any speed difference, in my use of the computer.

Is it a law of diminishing returns thing, where you go to a whole lot of trouble to get very little if anything out of it?

Please don't read me wrong, no personal attack or anything remotely like that here.  I respect your knowledge & experience, that is why I am asking you! :KS

---

