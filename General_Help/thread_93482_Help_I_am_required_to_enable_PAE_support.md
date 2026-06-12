---
title: "Help? I am required to enable PAE support"
date: 2005-11-22
forum: General Help
---

### Post by domino on 2005-11-22
Can someone please help with my confusion? I need to enable PAE support on my kernel and I don't know if it is enabled or not. I know my processor supports this feature.

```
2.6.12-9-686-smp
```
```
~@linux:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 3298.135
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6537.21

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 3298.135
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6586.36
```

---

### Post by JaS on 2005-11-22
I need to find out about PAE enabled Kernel also.
Hi Domino :)

---

### Post by domino on 2005-11-22
:D Hi JaS! It's a small world ain't it?

I tried to pass the switches in grub's menu.lst
```

kernel		/vmlinuz-2.6.12-9-686-smp root=/dev/hda7 ro quiet splash enable-pae ht=on
```

I looked in the logs after a successfull but and I don't se any changes. The only change I saw was that it doesn't state that HT isn't ennable anymore. As a matter of fact, it's says nothing about HT enabled or disabled. Is that good or bad?

---

