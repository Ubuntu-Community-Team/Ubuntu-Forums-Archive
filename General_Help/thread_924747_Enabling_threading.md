---
title: "Enabling threading"
date: 2008-09-19
forum: General Help
---

### Post by Pro-reason on 2008-09-19
I have access to two computers.  My main one is supposed to be more powerful, and yet it is often sluggish.

I recently ran the lrzip command on each computer, and noticed the following difference:

Primary computer:
```
Threading is DISABLED. Number of CPUs detected: 1
```

Secondary computer:
```
Threading is ENABLED. Number of CPUs detected: 2
```

This might explain why my main machine is often slower despite superior hardware.  Why is only half of my dual-core processor working?  How can I tweak this?

---

### Post by Pro-reason on 2008-09-20
Primary machine:
```
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl est tm2 cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0

```

Secondary machine:
```

     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: J2E1
          size: 2800MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0

```

---

