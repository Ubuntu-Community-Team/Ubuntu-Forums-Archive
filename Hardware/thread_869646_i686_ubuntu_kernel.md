---
title: "i686 ubuntu kernel"
date: 2008-07-25
forum: Hardware
---

### Post by S-99 on 2008-07-25
One thing i was really surprised about ubuntu was one small aspect that sort of sucks. I have an intel core 2 duo laptop, and i switched from mandriva to pure debian with the i686 kernel. Oh man did that make debian snappy. I tried the i586 kernel in debian and it ran about as fast as kubuntu did. So i reinstalled kubuntu because debian testing is more trouble than it's worth to get nvidia proprietary drivers up and running on at the moment. I took a look at the ubuntu repos and noticed it's got just a lot of choices for choosing different kernels.

Except for anything i686. I'm happy with the way my laptop is set up at the moment, but i know anyone with pentium 4 on up can run the i686 kernel and it makes the system a lot faster. Why does ubuntu offer just about everything desired for kernel selection besides an i686 kernel? It'd be really cool if ubuntu included such a kernel in the repos because installation and upgrade would be a lot easier than installing through other means.

---

### Post by sdennie on 2008-07-25
The closest thing in Ubuntu would be the -generic kernel which is compiled with optimizations for 586 machines.  I would be very surprised if changing the the optimization target to 686 would make a significant difference but, it would be very easy to download the kernel source, change the optimization target to your exact CPU and rebuild.  There are many, many guides for doing this:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

---

### Post by S-99 on 2008-07-28
I guess i'll have to do that. It sucks ubuntu doesn't have an i686 kernel in the repos i guess. Well if there's no difference in speed when using an i586 kernel then i guess i should just use an i386 kernel and wonder what you meant by your answer. Yes i686 does make a pretty significant difference in linux speed compared to an i586 kernel.

---

### Post by sdennie on 2008-07-28
I don't recommend the Ubuntu -386 kernel because it seems to be aimed at very old machines (for instance, it doesn't have SMP support compiled in).  I actually run a custom kernel compiled with optimizations for my architecture (Core 2 Duo) and, comparing it to the Ubuntu -generic kernel, there is little to no difference in performance that I can see.  I haven't done formal benchmarks between the two but, in for basic usage, nothing jumps out as being noticeably slower or faster for either kernel.

---

