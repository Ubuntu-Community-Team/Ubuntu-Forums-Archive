---
title: "Hyperthreading and kernel"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by Zalbor on 2006-03-06
Back when I was using Fedora Core, I noticed it had installed an SMP kernel, I imagive because my CPU is a hyperthreading P4. Ubuntu installed a regular kernel though; does that mean ubuntu judged the normal kernel to fit my system better? If I try to install an smp kernel anyway, will it work better or would it be unfit for my system and ubuntu?
Thanks in advance.

---

### Post by cosborn72 on 2006-03-06
Ironic - I've had just the opposite experience.

I have a Gateway laptop, which was running Ubuntu using the SMP kernel.  I installed MEPIS, and it appears to use the non-SMP kernel.  

Ubuntu automatically detected the hyper-treading - I didn't even know what it was.

I believe I was running breezy at the time.

---

### Post by Zalbor on 2006-03-06
So should I try installing smp, or is there a chance it would screw my system up or something?

---

### Post by codejunkie on 2006-03-06
[QUOTE=Zalbor]So should I try installing smp, or is there a chance it would screw my system up or something?[/QUOTE]
the smp kernels support hyperthreading and dualcore/multipleprocessor systems try the smp kernel it should improve the preformance.
edit: the linux-image-686-smp kernel would probably be the best one.

---

### Post by Zalbor on 2006-03-08
I installed the smp kernel and tried booting it. It seemed to go on well, until the point where the X server was supposed to start. Instead I got a terminal and a text-based GUI saying something like "The X server could not be started, probably because it's not configured properly".
I imagine this is solvable, but how? And also, if I make X work with the smp kernel, will it still work with the non-smp one in case I need to use it someday?

---

### Post by codejunkie on 2006-03-08
[QUOTE=Zalbor]I installed the smp kernel and tried booting it. It seemed to go on well, until the point where the X server was supposed to start. Instead I got a terminal and a text-based GUI saying something like "The X server could not be started, probably because it's not configured properly".
I imagine this is solvable, but how? And also, if I make X work with the smp kernel, will it still work with the non-smp one in case I need to use it someday?[/QUOTE]

if you have an nvidia video card,
and you manually installed your video card driver you have to reinstall it, each time you use a different/new kernel. if you used the nvidia-glx package in synaptic, all you have to do is install the linux-restricted-modules package for your kernel/kernels and it will work with every kernel you have the restricted modules installed for.

if you have a video card other than nvidia i can't give you an answer on that one because i've haven't used anything but nvidia in a long time.

---

### Post by Zalbor on 2006-03-08
Thank you - that fixed it! :D
I wonder though, how come wasn't 686-smp chosen when I was installing, instead of simple 686?

---

### Post by codejunkie on 2006-03-08
[QUOTE=Zalbor]Thank you - that fixed it! :D
I wonder though, how come wasn't 686-smp chosen when I was installing, instead of simple 686?[/QUOTE]
im not 100% sure on this but i think that the 386 kernel is the only one shipped with the install cd. i do know that the dvd has more kernel packages and it automaticly detects and install's the right kernel for your processor, so my guess is they just do this to make room for other packages.

---

### Post by Zalbor on 2006-03-08
I see... It's the DVD that I have, so I guess they didn't put the SMP ones in it.

---

