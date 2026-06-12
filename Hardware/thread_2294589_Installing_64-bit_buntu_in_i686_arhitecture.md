---
title: "Installing 64-bit *buntu in i686 arhitecture?"
date: 2015-09-11
forum: Hardware
---

### Post by flaymond on 2015-09-11
Hello, after doing a few research, I found that my hardware architecture actually is able to run 64-bit operating system. Unfortunately, I only have 1GB RAM and 1.73 GHz processor. Is it really okay to install 64-bit OS? After doing lscpu,  I got this -

```
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 22
Stepping:              1
CPU MHz:               1729.001
BogoMIPS:              3458.00
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K


```

and after 
[B]grep " lm " /proc/cpuinfo

[/B]
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36
 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf
 pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm

```


I want to use 64 bit OS because bunch of softwares (and updates) I'm using are going towards 64-bit, and my favorite applications only support 64-bit type architecture.

I'm currently using 32-bit Xubuntu.

What is your advice?

---

### Post by QIII on 2015-09-11
There is a chance that it will work if you can set VT-x in your BIOS.

But with one core and that little memory, Ubuntu (with Unity) is not likely to run well.

I would try Xubuntu or Lubuntu.  Download both the 32 and 64 bit versions, create live media and see which will work after setting VT-x.

---

### Post by flaymond on 2015-09-11
@QIII
Should I enable it or disable it? After doing -

```

egrep -c '(vmx|svm)' /proc/cpuinfo

```

I got 0 as the output.

and using cpu-checker, and runned kvm-ok -

```

INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used
```

Can I still install 64-bit?

---

### Post by QIII on 2015-09-11
Probably can't then.  But check your BIOS.  If available, try to *enable* it.

---

### Post by flaymond on 2015-09-11
@QIII

I try to find Vt-x if supported for my processor - [http://ark.intel.com/products/33100/Intel-Celeron-Processor-530-1M-Cache-1_73-GHz-533-MHz-FSB-Socket-P](http://ark.intel.com/products/33100/Intel-Celeron-Processor-530-1M-Cache-1_73-GHz-533-MHz-FSB-Socket-P)



and after looking at vt-x section, it's *not *supported unfortunately.

Tried checking BIOS for the vt-x, there's no even processor option.

So, to conclude, my processor is declared as *legacy *and don't have much new features supported (I'm lucky it's still can boot Xubuntu).

Anyway, is this also to conclude that I *can't *install 64-bit *buntu?

---

### Post by QIII on 2015-09-11
Pretty much.  If you try to install a 64 bit release, you will get a warning that the architecture does not support 64 bit.

---

### Post by flaymond on 2015-09-11
Thanks QIII, this discussion really helping me out whether to install it or not.

Issue solved.

---

### Post by Yellow Pasque on 2015-09-12
> **QIII said:**
> If you try to install a 64 bit release, you will get a warning that the architecture does not support 64 bit.

It looks like the CPU does support 64-bit (from Intel's ARK page) and the lm (long mode) flag. I think you assumed the OP wanted to install it in a VM based on the thread title (which is possible). I get the impression that the OP wanted to do a fresh install with 64-bit, in which case I would suggest trying to find some more RAM (hopefully fairly cheap).

---

### Post by QIII on 2015-09-12
I noticed the op-modes does include 64.  

I knew he was not using a VM, but I know that on a lot of those older ones, even if they say 64 bit operating mode, you sometimes had to set VT-x to get the installer to allow it.  I had an old single core I had to do that with.

But that's why I suggested trying both the 64 and 32 bit live media.  On i686 you still get the warning.

---

### Post by Yellow Pasque on 2015-09-12
> **QIII said:**
> even if they say 64 bit operating mode, you sometimes had to set VT-x to get the installer to allow it.

Thanks. That's a new one to me.

---

### Post by efflandt on 2015-09-13
I still have an early Athlon64 3200+ (2 GHz) from 2004, which I have not run lately, that has both 32 and 64-bit Ubuntu 10.04. At least your cpu has lahf_lm which 64-bit flash uses, but mine was lacking. But someone came up with a lahf_lm.so to use along with 64-bit libflashplayer.so, so 64-bit flash (which was beta at that time) would work on that computer. The computer had 1 GB for years, but I eventually upgraded it to 2 GB.

If you put a 64-bit live/install iso on DVD or USB and boot it, if your computer does not do 64-bit it would give some sort of error message like "Attempting to boot x64 on i686". I got that when I tried to boot 64-bit Ubuntu on an Intel 3 GHz with hyperthreading (but apparently before 64-bit). By around 2005-2006 I think most computers (except low end) could do 64-bit. A low end Compaq laptop from 2005 could not (it had Sempron 2.2 GHz which was a crippled 32-bit version of Athlon). But a 2005 work laptop and 2006 personal laptop (both with Intel 2 core 1.66 GHz) could do 64-bit.

---

### Post by flaymond on 2015-09-13
Thanks, I'll give it a try.

---

