---
title: "SMP KERNEL failure on x2 3800+"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by flapane on 2006-10-24
I bought a new cpu, and I tried a custom 2.6.18 smp kernel, and the 2.6.17 ubuntu kernel, however the system freezes at booting, with a kernel panic, and telling:  powernow-k8: MP systems not supported by PSB BIOS and then a lot of strange infos before telling KERNEL PANIC.
You can see these strange errors in the video I made (please raise the contrast in order to view correctly) [CLICK HERE]("http://napex.altervista.org/kernel.zip")
What to do?
i can boot without problems with a non smp kernel (1 cpu and not 2)

No problems in XP SP2

---

### Post by Aberrix on 2006-10-24
In Edgy they don't use the k7 kernel, etc, etc

the generic kernel has k7 and smp support, use that one.

---

### Post by flapane on 2006-10-24
but I have a k8
anyway I built my custom kernel, it should'nt give thos errors...

---

### Post by Aberrix on 2006-10-24
> **flapane said:**
> but I have a k8
anyway I built my custom kernel, it should'nt give thos errors...

you're profile say's you are using Edgy.

Use the generic kernel, that has support built in for everything instead of having to use seperate kernels.

---

### Post by flapane on 2006-10-24
So if you try the k8 kernel you get the same errors?

---

### Post by Aberrix on 2006-10-24
> **flapane said:**
> So if you try the k8 kernel you get the same errors?

I used the k7-smp kernel when I used dapper, I don't know where you got the idea that you need to use a k8 kernel.([link]("http://www.ubuntuforums.org/showthread.php?t=85917")) But I don't know that much either so?... When I upgrded to Edgy it wasn't allowing me to use the k7-smp kernel and I did some digging ([link]("http://www.ubuntuforums.org/showthread.php?t=283056")) and found out I should be using the generic kernel now.

---

### Post by flapane on 2006-10-24
I am using the 64bit version of Ubuntu, sounds like strange a k7 kernel...

---

### Post by Aberrix on 2006-10-24
> **flapane said:**
> I am using the 64bit version of Ubuntu, sounds like strange a k7 kernel...

I guess that our difference between you and I, I am running the 32-bit version of Ubuntu.

Regardless from my understanding "the generic kernel is the only one used for Edgy"

---

