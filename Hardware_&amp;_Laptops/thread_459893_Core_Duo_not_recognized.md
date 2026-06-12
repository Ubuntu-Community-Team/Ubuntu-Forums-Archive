---
title: "Core Duo not recognized"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by bated_breath on 2007-05-31
Hi,

I am using Edgy which is installed on a USB drive from which I boot and  have succesfully been using it this way for about a year .  I recently got a new Core Duo laptop and tried booting from the self-same USB drive which worked fine except that when I look at system monitor I cannot see the second processor.

I have read many threads on the subject and they all suggest that you need SMP kernel installed.  I have installed this using Synaptic but it does not seem to have any effect.

uname -a : Linux gauteng 2.6.17-11-386 #2 Fri May 18 23:37:00 UTC 2007 i686 GNU/Linux

cat /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3993.35


Any help much appreciated.

---

### Post by bated_breath on 2007-05-31
I have managed to get it working or I should say it was working all the time.  After I installed the generic-linux-kernel I restarted thinking that the Grub would pick it up and boot using this generic kernel and did not realise that I had to select it.  Now that I have selected this option from the grub boot menu it is working fine.

---

### Post by stchman on 2007-05-31
> **bated_breath said:**
> Hi,

I am using Edgy which is installed on a USB drive from which I boot and  have succesfully been using it this way for about a year .  I recently got a new Core Duo laptop and tried booting from the self-same USB drive which worked fine except that when I look at system monitor I cannot see the second processor.

I have read many threads on the subject and they all suggest that you need SMP kernel installed.  I have installed this using Synaptic but it does not seem to have any effect.

uname -a : Linux gauteng 2.6.17-11-386 #2 Fri May 18 23:37:00 UTC 2007 i686 GNU/Linux

cat /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3993.35


Any help much appreciated.

I believe the -386 kernels do not support SMP.  Switch to the -generic version.

---

