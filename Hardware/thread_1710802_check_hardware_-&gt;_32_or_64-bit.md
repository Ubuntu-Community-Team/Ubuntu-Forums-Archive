---
title: "check hardware -&gt; 32 or 64-bit?"
date: 2011-03-20
forum: Hardware
---

### Post by cccc on 2011-03-20
hi

Howto check hardware if 32 or 64-bit?

---

### Post by JRV on 2011-03-20
```
uname -p
```

If it returns "x86_64" then it's 64 bit.
I don't have a 32 bit system running at the moment to check, but I think a 32 bit system will return "i386".

---

### Post by cccc on 2011-03-20
Thx, but I get **unknown**:```

# uname -p
unknown
# uname -i
unknown

```

---

### Post by JRV on 2011-03-20
try```
uname -a
```
if it says "x86_64" anywhere it's 64 bit.

---

### Post by cccc on 2011-03-20
/proc/cpuinfo:```

# cat /proc/cpuinfo
```
or using lshw:```

# lshw -C cpu
  *-cpu:0
       description: CPU
       product: Intel(R) Xeon(R) CPU            3050  @ 2.13GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       version: 6.15.6
       serial: 0000-06F6-0000-0000-0000-0000
       slot: PROC
       size: 2133MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 1066MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       physical id: a
       bus info: cpu@1
       version: 6.15.6
       serial: 0000-06F6-0000-0000-0000-0000
       size: 2150MHz
       capabilities: vmx ht
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          capabilities: logical

```

---

### Post by tgalati4 on 2011-03-20
Xeons come in 32-bit (older) and 64-bit (newer) flavor.  Width=64 means 64-bit data bus width, so I presume that your Xeon is a newer, 64-bit processor.

uname -a tells you what kernel you have installed--you could have a 32-bit kernel installed but still have a 64-bit CPU running.

---

### Post by cccc on 2011-03-20
Thx

---

