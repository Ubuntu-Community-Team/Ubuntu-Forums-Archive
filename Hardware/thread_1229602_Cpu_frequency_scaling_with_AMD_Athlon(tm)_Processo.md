---
title: "Cpu frequency scaling with AMD Athlon(tm) Processor L110 ?"
date: 2009-08-02
forum: Hardware
---

### Post by diffy on 2009-08-02
Hi,

I tried to enable the frequency scaling on my laptop with this AMD processor, but I didn't found anything on the web now which work for my distribution/ processor.
```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 124
model name    : AMD Athlon(tm) Processor L110
stepping    : 2
cpu MHz        : 1197.081
cache size    : 512 KB
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch
bogomips    : 2394.16
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

``````

Linux 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

```I tried to follow [that thread]("http://ubuntuforums.org/showthread.php?t=248867") but I can't load any mentioned modules, I only have the errors like
```

sudo modprobe powernow-k8
FATAL: Module powernow_k8 not found.

```does anybody have some clues for me ?

Thanks
David

---

### Post by priegog on 2009-10-26
I am very interested in this too. I wouldn't normally care about something like scaling, but seeing that this processor is intended for netbook-like (depending on your definition of netbook) laptops, this becomes a REALLY big issue. I need to know in a reasonable amount of time (a little more than a week) because if there doesn't seem to be a solution in the horizon I might be taking it back to the store. It never ocurred to me that I would have to keep an eye out for processor compatibility on linux. video card, wireless card, onboard camera and sound card sure, but processor? never.
Anyways, thanks

---

### Post by lordofwinds on 2009-10-29
Yeah, it's really trouble.
I hope this promlem can be resolved soon.

---

