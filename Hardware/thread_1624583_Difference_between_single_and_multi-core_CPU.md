---
title: "Difference between single and multi-core CPU?"
date: 2010-11-17
forum: Hardware
---

### Post by emagine on 2010-11-17
Hello all!

This is something that I have always thought about and could not find the answer with a google search. What is the actual difference between a single core or multi-core CPU?  More specifically, is a single core CPU with a clock speed of 3.0 GHz better or worse than a dual core processor with a clock speed of 1.5 GHz.  Or is it the same because the dual core processor has two cores at a speed of 1.5 GHz which makes it a total of 3 GHz.  Is the cpu all based on speed?  Because new families of processors will come out with different architectures but not necessarily faster clock speeds.  Could someone please explain this to me?

Thank you!

---

### Post by mikewhatever on 2010-11-18
Well, 'better cpu' may relate to many things apart from speed, for example responsiveness, multitasking, power saving, heat output, etc. If speed is the only thing that matters to you, then faster cpu is better for running a single given program.

---

### Post by emagine on 2010-11-18
> **mikewhatever said:**
> Well, 'better cpu' may relate to many things apart from speed, for example responsiveness, multitasking, power saving, heat output, etc. If speed is the only thing that matters to you, then faster cpu is better for running a single given program.
Could you be more specific about my questions regarding a single core vs a dual core.

---

### Post by mikewhatever on 2010-11-18
Sure. If speed is all that matters and the program in question can only use one cpu, then the faster single core cpu is better. That was a very specific, and also a very hypothetical scenario, rarely available in real life. Thus, speed is almost never the only consideration, and multiple programs running at the same time are all too common in modern computing.

---

### Post by astrology on 2010-11-18
so, it doesn't look like there's a clear preference outside of speed.

---

### Post by amauk on 2010-11-18
multi-core beats uni-core in 99% of cases

For general desktop usage, with lots of low CPU processes, having multi-cores will spread the overall load and you'll reduce context switching (the CPU switching between different processes - which is expensive)

For any CPU intensive use-case (video encoding, etc.) where a single program needs lots of processing power, chances are it'll be multi-threaded and so the load can be shared across all cores

---

### Post by cascade9 on 2010-11-18
OK, you've got several questions combined here..... 

Dual core- all that means is that you've got 2 CPU cores on a  single socket/slot. 

Clock speed- not a good way to mesure performance. eg, a 1.8GHz Athlon (2500+) can be faster than P4s up to 2.6GHz+ due to different cache, architecture, etc. A 'faster' CPU wont always have higher clock speed, even if you are you are comparing CPU within a family, e.g. a 'original' P4 3.0GHz (512K cache, 400MHz FSB) will be a fair bit slower than a P4 620 2.8GHz (2MB cache, 800MHz FSB). 

New CPUs tend to have lower clock speeds than the old P4s, the fastest P4 was 3.8GHz, the fastest non-overclocked and non-trubo mode CPU around now is a Phenom II X4 970 (3.5GHz). Even if the Phenom II was  a single core, it would still be MUCH faster than the P4, due to superiour architecture, more cache, etc.  

> **emagine said:**
> Hello all!

This is something that I have always thought about and could not find the answer with a google search. What is the actual difference between a single core or multi-core CPU? More specifically, is a single core CPU with a clock speed of 3.0 GHz better or worse than a dual core processor with a clock speed of 1.5 GHz. Or is it the same because the dual core processor has two cores at a speed of 1.5 GHz which makes it a total of 3 GHz. Is the cpu all based on speed? Because new families of processors will come out with different architectures but not necessarily faster clock speeds. Could someone please explain this to me?

Thank you!

To answer this is very difficult. Apart from newer CPUs having different cache levels, better architecture etc there is the question of is the program multithreaded? 

Even if its not, a 'slower' CPU (measured in GHz) is quite often faster when you compared performance. Pity I cant find the old P4 vs Core2Duo benchmarks I used to have bookmarked (I knew I forgot to save something on my last format/reinstall) but heres a nice Pentium D (2.66GHz, 1MB cache, dual-core) vs Core2Duo (2.4GHz, 2MB cache, dual-core) test. BTW, Pentium D is just a P4 with dual cores, so its faster in general than the older single core P4s.

[http://www.bcchardware.com/index.php?option=com_content&task=view&id=2869&Itemid=81](http://www.bcchardware.com/index.php?option=com_content&task=view&id=2869&Itemid=81)

The Core 2 Duo eats the P4 alive.

---

