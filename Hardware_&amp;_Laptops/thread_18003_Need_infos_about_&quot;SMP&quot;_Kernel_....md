---
title: "Need infos about &quot;SMP&quot; Kernel ..."
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by Shinkan on 2005-03-04
Hi folks !!

I'm relatively newbie to linux systems, and I would like to know if "SMP" versions of kernels are for PHYSICAL multi-processing or LOGICAL multi-processing ?
I would mean : Should I set up ...-smp for my Hyper Threading P4 (logical multiprocessing for those who have been sleeping for many months) ?

ThanX !

---

### Post by Shinkan on 2005-03-04
OK, I'll answer myself ...

It seems that SMP kernels are better for Hyper Threading Compatible processors.
But I can't find complete documentation about SMP specifying that ...
In fact, Intel clearly annouce that an operating system MUST be compatible with the hyper threading technology for the user to use this technology.  :-({|=

---

### Post by alastair on 2005-03-04
If "HT" is on (BIOS?) then yes, you will need an SMP kernel.

Install one and try it. Remember - you can choose kernels at the boot screen - press ESC at boot.

---

