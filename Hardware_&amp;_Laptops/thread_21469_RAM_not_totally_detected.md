---
title: "RAM not totally detected"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by soul_rebel on 2005-03-22
Hi everybody!

this is what happens: 
> 
andrea@soul-rebel:~ $ free -m
             total       used       free     shared    buffers     cached
Mem:           885        321        563          0         16        148
-/+ buffers/cache:        156        728
Swap:         1537          0       1537


my memory amount is 1024 and free tells me i have got only 885.
Tested with kernel 2.6.8.1 from warty and with 2.6.10 from hoary.

Any idea what the problem is?
thanks

EDIT:
SOLVED: see [this wiki page](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-21.1496455883/view?searchterm=686) 

Bye and thanks

---

### Post by boobytrapped on 2005-03-22
I think the problem is that Ubuntu kernel's do not come with highmem support.  I myself 1gig of ram as well, but because of this reason not all shows up.  Having highmem support would give you the rest of the ram; however there would be a performance penalty for highmem support.

However, I know that there are kernel patches (Con Kolivas' kernel contains them) that support 1Gig of RAM without highmem.  I don't know if that will ever be picked up by Ubuntu.

Any ubunutu developers care to comment on this?

---

### Post by johneboy on 2005-03-22
Hi soul_rebel,

I had the same thing when I first installed Warty.  You need to upgrade to a himem enabled Kernel using synaptic.  The following link to the Ubuntu Wiki describes the very issue.

[Ubuntu Wiki Page about hi mem kernel](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-21.1496455883/view?searchterm=686) .  Also read the following page to determine exactly which kernel you require [Processor specific kernels](http://www.ubuntulinux.org/support/documentation/faq/optimised-packages/view?searchterm=linux-k7).

I personally upgraded to the linux-k7 kernel as I have an AMD Athlon XP processor.  Now I see my full 1024Mb of memory.

Hope that helps

Regards

John

[QUOTE=soul_rebel]Hi everybody!

this is what happens: 


my memory amount is 1024 and free tells me i have got only 885.
Tested with kernel 2.6.8.1 from warty and with 2.6.10 from hoary.

Any idea what the problem is?
thanks[/QUOTE]

---

### Post by soul_rebel on 2005-03-22
edited first message. Thanks for the help. See you

---

