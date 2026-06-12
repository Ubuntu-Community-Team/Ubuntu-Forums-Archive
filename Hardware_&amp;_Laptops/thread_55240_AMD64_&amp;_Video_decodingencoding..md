---
title: "AMD64 &amp; Video decoding/encoding."
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by f0rmula on 2005-08-08
I'm putting together a MythTV box for use in my lounge.

I'm torn between a simple athlon board and chip, or spending a little extra on an AMD64.

I'm aware that the performance of 32bit code executed on an AMD64 is relatively comparable to an athlon, but what I'm after knowing is whether general video decoding will benefit at all from 64bit instructions.  I thought it may have done, as there's obviously a lot of floting point to do, but I'm not sure if the codecs are written to take advantage of a 64bit architecture.  

Does anybody know for sure?

James

---

### Post by losing.virginia on 2005-08-08
Generally speaking the Athlon 64 chips are much better for a number of reasons than the Athlon XP chips. Ignore the older Athlon 64 chips  (those based off of the Clawhammer, Newcastle, or Winchester cores) and look at the lower end chips that are based off of the Venice core. The Athlon 64 (Venice cores) have lower heat output and power requirements, are built on the 90nm process, and support SSE3 as well. Currently I am running Ubuntu AMD64 and the speed is nice but I really have no 32bit to comare it to. If you want easy by the book installation of software without much fuss go with Ubuntu-i386 but go with an Athlon64 processor (socket 939) so that you will at least have an upgrade path.

If you are comfortable hacking away at a command line to get some things to work then go with Ubuntu AMD64 and get friendly in the forums  :-P

---

### Post by f0rmula on 2005-08-10
[QUOTE=losing.virginia]Generally speaking the Athlon 64 chips are much better for a number of reasons than the Athlon XP chips. Ignore the older Athlon 64 chips  (those based off of the Clawhammer, Newcastle, or Winchester cores) and look at the lower end chips that are based off of the Venice core. The Athlon 64 (Venice cores) have lower heat output and power requirements, are built on the 90nm process, and support SSE3 as well. Currently I am running Ubuntu AMD64 and the speed is nice but I really have no 32bit to comare it to. If you want easy by the book installation of software without much fuss go with Ubuntu-i386 but go with an Athlon64 processor (socket 939) so that you will at least have an upgrade path.

If you are comfortable hacking away at a command line to get some things to work then go with Ubuntu AMD64 and get friendly in the forums  :-P[/QUOTE]

Thanks for the reply :)

I really don't want to wrestle with the AMD64 distro if it's going to be a problem.  I think it's the x86 ubuntu  for me then.

Are the 64 bit AMDs significantly faster than the athlons running 32 bit code?  I'm startewd to get tempted by the cheap and cheerful athlon approach if i'm only using the 32bit distro.

Cheers,

James

---

### Post by losing.virginia on 2005-08-11
The Athlon64 is the new generation (K8 as compared to the K7 which is the regular athlon) from AMD. The 64's support more instruction sets (sse2/3) and are faster outright, the x86_64 instruction set is a bonus and is inline to become the standard platform for all machines (including Apple).

If you look around you will see advantages but here are just a few

[list]
[*]no FSB..it is built into the chip
[*]better memory access
[*]newer motherboard chipsets = better features
[/list]

---

