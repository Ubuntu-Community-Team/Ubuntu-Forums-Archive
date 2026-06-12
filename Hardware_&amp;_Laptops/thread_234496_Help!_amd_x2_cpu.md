---
title: "Help! amd x2 cpu"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2006-08-11
I just replaced my amd 64bit 3200 cpu with the amd 64bit x2 3800 cpu on the same motherboard (asus 8na), and the second core isn't showing up. It could be a problem with my bios as well, because it says:

AMD Hammer family processor - Model Unkown

when I run cat /proc/cpuinfo
and I see it in my bios as well.

Anybody have any experience with this??

---

### Post by Jagot on 2006-08-11
You may just need to install the SMP kernel.  The default kernel that comes with Ubuntu does not support multiple processors/dual-core/hyper threading etc.

```
sudo aptitude update
sudo aptitude install linux-amd64-k8-smp
```

---

### Post by william_nbg on 2006-08-11
I'm running the K7 kernel now. I've seen on other threads that it supports hyper threading.

---

### Post by william_nbg on 2006-08-11
Here's my cat /proc/cpuinfo if it helps.

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 1
cpu MHz         : 2010.514
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4025.08

---

### Post by John.Michael.Kane on 2006-08-11
william_nbg right now your running the 32 bit kernel. in which case you should use the smp kernel your cup is not hyper thread based so ignore that. you need to find the k7-smp kernel or install ubuntu 64bit and use the k8-smp kernel. also have you bothered to update your bios since it would seem it's reading your cpu as a single core cpu.

---

### Post by william_nbg on 2006-08-12
> **SD-Plissken said:**
> william_nbg right now your running the 32 bit kernel. in which case you should use the smp kernel your cup is not hyper thread based so ignore that. you need to find the k7-smp kernel or install ubuntu 64bit and use the k8-smp kernel. also have you bothered to update your bios since it would seem it's reading your cpu as a single core cpu.

Yes, I want to run the 32 bit kernel, though, I want my second core. I read in another thread that the K7 now has smp built in - even had a screenshot showing both kernels running with that kernel.

I'm pretty sure it's the bios as well, but a bios flash is one of those odd things I've never done before and makes me nervous.

---

### Post by william_nbg on 2006-08-12
I am now a happy camper!!!:D 

It was the bios - just needed a little flash.

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2015.161
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d now pni lahf_lm cmp_legacy
bogomips        : 4034.51

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2015.161
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d now pni lahf_lm cmp_legacy
bogomips        : 4030.29

---

