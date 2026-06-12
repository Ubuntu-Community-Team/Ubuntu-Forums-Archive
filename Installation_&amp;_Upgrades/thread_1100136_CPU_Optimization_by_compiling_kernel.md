---
title: "CPU Optimization by compiling kernel?"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by dhysk on 2009-03-18
From what I can tell Ubuntu x86 is compiled for an x86 core and although it works is not necessarily compiled for a Core2Duo.  I know that the current kernel version I'm using actually has a Core2Duo option under the processor types.

From what I've heard compiling for you specific core will give you a performance boost, makes since anyway. I have only compiled from source once, it worked however I knew little of what I was doing.

My question is how much of a performance boost, and for those more technical people out there, how exactly would it boost performance if going from x86 to a core2duo compiled kernel?  Second how likely, if using all the same options as the generic kernel, am i to break something?

System
Ubuntu 8.04 2.6.24-23-generic
Core2Duo E8400 3.0 GHZ @ 1333 Mhz bus
4 GB ram @ 800 MHz
GForce 9800GTX+

---

### Post by cariboo on 2009-03-19
Have a look at [this]("http://help.ubuntu.com/community/Kernel/Compile") if you are planning on compiling a custom kernel. I would also suggest trying out the 64-bit version, as it makes better use of 64-bit cpu's.

Jim

---

### Post by mrsteveman1 on 2009-03-19
Using a 64bit kernel will give you more performance than compiling for a specific cpu architecture.

64 bit processors have more registers, which is why there is some performance increase possible. The increase associated with compiling for Conroe or one of the others specifically is going to be minimal, because the kernel isn't really what determines the speed of executing of user programs.

---

