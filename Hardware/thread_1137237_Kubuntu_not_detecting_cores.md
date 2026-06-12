---
title: "Kubuntu not detecting cores"
date: 2009-04-25
forum: Hardware
---

### Post by Kazagistar on 2009-04-25
The best way to describe my problem is to show the output of cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping        : 4
cpu MHz         : 2653.192
cache size      : 8192 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5306.38
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

Note: the i7 processor has 4 cores, each with hyper-threading, so really, I should be seeing 8 cores.

I only have 2 leads... First, I have to have the "acpi=off noapic nolapic" parameters in my boot-loader so that the kernel does not panic right on startup. Also, my motherboard is the "EVGA X58 SLI" which has quite a few over-clocking and similar features, and while I have updated to the latest firmware release, it still could be considered beta-ish quality.

I made a custom-built computer with a lot of newer components, so I was kinda asking for problems, but if anyone could help me out or even share their thoughts on what might be up, I would be very grateful.

---

### Post by Kazagistar on 2009-04-28
*bump?*

---

### Post by krazyd on 2009-04-28
> **Kazagistar said:**
> (...)
Note: the i7 processor has 4 cores, each with hyper-threading, so really, I should be seeing 8 cores.

I only have 2 leads... First, I have to have the "acpi=off noapic nolapic" parameters in my boot-loader so that the kernel does not panic right on startup. Also, my motherboard is the "EVGA X58 SLI" which has quite a few over-clocking and similar features, and while I have updated to the latest firmware release, it still could be considered beta-ish quality.

I made a custom-built computer with a lot of newer components, so I was kinda asking for problems, but if anyone could help me out or even share their thoughts on what might be up, I would be very grateful.
The problem is that your setup had some brand new hardware, and the kernel shipped with Jaunty doesn't recognise it. Basically, you'll have to wait for the newer kernel in 9.10 for all the parameters of your hadware to be shown. It'll probably fix the panic on startup too.
Your MB's chipset and the *oldest *i7 was released in November 08 and Jaunty's kernel was only released in December 08.

---

### Post by Kazagistar on 2009-04-29
If I compile some newer, testing kernel from the repositories, there is a good chance it will work? You know, to kill time until it is supported in 9.10?

Should I try another distribution, perhaps? Something less stable/predictable/easy that has rolling releases?

---

### Post by krazyd on 2009-04-29
Maybe - I haven't compiled a kernel myself ;)

Try Arch.. I've heard some good things about the Chakra Project.
[http://chakra-project.org/](http://chakra-project.org/)

---

