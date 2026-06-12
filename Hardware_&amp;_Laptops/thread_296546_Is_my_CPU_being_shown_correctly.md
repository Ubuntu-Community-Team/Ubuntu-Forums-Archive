---
title: "Is my CPU being shown correctly?"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by Dead_$partan on 2006-11-09
Hi All,

Just updated to edgy and just found out about the generic kernels.

Im a bit new to all this and the kernel chnage has thrown me a bit, I have included the kernel and cpu info below does it look Ok?

uname -a
> Linux ARAGORN 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux


cat /proc/cpuinfo(highlighted suspect area in bold)
> Linux ARAGORN 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
iain@ARAGORN:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping        : 6
**[COLOR="Red"]cpu MHz         : 1000.000[/COLOR]**
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4332.39

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping        : 6
**[COLOR="Red"]cpu MHz         : 1000.000[/COLOR]**
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4327.62


As you can see the model name reports the CPU type and speed correctly but the highlighted section states it's only running @ 1GHz, I seen this in Dapper with the 386 kernelupdating to the 686 smp kernel resolved this.  I dont want to do any kernel updates etc until im sure im reading this correctly.

Regards
Iain

---

### Post by codejunkie on 2006-11-09
this is fine when the cpu is not being used it will scale down to save power/battery life run ```
watch -n 0 cat /proc/cpuinfo
```and run some applications, compile something, or encode some mp3's or video and you'll notice it jump up while the cpu is under load but everything seems fine.

---

### Post by Dead_$partan on 2006-11-09
Thanks for the fast reply, does the kernel look accurate too for my cpu?

Thank 
Iain

---

### Post by codejunkie on 2006-11-09
> **Dead_$partan said:**
> Thanks for the fast reply, does the kernel look accurate too for my cpu?

Thank 
Iain

yes you have the right kernel, with the release of edgy there are no longer cpu specific kernels, there is only the generic kernel for most desktop/laptop pc's. i think that there may be also some server specific kernels but i haven't looked at them much but yes you do have the right kernel.

---

### Post by Dead_$partan on 2006-11-09
Once again thank you for the fast response, the amount of documentation about ubuntu was the main reason for me installing it but the support on this forum beats anything you would need to pay for, thank you once again.

Regards
Iain

---

### Post by codejunkie on 2006-11-09
> **Dead_$partan said:**
> Once again thank you for the fast response, the amount of documentation about ubuntu was the main reason for me installing it but the support on this forum beats anything you would need to pay for, thank you once again.

Regards
Iain

I'm happy to help, the community here was what made me choose Ubuntu, I must have tried at least 50 distro's but never stayed because there forums made it hard with the lack of help and there members elitist attitudes.

---

