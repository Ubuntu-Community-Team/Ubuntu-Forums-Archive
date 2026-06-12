---
title: "W1N sound - recompiling my kernel"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by spolu on 2005-05-12
hi just installed ubuntu on my ASUS W1N laptop and then need to recompile my kernel in order to activate sound debug to make my sound card work well.

But even if i added all the sources in synaptic, i can't figure out what package do i have to install to get the kernel sources and recompile my image (i have actually kernel-image 2.6.10-5-386 installed) without any problem

Indeed, i tried to do so with one kernel source package 2.4 and i simply couldn't make it work

Thank you for your help !

Stanislas

---

### Post by bigbangbigbigbang on 2005-05-12
[QUOTE=spolu]hi just installed ubuntu on my ASUS W1N laptop and then need to recompile my kernel in order to activate sound debug to make my sound card work well.

But even if i added all the sources in synaptic, i can't figure out what package do i have to install to get the kernel sources and recompile my image (i have actually kernel-image 2.6.10-5-386 installed) without any problem

Indeed, i tried to do so with one kernel source package 2.4 and i simply couldn't make it work

Thank you for your help !

Stanislas[/QUOTE]

Just run from a terminal apt-get install linux-source-2.6.10

or look for this package in synaptic.
With this kernel the external speakers will only work on this laptop if you compile in sound-debug and manually set some registers afterwards.
The sound works out of the box with a newer 2.6.11 kernel from kernel.org
The 2.6.11 kernel that you find in the ubuntu repos only give you freezes on this laptop, do not even try. Get the 2.6.11.9 from kernel.org

---

### Post by spolu on 2005-05-12
thanks, i just recompiled the 2.6.10 kernel and everything is working well

---

