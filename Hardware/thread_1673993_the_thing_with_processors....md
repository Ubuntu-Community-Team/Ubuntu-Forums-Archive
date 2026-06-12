---
title: "the thing with processors..."
date: 2011-01-23
forum: Hardware
---

### Post by supermooshman on 2011-01-23
Hi all,

I'm in the market for a new laptop, but things have changed since I last was looking for one (and I did not keep up)

What I was wondering is: what is the difference between all processors?
eg: the atom processor of intel exists up to 2.13 ghz (according to wikipedia) but how would it compare to a processor against another (non atom) of the same clock rate?

and what's the deal with all the "cores"?

Thanks

---

### Post by TBABill on 2011-01-23
Here's a link where you can compare nearly every CPU on the market by speed performance. There are charts for low end, mid range and high end CPUs. That should answer how one will perform against another even though they may share similar clock rates. 

Cores is a method of describing how many CPU's are built into one chip. Dual core is a 2 processor CPU and quad is 4. There is tons of additional info online about the different CPU's, cores, clock rates, etc.

---

### Post by supermooshman on 2011-01-23
> **TBABill said:**
> Here's a link where you can compare nearly every CPU on the market by speed performance. There are charts for low end, mid range and high end CPUs. That should answer how one will perform against another even though they may share similar clock rates. 


thanks for the quick reply, but I think you forgot the link?

---

### Post by cascade9 on 2011-01-23
Cores, most modern CPUs have atleast 2 cores. Each core acts like a single CPU, so a dualcore has twice as much CPU power as a single core version of the same CPU, and half as much power as a quadcore version of the same CPU. 

*edit- well, not exactly, because of shared CPU cache and because all the cores use the same memory interface, twice as many cores have slighty less than twice as much power.  

Atom at any given clockspeed would be much slower than a modern CPU of the same clockspeed and number of cores. 

Clockspeed seems like an easy way to measure performance, but its got horrible flaws. It doesnt take into account the improvements in architecture, inceased CPU cache size, inceased memory speeds, etc..

---

### Post by JRV on 2011-01-23
> **cascade9 said:**
> 
Atom at any given clockspeed would be much slower than a modern CPU of the same clockspeed and number of cores. 

If you are looking for maximum battery life Atom is the way to go.  If you are looking for speed forget it.
> **cascade9 said:**
> 
Clockspeed seems like an easy way to measure performance, but its got horrible flaws. It doesnt take into account the improvements in architecture, inceased CPU cache size, inceased memory speeds, etc..

True, speed = clock speed X instructions per clock cycle.

---

### Post by TBABill on 2011-01-23
Sorry, here's the link [http://www.cpubenchmark.net/](http://www.cpubenchmark.net/)

---

### Post by mastablasta on 2011-01-24
> **cascade9 said:**
> Cores, most modern CPUs have atleast 2 cores. Each core acts like a single CPU, so a dualcore has twice as much CPU power as a single core version of the same CPU, and half as much power as a quadcore version of the same CPU. 
 

 
in the old days when dual cores came out i read a review and explanation that if the software uses only one core then for example 2.4 Ghz single processor would be better than 1.8Ghz dual core. is that true?
 
anyway i bought a single core back then. still works ok now. wish i had money for a  computer upgrade (CPU & GPU at least)...

---

### Post by cascade9 on 2011-01-24
> **mastablasta said:**
> in the old days when dual cores came out i read a review and explanation that if the software uses only one core then for example 2.4 Ghz single processor would be better than 1.8Ghz dual core. is that true?

Yes, if you comparing CPUs of the same familty/architecture, with the same FSB, and the same cache. Multitasking while runnign the single-core only program could make the dual-core faster (depending on exactly what you are doing). 
 
> **mastablasta said:**
> anyway i bought a single core back then. still works ok now. wish i had money for a  computer upgrade (CPU & GPU at least)...

GPUs are cheap, provided that you have a PCIe slot. If you only have AGP, then they are expensive. Unless you know of a decent place to get 2nd hard parts. 

Its probably worth having a look for a decent 2nd hand parts place inyour area. There is a constant stream of ex-office machines getting recycled, and sooner or later all types of CPU show up. GPUs.....they tend to only get 'low end' models, but still, I'd rather have a newer low end card than an older one.

---

### Post by mastablasta on 2011-01-24
yah maybe later. for now it works fine for what i need it (winXP)... but with Windows 7 on later who knows... anyway the slot is AM2 i think, so i guess a better one would be easy to get. also card is not so old, just not the latest (radeon HD 3650) for now it all works fine. maybe i will run Ubuntu on it side by side for a while (after support for XP expires) before getting new windows. afterall computer is used for games, various office tasks and i need windows to handle e-banking and occasionall e-taxes as well. for some reason sometimes firefox just doesn't work and have to resort to IE (oh the humanity!)...

---

### Post by JRV on 2011-01-24
TBABill - Thank you for the chart, that's good information.

---

### Post by cascade9 on 2011-01-25
@ TBABill and JRV- be very wary of passmark. It a long way from prefect and some of the results are...arguable at the very least. 

> **mastablasta said:**
> yah maybe later. for now it works fine for what i need it (winXP)... but with Windows 7 on later who knows... anyway the slot is AM2 i think, so i guess a better one would be easy to get. also card is not so old, just not the latest (radeon HD 3650) for now it all works fine. maybe i will run Ubuntu on it side by side for a while (after support for XP expires) before getting new windows. afterall computer is used for games, various office tasks and i need windows to handle e-banking and occasionall e-taxes as well. for some reason sometimes firefox just doesn't work and have to resort to IE (oh the humanity!)...

If its AM2, you might have some real problems getting a new CPU, depending on chipset and motherboard manufacturer. 

With a HD3650 and a sempron CPU, I wouldnt be looking at a GPU upgrade untill you've got a CPU upgrade.

---

### Post by mastablasta on 2011-01-25
it's AMD Athlon 64 3800+ 2.4 Ghz. and is still doing fine...
 
not sure what the motherboard is.... some gigabyte would have to look. for more pricise info i would have to look into it. Athlon is not one of the first one as computer is like 3 or 4 years years old. with DDR2 ram.
 
i think i will just wait for the motherboard to die and then upgrade :-) kind of have other priorities at the moment...
 
then later i can do full upgrade. i can give these older components to my wife's ocmputer. replace her Radeon 9600XT AGP card with this PCIe card (her mobo has two slots for GPU), replace her DDR ram with DDR 2 (mobo also has two slots). the only surplus will be the processor (since i couldn't find her a mobo like that with AMD chips). but then again she has a new dual core celeron (i think E3300) now so what good would this single core AMD do? :-)

---

