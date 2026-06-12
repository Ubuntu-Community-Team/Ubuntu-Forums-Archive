---
title: "High memory kernel"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by risager on 2005-04-10
On my Pentium M 1.7 GHz laptop with 1GB RAM doing dmesg I find

```
Warning only 896MB will be used.
Use a HIGHMEM enabled kernel.
896MB LOWMEM available.

```

I'm using the standard 2.6.10-5-386 kernel which is what the Ubuntu installer installed. Which kernel should I use to be get highmem? Pls do not tell me to compile one myself. 

BTW shouldn't I use the 686 kernel? Any reason why the installer choose not to use it? 

Any advice appreciated.

---

### Post by az on 2005-04-10
"BTW shouldn't I use the 686 kernel? Any reason why the installer choose not to use it? "

Yes, you should.

Because not all processors are pentiums.  But pentium processors can run the 386 kernel.

---

### Post by jdong on 2005-04-10
The Ubuntu "-smp" kernels (multiprocessor-enabled kernels) support HIGH memory. Use one of  them.


As to why the installer doesn't install a arch-optimized kernel by default, I am guessing it's for stability reasons (weird computers may hang under a 686 kernel, but not an 386 one)

---

### Post by risager on 2005-04-10
[QUOTE=jdong]The Ubuntu "-smp" kernels (multiprocessor-enabled kernels) support HIGH memory. Use one of  them.[/QUOTE]

So I should use 2.6.10-5-686-smp which seems to be the latest kernel in the ubuntu repositories. No disadvantages from using smp kernel on a single-processor system?

---

### Post by jdong on 2005-04-10
Yes, you should use that kernel.


The only disadvantage there is to using SMP kernels on UP systems is a "slight" performance hit. I've never seen it before....

---

### Post by risager on 2005-04-10
[QUOTE=jdong]Yes, you should use that kernel.[/QUOTE]

I'm using it now. Seems to be working great. Thanks guys.

---

