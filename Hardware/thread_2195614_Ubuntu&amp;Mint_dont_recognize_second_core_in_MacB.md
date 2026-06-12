---
title: "Ubuntu&amp;Mint dont recognize second core in MacBook 5,2"
date: 2013-12-25
forum: Hardware
---

### Post by realmarra on 2013-12-25
Hi there.
I was running Ubuntu on my MacBook 5,2 and it ran pretty good.
The only thing that was kinda wrong was the fact that it didnt seem to recognize my second core.
The MacBook has an Intel Core 2 Duo P7450 2,13Gh/z x2 built in.
Ubuntu just ran on one single core.
Then one time, i was restoring my root-password using a live-cd of Mint, and i saw that it DID run on 2 cores.
I then installed Mint 16 and after a day of dual-core-power, it just...  stopped "seeing" the second core.
No idea why, i just made an System Update and then suddenly there were just one core.

Can anyone help me? I am currently learning a couple of Programming Languages, and i need as much power as i can get.

Thank you for your help



System info:

OS: Linux Mint Cinnamon 64-bit
Kernel: 3.11.0-12-generic
Processor: Intel Core 2 Duo P7450 2,13Gh/z x2
RAM: 1,7GiB
HDD: 500 GB
Graphics Card: GeForce 9400M G

CPUINFO:

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1596.000
cache size    : 3072 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 4255.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by realmarra on 2014-01-06
bump

---

### Post by sudodus on 2014-01-06
Welcome to the Ubuntu Forums :-)

I don't understand why Mint first showed 2 cores and then only one core. I think all currently supported kernels of Ubuntu have SMP, But I know that there are several linux kernels. Some of them have SMP, which means that they can manage several cores, and other kernels don't have SMP, and can only manage one core. Sometimes SMP is part of the output of this command

```
uname -a
```

Please post the output of the command and maybe it will help us giving better advice.

Anyway, I think it is a problem with the linux kernel and your hardware. Probably the update in Mint made it switch to another kernel. If you still have the old kernel, you can select it in the grub menu and check if it finds both cores.

---

### Post by tgalati4 on 2014-01-06
Sometimes one core will shut down if there is a problem with cache or RAM.  Because the L1 and/or L2 is shared between the cores, a conflict or error will cause one core to shut down.  This should show up as an error in dmesg:

```
dmesg | tail -100
```

or in syslog:

```
less /var/log/syslog
less /var/log/syslog.1
```

---

