---
title: "powernowd: disabling a speed step"
date: 2008-08-21
forum: Hardware
---

### Post by SoulinEther on 2008-08-21
So I got myself a laptop recently and Ubuntu works great on it, just a few hitches with 64-bit and wireless (wired, for that matter, too).

But this is also my first computer whose CPU supports frequency scaling.

My CPU is a Turion RM-70 and according to powernowd it supports 3 steps on each core: 500 mhz, 1 GHz, and 2 GHz.

I use this laptop as a desktop also (this laptop is like 10x better than my old desktop lol), and it sort of overheats in Ubuntu. Using powernowd, the temperature goes down significantly, but at 500mhz/core, it becomes slow, and shifting up to the next step takes too long.

I was wondering if there was a way for it to never switch down to 500mhz, only swapping between 1 and 2 GHz?

I'm also going to try upping the minimum CPU frequency necessary to go up a step, but I think that might be a bit too overkill of a solution, causing it to also jump to 2 GHz. I'll try a lot of general tweaking, too, in case that there is no way to make a certain minimum.

And how long does the CPU take to change from one frequency to the next? Is it a processor-intensive task?

Thanks.

---

### Post by libra1780 on 2008-08-24
try use cpufreq
here the HOWTO
[http://ph.ubuntuforums.com/showthread.php?t=394911]("http://ph.ubuntuforums.com/showthread.php?t=394911")
switching should be instant, and no, it's not an intensive task, just a hardware command

---

