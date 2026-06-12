---
title: "How to see more than 3gig of ram?"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by RawMustard on 2005-10-15
I have 4 gig of ram, but ubuntu only reports that I have 3gig, is there some way to let it see the rest of my ram?

---

### Post by Rogmo on 2005-10-16
What i found out that, you need to build your own kernel.


You need to put this under Processor type and features section of kernel


```
High Memory Support (4GB)
```


Dont know how to build a kernel, but i believe other people will help you out in this area

---

### Post by RawMustard on 2005-10-20
Thankyou for your help!

Hmm, I just loaded up all the kernel stuff to set this option but it would seem to already be set.
I guess I've got bigger problems :(

---

### Post by medgno on 2005-10-20
If someone could figure this out I would also appreciate it. I've been having the same problem for quite a while, and was thinking breezy would fix it, since the release notes said " Support for up to 4 gigabytes of RAM by default on 32-bit architectures"

---

### Post by boltronics on 2005-11-28
Apparently, some motherboard BIOSs map the 4th GB of memory from 5Gb, and thus need PAX support. Sounds hard to believe, but I'm recompiling my breezy kernel right now with High Memory Support (64GB) set just to be sure.

---

### Post by avilella on 2005-12-20
Does anybody know if this is solved in Dapper Flight2?
Does anybody of you happen to have this problem with a Dell Dimension 5000? :-p

---

### Post by nick58b on 2005-12-20
I've got a Athlon 64 X2 machine with 4 GB of ram, with both the linux-686-smp and linux-k7-smp kernels 'free -m' displays only 3297 MB of memory.  Throwing the 64-bit breezy livecd in the box brings up all 4 gigs, while 32-bit RR4 and Knoppix LiveDVDs also show around 3300 MB of memory.

Has anyone had success in seeing all 4 GB on 32-bit Ubuntu? I'm wondering if I should spend my time recompiling the kernel, or just move to 64-bit.

---

### Post by nick58b on 2005-12-20
The 64 GB kernel option suggestion worked. I recompiled using the guide here:

[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

and changed the "High Memory Support" option from 4 GB to 64 GB and now my 32-bit Breezy can see the full 4 GB.

---

### Post by avilella on 2005-12-21
[QUOTE=avilella]Does anybody know if this is solved in Dapper Flight2?
Does anybody of you happen to have this problem with a Dell Dimension 5000? :-p[/QUOTE]

I reply to myself:

Using Dapper Flight2 Live only 3G are seen...

---

