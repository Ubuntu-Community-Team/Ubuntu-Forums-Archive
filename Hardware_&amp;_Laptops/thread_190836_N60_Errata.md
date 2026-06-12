---
title: "N60 Errata"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by digitalkarabao on 2006-06-06
It appears the kernel of Ubuntu Dapper (just like in Breezy) contains a patch for the N60 errata in Intel processors. I would like to know how to recompile the kernel without the N60 errata patch.  I would like to scale down my CPU below 2GHz. I was able to do so in Breezy using a kernel compiled without the N60 errata patch. Help guys. Or is there is another way possible without recompiling the kernel? But recompiling the kernel would be fun. har har. but i know I need help on this one. It is an uncharted territory for me.

---

### Post by BobRyan on 2006-06-14
I've got a dapper kernel I compiled with the vanilla p4_clockmod.c
you can download it at: [http://www.8cylinder.org/dapper-n60/](http://www.8cylinder.org/dapper-n60/)
good luck

---

### Post by digitalkarabao on 2006-06-14
thanks a lot man. will try this one later. by the way, is hyperthreading support enabled in this kernel?

---

### Post by Spiderdba on 2006-06-16
This kernel doesn't work with dapper drake 6.0.6, which has a different kernel: 2.6.15-25 :(
what can we do?

---

