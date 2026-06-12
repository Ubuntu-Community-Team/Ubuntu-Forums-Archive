---
title: "Core 2 Duo: Only 1 CPU Recognized, SMP enabled, Feisty"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by alfzer0 on 2007-05-28
Hi all,

I've been using Ubuntu for the better part of 3 years now, and this is the first problem thats got me completely stumped :confused:
I've just set up a new machine w/ a FoxConn G9657MA-8KS2HG965 mobo (G965 chipset) and a Core 2 Duo E6600 running Feisty w/ all current upgrades.
Problem is, Feisty is only recognizing 1 of the CPUs even though I'm using an SMP kernel.  Here's the output so you can take a look...

```

user@mediamonkey:~$ uname -a
Linux mediamonkey 2.6.20-16-lowlatency #2 SMP PREEMPT Wed May 23 01:49:41 UTC 2007 i686 GNU/Linux

```

```

user@mediamonkey:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2394.108
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4790.03
clflush size    : 64
```

I've tried enabling/disabling APIC and ACPI via the BIOS and kernel boot arguments.
Every kernel I've tried doesn't work (2.6.20-15-generic & lowlatency, 2.6.20-16-generic & lowlatency).
I'm also using the "all_generic_ide" kernel boot argument as a workaround to the SATA problems this board has with the current kernel.
Before someone suggests it, I don't want to install the 64bit Ubuntu, at this point I think it's more headache than what its worth.

Anyone have any ideas that could help me out? [-o<
Thanks in advance!
-Jeff

---

### Post by nss0000 on 2007-05-28
BigAL:

Consider again Ux64.

AFAIK only JAVA_plugin fails on DAPPERx64. I'm running Dx64 now without (other) issues on AMD5400 kit. It seems v7.x is still a bit raw. Better to deal with a malicious mallard than a frivolous faun.

nss
****

---

### Post by Twintop on 2007-05-29
I had a similar issue with a FoxConn motherboard (Athlon X2 Socket 939, not Core 2 Duo) where only one core was being recognized. For me, upgrading the BIOS fixed the problem. When was this motherboard manufactured? It could be it was released before multi core processors were standard for the socket type.

---

