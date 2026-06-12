---
title: "Strange micro-freezes when I don't move the mouse"
date: 2009-03-30
forum: Hardware
---

### Post by outofsync on 2009-03-30
Hi,

I'm using 8.10 (x64) on an Acer 6935G, and I'm noticing that the CPU seems to sleep for very small periods (fraction of a second) when I'm not moving the mouse.

A simple way to notice it is with the blinking cursor at the terminal: If I'm moving the mouse, the blinking rate is uniform. If I don't move the mouse, the blinking rate is non-uniform.

It can also be noticed with the system monitor, specially at the CPU graphs, where you can notice that the graphs don't scroll at constant speed unless I move the mouse.

I'm not sure if this happens all the time, but it's happening in this same moment.

I remember this same issue happened with some models of SGIs Indigo2 IMPACT, under IRIX, years ago (it was a bug in some revision of the R4XXX CPU, IIRC).

Thanks for any suggestions!

---

### Post by outofsync on 2009-04-22
> **outofsync said:**
> Hi,

I'm using 8.10 (x64) on an Acer 6935G, and I'm noticing that the CPU seems to sleep for very small periods (fraction of a second) when I'm not moving the mouse.

A simple way to notice it is with the blinking cursor at the terminal: If I'm moving the mouse, the blinking rate is uniform. If I don't move the mouse, the blinking rate is non-uniform.

It can also be noticed with the system monitor, specially at the CPU graphs, where you can notice that the graphs don't scroll at constant speed unless I move the mouse.

I'm not sure if this happens all the time, but it's happening in this same moment.

I remember this same issue happened with some models of SGIs Indigo2 IMPACT, under IRIX, years ago (it was a bug in some revision of the R4XXX CPU, IIRC).

Thanks for any suggestions!

It has been fixed by installing updates about a week ago or so, although I don't know which update fixed it. I guess it might be a kernel update.

Now the micro-freezes seem to be gone, and everything works fine :)

---

