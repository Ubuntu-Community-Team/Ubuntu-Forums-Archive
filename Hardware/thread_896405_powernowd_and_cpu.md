---
title: "powernowd and cpu"
date: 2008-08-21
forum: Hardware
---

### Post by radtek on 2008-08-21
My cpu doesn't seem to support it based on lshw but this is the output for both:

```
 *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          slot: Socket M2/S1G1
          size: 1800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae
 mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2
 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16
 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp
 tm stc 100mhzsteps cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
```

and

```
radtek@laptop:~$ sudo powernowd -v
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Settings:
powernowd:   verbosity:        1
powernowd:   mode:             1     (AGGRESSIVE)
powernowd:   step:           100 MHz (100000 kHz)
powernowd:   lowwater:        20 %
powernowd:   highwater:       80 %
powernowd:   poll interval: 1000 ms
powernowd: about to return count = 2
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
powernowd:   cpu0: 800Mhz - 1800Mhz (3 steps)
powernowd:      step1 : 1800Mhz
powernowd:      step2 : 1600Mhz
powernowd:      step3 : 800Mhz
powernowd:   cpu1: 800Mhz - 1800Mhz (3 steps)
powernowd:      step1 : 1800Mhz
powernowd:      step2 : 1600Mhz
powernowd:      step3 : 800Mhz


```

Is it working?

---

