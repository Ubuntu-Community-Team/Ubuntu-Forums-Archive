---
title: "Processor Speed Question"
date: 2010-07-21
forum: Hardware
---

### Post by Wug on 2010-07-21
This applies to all operating systems.

Say I have a build with an intel i7 processor.

i7's are quad core, with hyperthreading for 8 virtual/logical cores.  The hypothetical i7 in question runs natively at 3GHz.

I know that a 'hertz' is a unit of frequency and does not really measure speed, but still.  The 3GHz implies that all four cores are running at that speed, correct?  Giving roughly the same computational power as a single core processor running at 12GHz? (assuming that the processor has roughly the same capacity as a single core of an i7)?

I know the differences between serial and parallel computing.  This is more a hypothetical question regarding total computational throughput, not counting overhead or anything.

On that note, would disabling hyperthreading provide a performance boost because of the slightly reduced overhead?  Or is it efficient enough leave it running?  I do lots of serial stuff like video transcoding, and I think I would experience a performance benefit if I got 1/4 of the power instead of artificially limiting to 1/8.

Thoughts?

---

### Post by PresenceofMind on 2010-07-22
> **drag0nfur said:**
> This applies to all operating systems.

Say I have a build with an intel i7 processor.

i7's are quad core, with hyperthreading for 8 virtual/logical cores.  The hypothetical i7 in question runs natively at 3GHz.

I know that a 'hertz' is a unit of frequency and does not really measure speed, but still.  The 3GHz implies that all four cores are running at that speed, correct?  Giving roughly the same computational power as a single core processor running at 12GHz? (assuming that the processor has roughly the same capacity as a single core of an i7)?

I know the differences between serial and parallel computing.  This is more a hypothetical question regarding total computational throughput, not counting overhead or anything.

On that note, would disabling hyperthreading provide a performance boost because of the slightly reduced overhead?  Or is it efficient enough leave it running?  I do lots of serial stuff like video transcoding, and I think I would experience a performance benefit if I got 1/4 of the power instead of artificially limiting to 1/8.

Thoughts?

Hello dragonfur,

Yes, Intel Core i7 is a quad core general-purpose processor. Intel Corp. has recently release the Core i7 980X Gulftown which has six functioning cores. But the one you are talking about has four computational cores. 

Yes, Hertz (Hz) is the SI unit of frequency. All of today's processors support synchronous internal functions. So to synchronise everything (which inside the processor are the transistors) they have an external clock which run at various frequencies. Your hypothetical one has a clock frequency of 3GHz. 
And yes, this is not the only 'speed factor'. 

12GHz is a bit far-fetched. Even with all those physical and virtual cores, a processor of such power will probably not even go there.... UNLESS a program exists that uses all those computation cores simultaneously (possible if the software can run parallel in all the cores), then it might come close.....but most of the time, each core is often busy doing something.
In real-life, some of them are idle as there aren't many programs out there that use all those cores. Most programs are not even aware that they can split the workload among four cores. Operating systems are better at this. However, this is improving and programs are starting to offer multi-core support. 

Again, HT is only useful for programs that use this. There may or may not be a performance increase compared to a regular quad-core. HyperThreading is mainly aimed at parallel computing and is available for those programs that require multiple threads to run simultaneously. 

Personally, I would say to leave it switched on (unless the OS does not support is). This is in no way restricting it to 1/8 of power. It is still a quad-core.....

---

### Post by Wug on 2010-07-22
As you said, programs that are not aware of the additional cores (or are simply not scalable) will only be able to use one core at once, maximizing at 1/8 of the total power if HT is enabled (and 1/4 if not).  It would, therefore, be beneficial to disable it if running mostly non-scalable or non-core-aware programs.

I know that it is not really feasible to run a regular CPU at 12GHz, it was just a statement that if you could somehow run just one core of an i7 at 12GHz, ignoring all others, it would be as fast as the whole processor running at 3GHz.

Hyperthreading might not decrease performance as much as I fear it would (for non-scalable programs).  I read a brief description of how the technology works, and it exploits the following premise:
-There are multiple steps to processing a single instruction
-While any given step is in progress, the other steps are idle
-It is possible to run 2 instructions at the same time (each on a different step, and therefore using a different part of hardware)

So, while the added overhead and hardware strain of HT may decrease the amount of power available for non-scalable programs, it will increase the overall system processing throughput.

I think that settles things.  Hz is a stupid way of measuring processor speed, it should be done with flops...

---

### Post by PresenceofMind on 2010-07-22
Hello again,

To finish this off..

Yea, HT is more useful to the operating system than many of the user-programs at the moment. Personally I think a fast Dual-Core (possibly with HT) will suit your requirements far better than a quad-core. 

FLOPS should only matter to people who want the most out of floating point operations (which involves big numbers). This is a synchronised operation that is controlled by the external clock. Hence, the speed (or frequency) of the clock is the most important factor which decides how fast the transistor-gates in a processor switch, which in turn allows more floating operations to be completed. That's why the clock speed is at the top of the list rather than FLOPS.

Anyway, glad to hear you have arrived at your conclusion. Have a nice day......

---

### Post by Wug on 2010-09-21
I have purchased and assembled the machine I originally posted queries about.  I have come to the following important conclusions:

*Processor clock speed is a poor indicator of processor performance.
*FLOPS, on their own, are a poor indicator of processor performance.
*PC Wizard has multiple good benchmarks, as well as comparison data for other chips.  A good indicator of overall system performance, as well as performance of specific components.
*Hyperthreading does increase processing capacity for multithreaded applications and for multiple simultaneous applications significantly.
*Hyperthreading does not noticably impair singlethreaded applications as I had feared it would.  I feared it would enable support for twice as many threads by halving singlethreaded performance of each core.

That being said, I would like to post some rough benchmarks -
intel i7 930 2.8GHz, stock settings(my desktop, Win7) -
wPrime 32M (HT ON, 4 threads) - about 13s
wPrime 32M (HT ON, 8 threads) - about 9s
wPrime 32M (HT OFF, 4 threads) - about 13s
wPrime 32M (HT OFF, 8 threads) - about 13s
wPrime 1024M (HT ON, 8 threads) - about 300s

intel core duo T2400 1.83GHz(my laptop, WinXP/Ub10.04) -
wPrime 32M (HT N/A, 2 threads) - about 103s
wPrime 1024M (HT N/A, 2 threads) - idk, I didn't run it; probably all night

so yeah.  don't fall for the megahertz myth.  the research I did when buying parts led me to the conclusion that AMD is using high GHz values to trick people into believing in superior performance.  Their highest Phenom II X4 (iirc) runs at 4.0GHz, but is outperformed in many applications by the i7 930 (2.8GHz) at stock settings.  That being said, an i7 930 with a decent overclock of say 3.4GHz (120%) will perform most admirably.  Can you get a 120% overclock on a chip whose native freq. is 4.0GHz?  Probably not.

Overall conclusion - if you need multitasking power, go for an i7 or other 4 core processor with hyperthreading capability, and if you don't, go for a decent dual core.  Hyperthreading does make a significant difference, considering you are not actually adding additional hardware (but still get a 40% boost in capacity).  However, HT will not help singlethreaded applications on their own.

---

