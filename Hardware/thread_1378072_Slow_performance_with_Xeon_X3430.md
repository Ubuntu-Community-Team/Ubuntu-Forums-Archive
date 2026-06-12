---
title: "Slow performance with Xeon X3430"
date: 2010-01-11
forum: Hardware
---

### Post by BiggerBadderBen on 2010-01-11
I just received a couple of new Dell T110 servers with the following hardware:
[LIST]
[*]Xeon X3430 Quad core with 8MB cache @ 2.4GHz
[*]8GB RAM
[*]250GB 7200RPM SATA HD
[/LIST]

I'm using these machines as build servers for a fairly large project.  They are supplementing two T100 servers that are identically configured apart from different CPUs: Xeon X3220 @ 2.4GHz.  I have an HP desktop with Q6600 Core2 Quad that performs roughly the same as the X3220 ones.

The new machines are significantly slower than the old ones at two tasks:
[LIST=1]
[*]Code generation project using Sun 2.6.16 javac (64-bit):  OLD=28minutes, NEW=39minutes
[*]C++ project using 32-bit cross-compiler (gcc-based)  OLD=66 minutes, NEW=96 minutes
[/LIST]

I've run the tests multiple times on both new machines, and the slowness is repeatable.  To remove any differences in installation, I cloned one of the old machine's hard drives, but no difference.

Ubuntu version is 9.04 Server x86_64, last updated November or so.

Is anybody aware of kernel or BIOS optimizations that can make these machines work at least as fast as the older ones?  I'm at my wit's end - how can brand new machines with more modern CPUs and memory take 50% longer to compile?

thanks,
Ben

---

### Post by BiggerBadderBen on 2010-01-11
Problem solved by disabling **cstates** in BIOS.  I guess this kernel doesn't know how to deal with the new Turbo mode...

---

