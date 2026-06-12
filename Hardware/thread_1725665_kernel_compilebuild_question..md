---
title: "kernel compile/build question."
date: 2011-04-10
forum: Hardware
---

### Post by mxaddict on 2011-04-10
I have a 64bit version of Ubuntu 10.10 Running kernel-2.6.32 and i want to recompile to make it a little faster, but am not sure how to set it to 64bit, cause i might be compiling as 32bit and, that wont work with my OS?

or do i have the wrong idea?

Help would be great.

---

### Post by Yellow Pasque on 2011-04-10
It sounds like you're running a kernel leftover from Lucid. Maverick uses 2.6.35.x. Try using that first.

The architecture will be detected by the configure, so unless you're doing something odd (like compiling in a 32-bit chroot), that's not a concern.

---

### Post by mxaddict on 2011-04-10
thanks for the reply, and you are right i got it compiled im now running kernel version 2.6.38.2-core2-xeon. i compiled it for the core2-xeon processor family, its faster at boot and alot of apps are faster, but, there is a but, something is wrong with the graphics, cause i get alot of flickering, and sometimes the screen doesnt update.

did i use the wrong processor family?

my proccessor is an Intel Pentium Dual Core P6100 Mobile

and from what i could gather from google, core 2 processor family is the closest.

---

### Post by mxaddict on 2011-04-10
bump.

---

