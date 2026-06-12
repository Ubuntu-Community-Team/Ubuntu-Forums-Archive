---
title: "Dual Processors in Breezy"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by Milerky2-97 on 2006-05-24
I am recycling some old components attempting to build a file server in Breezy and I have no problems running it in this machine, but alas it seems to only be utilizing one of the processors.  

here are the specs, (Try not to laugh too hard)

2x Socket 370 Celeron Processors 366 clock speed ( O.C.ed to 523 Each)
576MB Ram
Radeon 7000 32mb Graphics

The Hardware Monitor seems to only show one processor.  Is there a way to do SMP Kernel in Breezy?

---

### Post by Hellaxe on 2006-05-24
You have to install the smp kernel.

---

### Post by Milerky2-97 on 2006-05-24
I figured that, but is there a way to have it defaulted during the install?  I looked through the tags, but couldnt find it.

It has been a while wince I installed any linux so I am a little behind the times


Thanks

---

### Post by Bandit on 2006-05-24
On breezy you will have to install the SMP kernel it in apt after ubuntu is installed. It only has one default kernel.
Hopefully they may change this in Dapper. Not sure if they have changed this or not in Dapper.

Cheers,
Bandit

---

