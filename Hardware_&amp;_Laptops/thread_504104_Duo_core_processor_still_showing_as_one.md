---
title: "Duo core processor still showing as one"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by travist120 on 2007-07-18
I installed the SMP kernel for my Dual core processor. And yet, I'm still having issues on it, it doesn't seem to detect that there are actually 2 cores.

this is a geekbench score
```

System Information
  Platform:                  Linux x86 (32-bit)
  Compiler:                  GCC 4.1.1 20061011 (Red Hat 4.1.1-30)
  Operating System:          Linux 2.6.20-16-386 i686
  Model:                     Linux PC (Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz)
  Motherboard:               Unknown Motherboard
  Processor:                 Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
  Processor ID:              GenuineIntel Family 6 Model 15 Stepping 6
  Logical Processors:        1
  Physical Processors:       1
  Processor Frequency:       1.00 GHz
  L1 Instruction Cache:      0.00 B
  L1 Data Cache:             0.00 B
  L2 Cache:                  0.00 B
  L3 Cache:                  0.00 B
  Bus Frequency:             0.00 Hz
  Memory:                    1011 MB
  Memory Type:               N/A
  SIMD:                      1

```

---

### Post by travist120 on 2007-07-18
I still can't find anything. I've gone into my BIOS to be sure that dual core was enabled by the way I still haven't figured out from google or from here on why SMP refuses to see that I have 2 cores. Not just one.

---

### Post by ubanchaos on 2007-07-18
what linux ru running on and ru dual booting

---

### Post by travist120 on 2007-07-19
Ubuntu 7.04 and I am not dual booting.

---

### Post by tgm4883 on 2007-07-19
output of
cat /proc/cpuinfo

---

### Post by travist120 on 2007-07-19
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.164
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3999.23
clflush size    : 64

```

---

### Post by tgm4883 on 2007-07-19
Output of
uname -a

---

### Post by Suzan on 2007-07-19
What SMP-Kernel do you mean?

Since Edgy the right kernel for both normal and duo core processors is the generic-kernel, not the -386 kernel!

Please install the packages "linux-generic" which installs  the right, actual kernel and the fitting kernel-headers for you.

---

### Post by travist120 on 2007-07-19
Linux travis-laptop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

is what uname -a shows me. And I do have the Generic Kernels installed. I just want to be able to use both of my cores

---

### Post by Suzan on 2007-07-19
So you use the 386-kernel, which DON'T support two kernels!

Start with the generic-kernel an you will be happy! ;-)

---

### Post by tgm4883 on 2007-07-19
> **travist120 said:**
> Linux travis-laptop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

is what uname -a shows me. And I do have the Generic Kernels installed. I just want to be able to use both of my cores

You may have the generic kernels installed, but your using the i386 kernels which don't have SMP support.  You may want to check again and check grub when you boot to see which kernel it is using.

---

### Post by xghstst0riesx on 2007-07-24
I still can't get my 2 processors to show up in Feisty. I have the generic kernel installed and judging from my /etc/boot/menu.lst it is booting it as well. Is there anything else that may be causing this?

---

### Post by steveneddy on 2007-07-24
> **xghstst0riesx said:**
> I still can't get my 2 processors to show up in Feisty. I have the generic kernel installed and judging from my /etc/boot/menu.lst it is booting it as well. Is there anything else that may be causing this?

Yeah, PEBKAC.

---

### Post by tgm4883 on 2007-07-24
> **xghstst0riesx said:**
> I still can't get my 2 processors to show up in Feisty. I have the generic kernel installed and judging from my /etc/boot/menu.lst it is booting it as well. Is there anything else that may be causing this?

output of 
uname -a

---

