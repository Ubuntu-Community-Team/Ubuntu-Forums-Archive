---
title: "How to load a new DSDT ?"
date: 2005-01-21
forum: Hardware &amp; Laptops
---

### Post by snop on 2005-01-21
Hi,

I own an Acer Travelmate 4001Wlmi.  I know it has a buggy dsdt and here's a link to a corrected dsdt: [http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/dsdt.html](http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/dsdt.html)

But I don't know if there's another way other than kernel recompilation to load a custum dsdt file (I'm comfortable recompiling kernels but I'd like to stick to ubuntu kernels since it's easier to update/upgrade).

Thanks in advance

SnOp

---

### Post by snop on 2005-01-21
Ok, I'm gonna answer to myself.

I've found this:
[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

It seems that there's a patch that allows loading a new DSDT just appending the new DSDT to initrd. It seems that 2.6.9 kernel from Ubuntu has this patch but 2.6.10-2 (the one I'm using) hasn't.

Any developer knows if this patch will be included in kernel 2.6.10 ?

Perhaps I try to install 2.6.9 again and load a new DSDT. 

Bye

SnOp

---

