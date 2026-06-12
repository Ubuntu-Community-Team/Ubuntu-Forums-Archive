---
title: "Intermittent BSOD"
date: 2014-02-07
forum: Hardware
---

### Post by mmoller on 2014-02-07
I've recently put together a desktop PC like I've done many times in the past. Pretty standard components: Gigabyte motherboard, Seagate HD, 16GB Kingston RAM, i5 CPU, 450W Thermaltake PSU, NVidia GPU. All reliable, trusted components.
But this machine is behaving oddly. First individual apps would start segfaulting for no reason. Nautilus, Firefox, even Solitaire. Restarting the apps would work sometimes for days, sometimes for only a minute or two. Every few days the machine would throw a kernel panic and black screen of death. (It is a server which runs 24/7).
My question is this: Is this a hardware problem, and if so, which component is the most likely culprit? Is there some software that could hammer the hardware and flush out the problem - assuming it is hardware related?

---

### Post by Gone fishing on 2014-02-07
Hardware - I'd check RAM by booting on a live CD and using memtest. Overheating? is the heatsink sitting nicely on the processor?

---

### Post by mmoller on 2014-02-07
Thanks for the advice. It turned out one DDR3 module in a matched set of two was faulty. Go figure.

---

