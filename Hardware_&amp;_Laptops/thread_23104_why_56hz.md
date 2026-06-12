---
title: "why 56hz?"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-03-31
i have a laptop with an lcd display which has a native resolution of 1400x1050. as far as i know, it only supports a refresh rate of 60hz at this resolution and windows also detects and runs it at that rate. however, ubuntu (and actually all other distros i've tried) will insist on 56hz. 

i know this can be tweaked by entering a modeline in xorg.conf, but i don't know if i should do it. on one hand, i have the display looking quite right, without any flicker that is the normal symptom of an incorrect/insufficient refresh rate, but i also have problems with font smoothing and anti-aliasing, and no matter what i do i can't get them quite as smooth as in other operating systems, and i'm wondering if that difference of 4hz might be a factor...

-m.

---

### Post by soul_rebel on 2005-03-31
the video card tells X what it can do, you can see that in /var/log/xorg.0.log or similar. Refresh doen't really matter much on a lcd. Bye

---

### Post by 23meg on 2005-04-04
why does it not matter much?

---

### Post by soul_rebel on 2005-04-05
beacuse of lcd technology, ... my english is not good enough to explain that, but on lcd refresh has less visual impact than on ctr.

Anyway you should squeeze everything you can.
Bye

---

