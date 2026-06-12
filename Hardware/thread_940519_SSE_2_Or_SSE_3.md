---
title: "SSE 2 Or SSE 3"
date: 2008-10-07
forum: Hardware
---

### Post by bhoemen on 2008-10-07
can somebody tell me how to tell if my processor is SSE 2 or 3

---

### Post by grim4593 on 2008-10-07
Try:
```
sudo lshw -C cpu
```
And look under capabilities.

For example mine says:
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr **sse sse2** ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq

---

### Post by TheLions on 2008-10-07
type ```
sudo lshw
```and look at cpu section

---

### Post by bhoemen on 2008-10-09
thanks for your help

---

