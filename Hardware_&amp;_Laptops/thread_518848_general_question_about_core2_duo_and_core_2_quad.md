---
title: "general question about core2 duo and core 2 quad"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Chymera on 2007-08-06
When it says:
> 2.4GHz 
If we're talking about a core 2 quad processor, does that mean that the processor has a frequency of 2400mhz only that it is distributed to 4 cores, ore does it mean that the processor contains 4 cores, each of them having a frequency of 2400mhz

---

### Post by steveneddy on 2007-08-06
I believe that all four cores run at 2.4 Ghz, but are not all added up together. 

Each core is 2.4, and all 4 doesn't equal 9.6 Ghz.

---

### Post by Chymera on 2007-08-06
why not? frequency stacks up additively. If a resort oscillates 2400 times per second and another one 600 times per second, together they oscillate 3000 times per second... right?

---

### Post by Depressed Man on 2007-08-06
Ugh I forget  how it's done (there was a discussion on the extremeoverclockers forum when dual cores started to get come onto the consumer market). But it has to do with the load not being distributed to both equally I think. So one core may be using more of its speed then the other core. 

But I don't remember much of that arguement..

---

### Post by dabl on 2007-08-06
> **Chymera said:**
>  If a resort oscillates 2400 times per second and another one 600 times per second, together they oscillate 3000 times per second... right?

This sounds like more of a philosophical question than a technical question.  The CPU cores are clocked by a common clock, so they cycle at the exact same rate.  If the clock is cycling at 3.0 GHz, then both (or all 4) cores are cycling at 3.0GHz.

If you want to say "I have (2 x 3.0GHz =) 6.0GHz in my computer", I guess that is a form of the truth.  :)

However, there is nothing running in this hypothetical computer at a rate of 6GHz.

---

### Post by Chymera on 2007-08-06
lets put it this way, if a certain command takes 6.000.000.000 oscillations to complete, in a core2duo, those oscillations will be distributed evenly to let's say two 3GHz cores. in one second both cores, put together will provide the 6 billion oscillations needed to complete the task.

this would in turn be equivalent to a 6GHz CPU which would indeed oscillate faster than any part of the core2duo processor, but would take the exact same time to complete the task.

---

### Post by fredj on 2007-08-06
If you run a program such as a video editing program that has been configured to work with
multi processors then on a dual core it will run about 1.87 times as fast as it would on a single
core. If you have a quad core it will run at about 3 times as fast as it would on a single core.
If you run a program that has only been written to run on 1 core then you won't get any speed
increase over a single core cpu. Quad core computers have to share cache and main 
memory so they can never reach 4 times the speed of a single core. Also at the same time
your computer has to run many operating system tasks in the background and these take up
cpu time. A 2.4 quad core has 4 cores each running at 2.4G. Many programs have only been
compiled to run on one core or two cores. Some operating systems handle multi-cores
better than others. Linux seems to be better than windows in this respect.

---

