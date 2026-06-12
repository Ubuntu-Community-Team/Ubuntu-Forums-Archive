---
title: "Duda si mi Procesador es 64 o 32 bits"
date: 2010-10-20
forum: Hardware
---

### Post by cellini on 2010-10-20
Buenos dias a todos, aca voy con una pregunta muy tonta seguramente:

No se bien si mi Procesador es 32 o 64 bits, ya que cuando hago el:

trochey@cuscusita:~$ lshw -C cpu

me tira:

  ***-cpu                   **
       product: AMD Athlon(tm) II X2 245 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 5
       bus info: cpu@0
       version: 15.6.2
       size: 800MHz
       capacity: 800MHz
       [COLOR=Red]**width: 64 bits**[/COLOR]
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq
  ***-processor UNCLAIMED**
       description: Co-processor
       product: MCP78S [GeForce 8200] Co-Processor
       vendor: nVidia Corporation
       physical id: 1.3
       bus info: pci@0000:00:01.3
       version: a2
       [COLOR=Red]**width: 32 bits**[/COLOR]
       clock: 66MHz
       capabilities: bus_master
       configuration: latency=0 maxlatency=1 mingnt=3
       resources: memory:fcf80000-fcffffff

Me podrian aconsejar si debo o no cambiar la arquitectura de mi SO, ya que es:

trochey@cuscusita:~$ uname -a

Linux ubuntu-desktop 2.6.31-22-generic #65-Ubuntu SMP Thu Sep 16 15:48:58 UTC 2010 [COLOR=Red]**i686**[/COLOR] GNU/Linux

i686 = 32 bits

Bueno, muchas pero muchas gracias!

Manuel desde La Plata

---

