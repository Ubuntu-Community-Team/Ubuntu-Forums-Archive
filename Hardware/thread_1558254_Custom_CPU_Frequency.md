---
title: "Custom CPU Frequency"
date: 2010-08-21
forum: Hardware
---

### Post by Keith Cancel on 2010-08-21
Hello I have a question I have CPU Frequency Scaling enabled on my laptop but the available frequency's do not fit my needs since my fastest clock speed makes my laptop run too hot the same applies to the second and my last and slowest is too slow how can I specify a custom Frequency for my CPU so I can have some decent performance when trying to convert files but not let my CPU hit temperatures that are too hot out so lets say I want to set my CPU too 1400MHZ but its not on the list how could I do that?

---

### Post by Keith Cancel on 2010-08-22
Bump.

---

### Post by psusi on 2010-08-22
Not possible.  The available frequencies are provided by the hardware.

---

### Post by corrytonapple on 2010-08-22
Since it is a laptop over-clocking is not possible. Over clocking is for high end laptops. Under-clocking is possible.

---

### Post by cascade9 on 2010-08-22
> **psusi said:**
> Not possible.  The available frequencies are provided by the hardware.

It might not be possible with the hardware Keith Cancel has, but underclocking is more than possible..... 

> **corrytonapple said:**
> Since it is a laptop over-clocking is not possible.

Wrong. Its not as common as being able to under/overclock on desktops, but there are quite a few laptops which you can play with the CPUs speeds, etc..

---

### Post by corrytonapple on 2010-08-22
> **cascade9 said:**
> It might not be possible with the hardware Keith Cancel has, but underclocking is more than possible..... 



Wrong. Its not as common as being able to under/overclock on desktops, but there are quite a few laptops which you can play with the CPUs speeds, etc..
Yes, understood. The gaming laptops and high end ones you can over-clock. But yes true, Under-clocking is possible.
System Specs please.

---

### Post by psusi on 2010-08-22
Overclocking is done by slightly altering the system clock frequency on motherboards that allow you to do so, which virtually no laptops do.  The OP is asking about the dynamic performance frequency scaling, which alters the processor voltage and multiplier at runtime.  These settings come from what the processor and motherboard support, and can not be changed.

---

### Post by Keith Cancel on 2010-08-29
Dang.

---

### Post by Yellow Pasque on 2010-08-29
There is a CLI tool for custom undervolting/clocking of AMD k8-based CPU's. I don't remember the name of it though. There are also patches for the powernow-k8 module.

Oh, and post the output of cat /proc/cpuinfo

---

### Post by Docet on 2012-09-13
Hey,

I wandered on Google and I found how you can do it on Intel CPUs. It's not so easy, but you can take a look if you care!

[http://linuxsolver.blogspot.it/2012/09/how-to-customize-cpu-frequency-steps.html](http://linuxsolver.blogspot.it/2012/09/how-to-customize-cpu-frequency-steps.html)

Cheers

---

