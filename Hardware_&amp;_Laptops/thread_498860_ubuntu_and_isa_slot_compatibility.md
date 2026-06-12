---
title: "ubuntu and isa slot compatibility"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by zutronius on 2007-07-11
How well does ubuntu work (or not work) with older ISA slot cards. I run ubuntu some some older pentium II pcs that still use ISa slot and ive had generally ok luck so far. Just wondering what your experience have been?

---

### Post by tgalati4 on 2007-07-12
Since Linux is not a plug-n-play operating system, it requires the user to pay attention to interrupts and io ports.  Conflicts in resources will require active effort on your part to resolve.  If you turn off plug-n-play OS in the BIOS, Linux will generally detect and assign resources successfully.

Sometimes there are conflicts and you will have to either manually assign those resources in the BIOS and then specify them using modprobe options.  

There are also some oddball ISA cards out there that probably have no Linux support.  Try plugging them into your machine and expect a hard lockup when the kernel gets confused.

So, yes it works for common sound cards and network cards.  For more exotic cards (such as instrumentation cards that use 3 DMA channels) you will have to do some homework.

---

