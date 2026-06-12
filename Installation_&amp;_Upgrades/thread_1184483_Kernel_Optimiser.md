---
title: "Kernel Optimiser"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by madtom1999 on 2009-06-11
Does anyone know of a kernel config optimiser that can look at your system and modify the config file for kernel compilation so that there is nothing unneeded in it?
It would be nice to run after each new kernel comes out so that I dont have ram taken by drivers for things I cant afford or sub-optimal configurations for my processor(s) etc.

---

### Post by kerry_s on 2009-06-11
the debian expert install mode has a targeted option.
but just to let you know if you don't have the device, then nothing is loaded so no ram is wasted, the only difference is kernel size. everything is auto detected and loaded at boot, the other drivers just sit on your hard drive.

---

### Post by madtom1999 on 2009-06-15
Presumably if something can be auto-detected at boot time then it can also be detected at compile configure time so no unnecessary tests are run at boot time.
Also cpu configuration etc - I still have a 386 that runs - and anything that gets it up faster would help!
I must confess I havent compiled a kernel for several years but then there were many options for smaller/faster and from memory it took forever to select options when most of these could have been automatically selected from the machine in question.
While I agree completely that the first install on a new kernel should be totally 'inclusive' once thats done I'd like it to be a fallback option in the very slim chance I need to modify my hardware - or some fails.

---

### Post by kerry_s on 2009-06-15
hmm, that use to be the case, i don't think so now a days.
it's more the software end that bogs down these days.
mines a p3 450mhz 256mb ram.
to get the best results you simply install a base & build up from there.
debian & arch work really good.
i'm using debian testing at the moment.

---

### Post by Gen2ly on 2009-06-15
The kernel is very well optimized.  Even having options there that you don't need (e.g. drivers...) are either not loaded or take up a such a small amount of RAM they aren't worth bothering with.  Go ahead an make a custom one if you wish.  I've done the perfect kernel config for mediocre-results, it is fun to tinker with though.

---

