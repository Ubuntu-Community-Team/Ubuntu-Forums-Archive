---
title: "Can my CPU support a Virtual Machine?"
date: 2018-03-10
forum: Hardware
---

### Post by tinker123 on 2018-03-10
Hi,

I wanted to do a dual boot with Windows 10, so I can use a CAC secured VPN connection to my computer at work.

Someone advised me to go the virtual machine route rather than do a dual boot.  I sent away for more RAM, installed it, installed Oracle Virtual Box 5.0.
When I went to create a new virtual machine I only saw 30 bit options in the menu.

I read on "how to geek" that if my processor doesn't have "vmx" listed in it, then I don't have what I need 

Here is my processor info:



```


Mint17QianaCinnamonBIOSF10$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 1596.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm
bogomips	: 5585.91
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 1596.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm
bogomips	: 5585.91
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

Mint17QianaCinnamonBIOSF10$
``` 


Am I out of luck with being able to use VirtualBox?

Can I use a 32 bit version of Windows 10 instead?   Again, all I want to do is VPN into my computer.

I didn't see any options for virtualization in my bios

---

### Post by #&amp;thj^% on 2018-03-10
E7400 (SLB9Y) does not support VT 
Before buying a processor, always refer to this URL: [http://processorfinder.intel.com/](http://processorfinder.intel.com/) for CPU details and it's supported features.
Sorry about that. :(

---

### Post by Yellow Pasque on 2018-03-10
> I didn't see any options for virtualization in my bios 
The feature may be named VT-x:
[https://support.hp.com/hk-en/document/c01673606](https://support.hp.com/hk-en/document/c01673606)
[https://superuser.com/a/284575](https://superuser.com/a/284575)

> Can I use a 32 bit version of Windows 10 instead?
You should be able to at least do that even if you don't have VT-x. See: [https://www.virtualbox.org/manual/ch10.html#hwvirt](https://www.virtualbox.org/manual/ch10.html#hwvirt)

---

### Post by Yellow Pasque on 2018-03-10
Consider upgrading the CPU on the cheap:  [https://www.amazon.com/Intel-E8400-3-0GHz-Processor-EU80570PJ0806M/dp/B0019NKGR4/](https://www.amazon.com/Intel-E8400-3-0GHz-Processor-EU80570PJ0806M/dp/B0019NKGR4/)

EDIT: I believe that would give you the option for VT-x if BIOS cooperates.

---

### Post by cruzer001 on 2018-03-10
> **Temüjin said:**
> Consider upgrading the CPU on the cheap:  [https://www.amazon.com/Intel-E8400-3-0GHz-Processor-EU80570PJ0806M/dp/B0019NKGR4/](https://www.amazon.com/Intel-E8400-3-0GHz-Processor-EU80570PJ0806M/dp/B0019NKGR4/)

EDIT: I believe that would give you the option for VT-x if BIOS cooperates.

 Intel® Virtualization Technology (VT-x) ‡ Yes 

[https://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB#tab-blade-1-0-4](https://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB#tab-blade-1-0-4)

---

