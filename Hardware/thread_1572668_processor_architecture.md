---
title: "processor architecture"
date: 2010-09-11
forum: Hardware
---

### Post by flyingsliverfin on 2010-09-11
can someone (simply) explain processor architectures to me? i have a fairly outdated computer with 2* pentium 4 3.00 ghz processors. i heard that it was outdated because it had an old architecture, which is where my question originates from.

also, is it worth it for me to get a new computer anytime soon? i read somewhere it seems that these processors waste a lot of power. my other specs: 2.7 gb DDR2 ram (added more myself), nVidia Quadro FX 540. im not sure what this output from lspci -vv means :    Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
    Region 1: Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Region 3: Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
i dont do anything thats high processor and ram needy. the only thing i sometimes do is run virtual machines cuz i dont want to reboot into windows
also, im sometimes surprised how smoothly and quickly this computer runs compared to some of the newer ones like my dad's laptop (which is running windows so that might be the problem)

---

### Post by sikander3786 on 2010-09-11
3.0 GHZ with 2.7 GB DDR 2 is more than enough for routine tasks. I have been using Pentium 2.8 GHZ, 800 FSB, 1 MB, HT processor until 9.10 and it worked smoothly for me. It also did run a Windows Virtual Machine.

In my opinion you don't need to get a newer machine unless you are a hardcore gamer or a graphics designer.

If you are comparing your desktop to your father's laptop, desktop will win in most aspects. Many reasons.

---

### Post by coffeecat on 2010-09-11
A Pentium 4 is a 32-bit single core processor. Later ones included hyper-threading technology which emulates two virtual processors, but this isn't as good as having two physical cores. Today's Intel and Athlon CPUs are 64-bit and at have least two cores. Four-core machines are not uncommon. So in that respect your P4 is outdated, but if it works OK for you, then that's fine. You won't be able to run a 64-bit OS on it but Ubuntu will be supporting 32-bit architecture for some time to come yet.

The main problem with P4s is what you've already identified - they are power inefficient and need good cooling.

---

### Post by flyingsliverfin on 2010-09-11
> **coffeecat said:**
> A Pentium 4 is a 32-bit single core processor. Later ones included hyper-threading technology which emulates two virtual processors, but this isn't as good as having two physical cores. Today's Intel and Athlon CPUs are 64-bit and at have least two cores. Four-core machines are not uncommon. 


ive looked at the different bios options and hyper threading is there and on. does that mean when (in ubuntu) i do cat /proc/cpuinfo it gives me 2 entries (cpu 0 and 1) is that hyper-threading?

is it possible to have 2 seperate processors (actual chips) in 1 computer?
do todays cpu's also support 32-bit?

---

### Post by coffeecat on 2010-09-11
> **flyingsliverfin said:**
> ive looked at the different bios options and hyper threading is there and on. does that mean when (in ubuntu) i do cat /proc/cpuinfo it gives me 2 entries (cpu 0 and 1) is that hyper-threading?

If cat /proc/cpuinfo shows 2 entries then your CPU does support  hyper-threading. But you don't have two cores as with newer processors.  Wikipedia on hyperthreading:

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

> **flyingsliverfin said:**
> is it possible to have 2 seperate processors (actual chips) in 1 computer?

To be honest I don't know, but having a 2-core processor is as good (I believe) as having two processors.

> **flyingsliverfin said:**
>  do todays cpu's also support 32-bit?

Oh yes. Today's 64-bit processors are backward compatible and will run 32-bit OSs.

---

### Post by flyingsliverfin on 2010-09-11
and the advantages of 64 bit are just that its faster?

---

### Post by linux18 on 2010-09-11
your computer is fine, your running linux so you'll still run faster than windows for years to come (Heck, even small linux runs faster on a 386 than w7 on a p4 ) as long as it works for you, don't bother with naysayers

---

### Post by coffeecat on 2010-09-11
> **flyingsliverfin said:**
> and the advantages of 64 bit are just that its faster?

Here you go:

[http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit](http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit)

---

### Post by flyingsliverfin on 2010-09-11
i find understanding the way the processor works and operates confusing, but i dont need that right now i guess... 

thanks for answering all my questions

---

### Post by srs5694 on 2010-09-11
> **flyingsliverfin said:**
> can someone (simply) explain processor architectures to me?

Broadly speaking, "processor architecture" or "CPU architecture" refers to the instruction set and design details of a CPU. Today, only two architectures are common on desktop systems: x86 (aka i386 or various variants of this name, although there are subtle differences between them; or IA32), which is a 32-bit architecture; and x86-64 (aka AMD64 or EM64T), which is a 64-bit variant of x86. Macs older than about 3 years use another architecture, PowerPC. More exotic architectures are also available, although they're mostly used for servers, supercomputers, and embedded devices (in cell phones, game consoles, DVRs, and so on). A few netbooks use such oddball architectures, though.

Most desktop and laptop computers sold today use the x86-64 architecture. This can be faster than x86, but that's not always true. There are so many other factors that work into the equation that it's hard to compare CPU speed without using a benchmark test. An increasingly important advantage of x86-64 over x86 is that x86-64 enables access to much more memory than does x86, which theoretically maxes out at 4GB, IIRC. (Linux can address more than 4GB on x86 systems by using addressing tricks, but they slow down execution.)

For the most part, binary code for one CPU architecture can't be run on another one -- you can't run a PowerPC binary on an x86 system, for instance. An important exception is that x86-64 systems can run x86 binaries. This fact is helpful in the transition to x86-64, since legacy software can still be run.

The bit width of a CPU, incidentally, refers to the size of variables it processes in one chunk -- 32 or 64 bit for most modern CPUs. More may sound like better, but that's not always true. Most computations only require 32-bit integers, so the extra size won't speed things up. x86-64 can be faster than x86 because of other changes in the architecture, such as increasing the number of registers (on-chip storage slots) available.

> i have a fairly outdated computer with 2* pentium 4 3.00 ghz processors.

It sounds like you may have two physical processors. In the days before dual-core CPUs, some high-end systems had two physical CPUs. If you've got such a system, it's probably still reasonably speedy, especially if you don't load it down with overly bloated software. I wouldn't worry about it being a 32-bit x86 system rather than a 64-bit x86-64 system.

---

### Post by Yellow Pasque on 2010-09-11
> **flyingsliverfin said:**
> i have a fairly outdated computer with 2* pentium 4 3.00 ghz processors. i heard that it was outdated because it had an old architecture

Your CPU setup should be more than fast enough for most tasks. P4's aren't terribly efficient, but the extra money you spend on your electricity bill over the next few years should be significantly less than replacing your system.

My guess is that you're getting information from someone trying to sell you a new system :)

---

### Post by flyingsliverfin on 2010-09-11
nah it wansnt some guy trying to sell me stuff... i just visited a friend that built himself a new gaming desktop and he told me a bunch about processors and video cards, which led me to investigate what i have myself

---

