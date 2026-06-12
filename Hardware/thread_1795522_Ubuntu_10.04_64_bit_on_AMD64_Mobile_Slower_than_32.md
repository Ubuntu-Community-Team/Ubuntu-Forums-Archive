---
title: "Ubuntu 10.04 64 bit on AMD64 Mobile Slower than 32 bit?"
date: 2011-07-02
forum: Hardware
---

### Post by Trevayne10 on 2011-07-02
I have a Compaq CQ62 laptop with a 2.8 GHz AMD64 Phenom II X2 dual core CPU.

I'm running Ubuntu 10.04.2 LTS 64 bit. Best release of Ubuntu ever, imho.

However, I've noted a pattern with most AMD64 cpu's on Ubuntu 10.X and 11.X 64 bit, with benchmarks like Geekbench:

The 32 bit integer performance on these CPUs is much lower in Geekbench than on 64 bit Ubuntu, and their 64 bit floating point performance is much FASTER than on 32 bit. It's kind of disappointing.

I'd also expect higher all-around scores from the 64 bit Ubuntu.  I don't. Instead, they're about 12% lower than 32 bit Ubuntu.

Maybe it has something to do with the way AMD64 cpu's handle ia32 libs?

Intel CPUs, from Core 2 Duos to i5's and i7's all seem to show a 64-bit 15 - 20% improvement over 32-bit, with GeekBench.

Here is a screen scrape of my system running Geekbench on Ubuntu, running 32- and 64 bit versions of the benchmark:

64-bit Geekbench running on Ubuntu 10.04.2 64-bit on the left side, 32-bit Geekbench running on Ubuntu 10.04.2 64-bit on the right.

[http://browse.geekbench.ca/geekbench2/compare/414230/431625](http://browse.geekbench.ca/geekbench2/compare/414230/431625)

I would figure that the 64 bit results would be somewhere around 4,250 to ~4,300.

It's too bad Ubuntu can't roll a single, fast 64-bit kernel for AMD64 cpu's that takes the fast FPU performance from the 32-bit kernel, and the fast integer performance from the 64-bit kernel.

One more item: I explicitly set out to install the AMD64 iso / kernel.

When I do a # uname -a , why do I see "generic" for the kernel, instead of AMD64?

---

### Post by wolfen69 on 2011-07-02
> **Trevayne10 said:**
> 
It's too bad Ubuntu can't roll a single, fast 64-bit kernel for AMD64 cpu's that takes the fast FPU performance from the 32-bit kernel, and the fast integer performance from the 64-bit kernel.



I wouldn't be so quick to blame ubuntu for your kernel issues. I've done a few 64bit installs and they are pretty quick. 

Anyway, if you are doing *uname -a* and it's coming back as a generic kernel, then you are **not** using the 64bit version of ubuntu. If you have multiple iso's on your pc, then you could have burned the wrong one. I've done it myself.

---

### Post by Trevayne10 on 2011-07-02
> **wolfen69 said:**
> I wouldn't be so quick to blame ubuntu for your kernel issues. I've done a few 64bit installs and they are pretty quick. 

Anyway, if you are doing *uname -a* and it's coming back as a generic kernel, then you are **not** using the 64bit version of ubuntu. If you have multiple iso's on your pc, then you could have burned the wrong one. I've done it myself.

Thanks for your quick reply, wolfen69 -


Oh, uname -a does indeed show the kernel as 64-bit alright, but "generic". The .iso I downloaded & burned said "AMD64" right on the file name.  Very weird.

uname shows 64 bit (and SMP as well, btw).

,";^,

---

