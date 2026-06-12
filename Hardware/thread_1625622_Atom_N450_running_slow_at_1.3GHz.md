---
title: "Atom N450 running slow at 1.3GHz"
date: 2010-11-19
forum: Hardware
---

### Post by phraemer on 2010-11-19
Hi,

I have a HP Mini 5102 running 10.10 AMD64

Under load I just can't seem to get the cpu to go faster than 1.3GHz

Here's /proc/cpuinfo

```
@ubuntu:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3325.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3325.30
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

```

Starting two "cat /dev/urandom > /dev/null" only brings the speed up to...

cpu MHz		: 1333.000

Is this just being falsely reported or something else?

thanks,
James

---

### Post by phraemer on 2010-11-20
Nobody can confirm this one? On any n450 based machine?

---

### Post by Vangelis on 2011-02-23
Hey James,

I wonder if you ever got this sorted out. I've just bought the same machine and it seems to run a little slow for my liking. I'd like to set it up to a constant 1.66GHz and be done with it!

Does anyone else know how to do this?

Thanks,

Vangelis

---

### Post by phraemer on 2011-02-23
sorry no, never figured this out :/

---

### Post by fjgaude on 2011-02-23
This might work. Add the CPU Frequency Scaling Monitor to the panel. Then set it to Performance from the normal Ondemand setting. You might have dual-core Atom so Add two the Monitors and set one to 0 and the other to 1.

---

### Post by khartahk on 2011-04-27
Adding processor.ignore_ppc=1 to /etc/default/grub where it says GRUB_CMDLINE_LINUX_DEFAULT fixes the problem of not beeing able to set 1.67GHz to the atom N450 CPU on HP Mini 5102.

The line then looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.ignore_ppc=1"

Found the sollution here: [https://bbs.archlinux.org/viewtopic.php?pid=782603](https://bbs.archlinux.org/viewtopic.php?pid=782603)

Hope this helps anyone.

---

### Post by phraemer on 2011-04-27
that works great.

thanks!

---

