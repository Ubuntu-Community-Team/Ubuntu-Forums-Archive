---
title: "686 Kernel Help"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by QuickNinja on 2009-04-07
Hey everyone I'm trying to install the linux kernel 686 for my comp because I believe it's the best kernel for my Celeron D processor.

I tried using the instructions in the terminal: sudo apt-get install linux-686 or using: sudo apt-get install linux-restricted-kernel-686 but both commands leave me with "Couldn't find package (Blank)."

What's the command for installing the 686 kernel or how should I be doing it?

---

### Post by mcduck on 2009-04-07
There is no such kernel in Ubuntu.

(There used to be specific 386, 686 and k7 kernels but these days the generic kernel handles them all and automatically uses correct optimizations depending on what CPU you have).

If you really, really feel that the generic kernel isn't good enough you can of course compile your own kernel. But I doubt you'd get any noticeable increase in performance.

---

