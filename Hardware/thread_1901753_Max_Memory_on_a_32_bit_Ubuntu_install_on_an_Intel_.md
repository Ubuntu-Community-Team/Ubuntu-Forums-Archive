---
title: "Max Memory on a 32 bit Ubuntu install on an Intel Atom D525"
date: 2011-12-29
forum: Hardware
---

### Post by Technosites on 2011-12-29
Hi there,

So I have (naively) installed Ubuntu 32 bit even though I believe my system is 64 bit, and I was wanting to upgrade the ram (from 2GB to 4GB+).

I realise that normally the 32bit limit is 4GB, but searching around it seems that if my kernal supports PAE (which Ubuntu 11.10 does right?) then I have go up to 64GB?

However, might I be limited by my mobo? The spec says 4GB max:
[http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp)
(GA-D525TUD)

cat /proc/cpuinfo gives
```

...
vendor_id	: GenuineIntel
...
model name	: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
...
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
...
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
...

```

So with the pae flag set and 36 bits physical address size I should be alright for say 8GB ram on my 32 bit system?

Thanks for the help!

---

### Post by BC59 on 2011-12-29
The problem with kernel PAE is that if you use more than 4GB of RAM, the memory above the 4GB is a little bit slower. Better make a fresh 64bit install.

---

### Post by Technosites on 2011-12-29
Okay so if I install 64 bit, I won't have any problems with motherboard limitations (if there is such a thing? )

Thanks!

---

### Post by BC59 on 2011-12-29
Run **lscpu** to be sure about the architecture of your computer.
The motherboard has a limitation on the maximum RAM permitted. Better check on Google with the type of your computer, to see what type of motherboard you have and the limitation of RAM.

---

### Post by Technosites on 2011-12-29
Ah, so Gigabyte ([http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3549#sp)) isn't lying when they its limited to 4GB :( Nevermind, thanks for the help!

---

