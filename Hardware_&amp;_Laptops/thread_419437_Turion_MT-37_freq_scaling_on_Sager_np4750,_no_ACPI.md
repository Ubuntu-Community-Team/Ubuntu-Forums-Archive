---
title: "Turion MT-37 freq scaling on Sager np4750, no ACPI support?"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by wbeck85 on 2007-04-23
Hello, I apologize for posting yet another thread about cpu scaling, however I think that my issue is different from the typical scaling issues. This is on Ubuntu Feisty 7.04.

My problem began when I upgraded my Sager np4570 laptop (or sidewaysgraded) processor from the original Athlon 64 3200+ DTR (81W) to an energy sipping Turion 64 Mobile MT-37 (25W) processor. Socket 754.

This upgrade also required a BIOS upgrade from the std 1.01 BIOS to 2.04a, which enabled Turion support.

In Windows, I get low voltage throttling through the program RMClock, which allows me to pick my pstates and corresponding voltages.

However, in Ubuntu, I am getting absolutely zero frequency scaling support. I believe the issue is ACPI and BIOS related.

When I try to add the CPU frequency scaling monitor to my gnome panel I get the message > You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling..

A dmesg yields this: ```
will@will-laptop:~$ dmesg | grep powernow
[ 1836.066521] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-37 processors (version 2.00.00)
[ 1836.070428] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[ 1910.675484] powernow: This module only works with AMD K7 CPUs
[ 2779.957503] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-37 processors (version 2.00.00)
[ 2779.961412] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
```  lsmod: ```
will@will-laptop:~$ lsmod | grep cpu
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
will@will-laptop:~$ lsmod | grep power
cpufreq_powersave       2688  0 
``` These modules were manually loaded by me as I was trying to figure out how to fix my problem. I would like to point out that these are the only scaling related modules loaded.

If I try to manually load the module for the processor, I get ```
will@will-laptop:~$ sudo modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device 
```
Some processor information: ```
will@will-laptop:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology MT-37
stepping        : 2
cpu MHz         : 2004.650
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 4013.02
clflush size    : 64

will@will-laptop:~$ cat /proc/acpi/processor/CPU0/info 
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
will@will-laptop:~$ cat /proc/acpi/processor/CPU0/throttling 
<not supported>

```

It is my guess that the BIOS does not know how to handle this Turion processor, or perhaps that there is a miscommunication between the kernel and the BIOS? Why can the proper throttling module load? I think the device should be there. The original CPU, the Athlon64 processor works and throttles correctly.

If the BIOS and the kernel never decide to cooperate, does anyone know of a way in which I could throttle the cpu. If RMClock can do it in Windows, why can't Linux do it with some other program?

Any pointers / howto's / comments would be greatly appreciated.

~Will

---

### Post by jeromeN on 2007-04-29
I have the same problem. I got it when i updated from Dapper to Feisty
I think it is a kernel problem because if i use the 2.6.15 kernel then it is working as it was with the Dapper. I have no better solution for now than to use this kernel.

Jerome

---

### Post by Tuho on 2007-05-01
Same situation here with Turion 64x2 (TL-50) on pavilion dv9014. After upgrading from edgy to feisty, powernow-k8 module just wont load. Reckon somethings rotten with kernel, although I'm no expert on the issue.  Scaling was working before with two (800MHz/1,6GHz) steps, so this processor _is_ supported. I'm hoping this is something minor and gets fixed with next kernel upgrade.

I get a slightly different error reported> tuho@tuikutin:~$ dmesg|grep powernow
[  634.972160] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (version 2.00.00)
[  634.971462] powernow-k8: MP systems not supported by PSB BIOS structure
[  634.972710] powernow-k8: MP systems not supported by PSB BIOS structure


EDIT
Kernel packages 2.6.20-16-generic came, no change. Powernow-k8 module still reports same error (above) and wont load.

In case some devs would need this:```
tuho@tuikutin:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1607.327
cache size      : 256 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 3217.74
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1607.327
cache size      : 256 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 3220.80
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
```

---

### Post by Tuho on 2007-10-18
Update:

Frequency scaling is now working on my HP Pavilion dv9014, after upgrading to gutsy gibbon.
Many thanks to all you ubuntu devs.

---

