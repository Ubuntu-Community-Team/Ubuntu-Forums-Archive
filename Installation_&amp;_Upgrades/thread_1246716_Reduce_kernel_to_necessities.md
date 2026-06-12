---
title: "Reduce kernel to necessities?"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by DejitaruJin on 2009-08-22
I am currently running kernel 2.6.30 on Ubuntu 9.04. I failed twice to slim down what went into it; first disabling my hard drive, then disabling my NIC. Neither case made any sense at all (my drive is not SCSI or SATA, and my NIC is 10/100, not 1000), so after that, I just gave up and let it keep its default configuration, aside from things like optimizing it for a Pentium M.

I have been told that, to increase the speed of my system, I should slim the kernel down, and make it as monolithic as possible. That certainly sounds like a good idea.

However, I have no idea what modules I *really *need. The output of lsmod is... cryptic, to say the least, and I see only two that I can positively match to a listing in the kernel configuration.

Right now, everything runs perfectly fine (albeit a bit slowly), because amongst that huge mess of drivers are the ones I need. I would like a way to  specifically configure the kernel to *only* include what is keeping the computer operational at the moment (because it's a laptop, it isn't changing any time soon), and make it completely built into the kernel. The only exceptions are all of the USB and PCMCIA drivers, which should still all be present and in module form.

Is there a simple way to do this? Or even a complicated way, I don't care. The output of lsmod is even short enough to do it all manually, if I could make sense of it all - though it seems to not mention things that are already fully built into the kernel, necessary or not.

---

### Post by DejitaruJin on 2009-08-22
Huh, drive's been disabled again. I've got the kernel down to the point where it compiles in about half an hour (down from about five hours), but clearly something is missing. Isn't there a tool somewhere? Something I can run that will give me a single list of "this is precisely what your computer needs to operate"?

---

