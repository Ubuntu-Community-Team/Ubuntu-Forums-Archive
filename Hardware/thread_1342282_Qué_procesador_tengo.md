---
title: "Qué procesador tengo?"
date: 2009-11-30
forum: Hardware
---

### Post by Criminel on 2009-11-30
Se supone que mi PC vino con un simple procesador AMD Sempron de 32 bits.
El resultado de buscar en la máquina me dá esto:
  description: CPU
          product: AMD Processor model unknown
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.3
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy ts fid vid ttp tm stc cpufreq

¿Qué procesador tengo finalmente?

Gracias

---

### Post by Mauro22 on 2009-11-30
fijate instalando el paquete cpuid, te da más informacion. Por ejemplo, con el mio:

```
Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 000006fd:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 15 - 
Extended model 0
Stepping 13
Reserved 0

Extended brand string: "Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz"
CLFLUSH instruction cache line size: 8
Initial APIC ID: 1
Hyper threading siblings: 2
```

---

