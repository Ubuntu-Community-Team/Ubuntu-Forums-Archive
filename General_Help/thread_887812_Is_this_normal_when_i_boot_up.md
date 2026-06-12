---
title: "Is this normal when i boot up?"
date: 2008-08-12
forum: General Help
---

### Post by Antihero20 on 2008-08-12
I'm new to Ubuntu and Linux all together, so when i boot up i press the Esc button and it appears as if I've got different version of Ubuntu on my computer and it asks me which OS i would like to boot up with and the selection is:

-Ubuntu 8.04.1, Kernel 2.6.24-19-generic
-Ubuntu 8.04.1, Kernel 2.6.24-19-generic(recovery mode)
-Ubuntu 8.04.1, Kernel 2.6.22-14-generic
-Ubuntu 8.04.1, Kernel 2.6.22-14-generic(recovery mode)
-Ubuntu 8.04.1, Memtest86+


So is this normal? I'm guessing not cause when i was upgrading to 8.04 the light went out a couple of times

Anyways help would be appreciated

---

### Post by Ezlo4 on 2008-08-12
I get the same thing, but I don't think it's anything unusual.

---

### Post by snowpine on 2008-08-12
It is totally normal, nothing to worry about.

Recovery mode is useful if things go wrong someday.

2.6.22-14 is an older version of the kernel. If something ever goes wrong with 2.6.22-19, you can fall back on the older version.

Memtest is for, well, testing your memory :)

It is totally normal.

---

### Post by rampageoberon on 2008-08-12
Yes that is normal. It is grub showing the different kernels available for you to boot with.

Generally you boot with the latest kernel so "Ubuntu 8.04.1, Kernel 2.6.24-19-generic". An older kernel is there for you to fall back on incase the newer kernel causes problems.

Hope that helps

---

### Post by finer recliner on 2008-08-12
If you dual boot with windows, that option would also show up on that list. This would be the point after you turn on your computer where you would get to choose if you wanted to boot to linux or to windows.

as stated above: this is normal, its just GRUB


EDIT:
i wanted to add that you do NOT have different versions of ubuntu installed, just different versions of the kernel (the core of the operating system and how it interacts with hardware). the wasted space is minimal, and its nice to have an older kernel at hand in case the newest one gives you problems.

---

### Post by kernelhaxor on 2008-08-12
That just gives u a chance to boot with an older version of the kernel if a recent update doesnt work for your computer .. It is very helpful at times ..
Thats perfectly normal .. you have nothing to worry about

---

### Post by Antihero20 on 2008-08-12
Ok then, now i feel better, i thought the light going out messed up something :P

Ubuntu keeps getting better XD

Thanks alot

---

