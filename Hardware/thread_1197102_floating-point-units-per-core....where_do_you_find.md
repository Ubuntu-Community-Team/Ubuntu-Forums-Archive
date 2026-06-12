---
title: "floating-point-units-per-core....where do you find this value?"
date: 2009-06-25
forum: Hardware
---

### Post by helstreak on 2009-06-25
how do I find this value for a processor?

thank you for your help

---

### Post by toopi on 2009-06-25
I think there is generally one FPU/core in today's multicore processors, but I don't know how to find that out from the OS.

You can find out about your processor's instruction sets the following way in the CLI:
```
 cat /proc/cpuinfo 
```

---

### Post by helstreak on 2009-06-25
> **toopi said:**
> I think there is generally one FPU/core in today's multicore processors, but I don't know how to find that out from the OS.

You can find out about your processor's instruction sets the following way in the CLI:
```
 cat /proc/cpuinfo 
```


I'm buying processors for a computer cluster so I'm trying to figure out what the processors have.

---

### Post by toopi on 2009-06-25
Oh!  I see.  Since I am not an expert on HPC, someone with great knowledge on clustering should chime in here.

A nice howto on this topic is [here]("http://www.gentoo.org/doc/en/hpc-howto.xml"), if you are interested.  I know it is really for Gentoo, but you will get some ideas.

Btw, I received a mail about a webinar regarding on HPC the other day.  Here's the [link]("http://www.linux-mag.com/id/7328") (need to register though, but free I think), if that intrests you as well.

---

### Post by sdennie on 2009-06-25
I'm not sure if you are asking the right question.  I think you want to know how many floating point instructions a core can execute per clock cycle.  The answer is very dependent on your software, how it's been compiled and what instruction sets your CPU has.  I would recommend you try your software on single node versions of various machines and see what performance is like.  However, unless the problems you are trying to solve aren't dependent on the latency of passing data between nodes (which is VERY high), chances are good that node computational speed (i.e. "how many FPUs it has") isn't going to be the bottleneck in a cluster.

---

### Post by helstreak on 2009-06-25
> **sdennie said:**
> I'm not sure if you are asking the right question.  I think you want to know how many floating point instructions a core can execute per clock cycle.  The answer is very dependent on your software, how it's been compiled and what instruction sets your CPU has.  I would recommend you try your software on single node versions of various machines and see what performance is like.  However, unless the problems you are trying to solve aren't dependent on the latency of passing data between nodes (which is VERY high), chances are good that node computational speed (i.e. "how many FPUs it has") isn't going to be the bottleneck in a cluster.

It's not software, it's an actual hardware device designed for doing floating point calculations.  

[http://en.wikipedia.org/wiki/Floating_point_unit](http://en.wikipedia.org/wiki/Floating_point_unit)

---

### Post by lisati on 2009-06-25
> **helstreak said:**
> It's not software, it's an actual hardware device designed for doing floating point calculations.  

[http://en.wikipedia.org/wiki/Floating_point_unit](http://en.wikipedia.org/wiki/Floating_point_unit)

There was a time when CPUs in the x86 family didn't come with a FPU built in. One option was to install a FPU on the mobo, but, trouble was, not all mobos had provision for it, let alone actually having one. Another option was to provide a FPU emulator in software. 

If memory serves correctly, MS-DOS programs could use INT 11 to query the BIOS and discover if a FPU is installed, and either use the proper FPU instructions or call up an emulator.

---

### Post by sdennie on 2009-06-25
> **helstreak said:**
> It's not software, it's an actual hardware device designed for doing floating point calculations.  

[http://en.wikipedia.org/wiki/Floating_point_unit](http://en.wikipedia.org/wiki/Floating_point_unit)

I know what an FPU is.  :)

What I'm saying is that if you could type:

```

cat /proc/number_of_fpus

```

It would have no direct relevance on how fast your software would run.  You can currently type:

```

grep MHz /proc/cpuinfo

```

And that number is largely meaningless.  5 years ago I had a Pentium 4 at 3.4Ghz and now I have a Core 2 Duo at 2.5Mhz.  Yet this machine is much faster even for single threaded applications.  From a user standpoint, the interesting numbers are how well a chip runs your software and not how many "foos" it has.

---

### Post by jgeorger on 2009-06-25
Maybe this is not what you want to hear but it almost is irrelevant.  It is very hard to even find FLOPS numbers on various CPU's because they are so memory bandwidth starved - keeping the cores fed is the biggest challenge.  In the Netburst P4 vs the AMD Opteron a few years ago, the P4 looked better on paper with a higher theoretical flop count.  However the Opteron performed better in practice, attaining a higher "computational efficiency" than the P4 - probably due to the on-die memory controller.

With the advent of Core2 Intel took back the crown and AMD has been playing catch-up ever since.  I've tested AMD Istanbul and it still doesn't even beat Intel's previous-gen Harpertown Xeon (54xx).  I'm just about to get my hands on a Nehalem-based Xeon (55xx) system, but from the reviews I've read it is quite an impovement.

I *think* I read that Nehalem can do 4 flops/clock/core, and Istanbul 3, but I'm not totally sure of that.  There is a 6 core Istanbul out now, Intel is not releasing hex core until early 10 from what I've read.

---

### Post by helstreak on 2009-06-25
> **jgeorger said:**
> Maybe this is not what you want to hear but it almost is irrelevant.  It is very hard to even find FLOPS numbers on various CPU's because they are so memory bandwidth starved - keeping the cores fed is the biggest challenge.  In the Netburst P4 vs the AMD Opteron a few years ago, the P4 looked better on paper with a higher theoretical flop count.  However the Opteron performed better in practice, attaining a higher "computational efficiency" than the P4 - probably due to the on-die memory controller.

With the advent of Core2 Intel took back the crown and AMD has been playing catch-up ever since.  I've tested AMD Istanbul and it still doesn't even beat Intel's previous-gen Harpertown Xeon (54xx).  I'm just about to get my hands on a Nehalem-based Xeon (55xx) system, but from the reviews I've read it is quite an impovement.

I *think* I read that Nehalem can do 4 flops/clock/core, and Istanbul 3, but I'm not totally sure of that.  There is a 6 core Istanbul out now, Intel is not releasing hex core until early 10 from what I've read.


the reason this number is needed is to calculate the theoretical peak performance of a computer cluster.

peak-performance = #nodes x #cores-per-node x floating-point-units-per-core x clock-speed

---

### Post by lisati on 2009-06-26
> **sdennie said:**
> 
And that number is largely meaningless.  5 years ago I had a Pentium 4 at 3.4Ghz and now I have a Core 2 Duo at 2.5Mhz.  Yet this machine is much faster even for single threaded applications.  From a user standpoint, the interesting numbers are how well a chip runs your software and not how many "foos" it has.

I concur that the numbers can be misleading if all one works with is the clock frequency, there are other factors which come into play. My current laptop, with 1.66GHz dual-core cpu & 2Gb RAM runs the same video editing software much better than my 4-year-old desktop with 1.79GHz "single-core" machine with 1GB ram.

---

