---
title: "cpufreq with smp kernel and amd dual core"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by luscinius on 2007-06-22
Hi

My question is related to the kernel frequency scaling governors on SMP kernels, and in particular AMD processors. With the use of the ``conservative'' one the scaling is done based the core 0 load only. If I run say the mprime stress test it uses 100% of a single core, and the load periodically gets transferred between the core 0 and core1. Thus after it gets moved to the core 1 (as it is seen from gkrellm) in 3.2 seconds (sampling_rate interval of the governor) the frequency drops down to 800MHz --- the core 1 being fully loaded and running at only 800MHz also! As soon as the mprime thread comes back to core 0 it is 1600MHz again. 

Similarly with the ``ondemand'' governor: the processes at the core 1 seem to cause no effect on it. Anothe AMD-specific issue is that the processors has only the two steps (0.8 and 1.6 GHz in my case). As it is explained here, [http://osdir.com/ml/linux.kernel.cpufreq/2006-07/msg00114.html](http://osdir.com/ml/linux.kernel.cpufreq/2006-07/msg00114.html), the ondemand governor calculates the optimal frequency and splits time between the next lower and next higher ones. Having only the two frequencies it means that it is constantly jumping between the 800 and 1600 MHz which may be not the best scenario.

The question is: is there any way to somehow trick these governors and make them respond based on the *cumulative* usage for the both cores (then one can adjust up_threshold etc.)? Or on the core used more? It seems this patch together with the conservative governor would give a reasonable regime. This question is rather kernel-related than Ubuntu specific. Of course in the worst case one can just set the fequency by hand. ;-)

Thank you in advance.

2.6.20-16-generic #2 SMP x86_64 GNU/Linux
Compaq Presario V6000 AMD Turion 64 X2 1.6 GHz

---

### Post by ukripper on 2007-06-22
Have you tried 'performance' governor?

---

### Post by luscinius on 2007-06-22
Thank you; yes, I have tried the powersave and performance governors. They just fix the clock rate at the lowest/highest values correspondingly. I am not an expert in all this; naively I would think it is something related rather to the powernow-k8 driver in the kernel. If I understand correctly (from watching gkrellm and the cpu frequency applet simultaneously an experimenting with different cpu loads/governor settings) all the decisions are made based solely on the core 0 load only. :-( I am not an expert, and writing a patch/recompiling kernel is not trivial for me. ;) 

Do the other people who have a dual core AMD cpu have the same problem?

---

### Post by ukripper on 2007-06-22
I have set my setting at performance in every case, I cant be bothered with scaling, just need performance at all times.

---

### Post by evri2 on 2007-07-04
I have the same CPU but i cannot lower my CPU clocktime.It is always 1600mhz.How did you do that?I tried both 32 and 64bit Feisty...

Laptop=HP Pavilion dv6062ea
CPU=Amd Turion Mobile X2 64 TL-52(1.6ghz)

---

