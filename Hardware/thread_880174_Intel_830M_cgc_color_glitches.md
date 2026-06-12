---
title: "Intel 830M cgc color glitches"
date: 2008-08-04
forum: Hardware
---

### Post by immerohnegott on 2008-08-04
Ok. I've been fiddling with this business off and on since I upgraded to Hardy. The affected machine is an elderly Dell C400 running an Intel 830M CGC. Here's the rundown - when I use the older "i810" driver, everything looks nice, but the thing locks up all over the place (I've tried several different kernels with it, messed with xorg.conf enough to melt part of my cerebral cortex). If I use the newer "intel" driver, it runs fine (no lockups), but the color is poorly rendered - setting it to 24 bit leaves me with hideous, hideous gradients, among other things.

SO, the question is, how do I get the lockup-free "intel" driver to correctly render in true-color?
I've tried fanagling xorg.conf...many, many times, but it just doesn't want to play nice.
Also tried setting it up via displayconfig-gtk, but that didn't do much good either.

---

### Post by immerohnegott on 2008-08-23
Bump?

---

### Post by didjital1984 on 2008-12-06
Were you ever able to solve this issue? I am having the same problem.

---

