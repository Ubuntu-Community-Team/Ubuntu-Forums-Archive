---
title: "Ubuntu has the wrong processor?"
date: 2012-10-19
forum: Hardware
---

### Post by qedprigmosynois on 2012-10-19
So here's the deal. Im running through my conky setup  and i have it report back to me my system settings. Lo and behold it's telling me i have a Intel Pentium D .53 GHz processor and I know this isn't right.  Any advice on whether I can diagnose this further and install appropriate ware to mend this?

Thanks

---

### Post by ahallubuntu on 2012-10-19
Just because Ubuntu is incorrectly reporting the exact name of your CPU doesn't mean anything is wrong or that you are suffering any performance losses.

Please open a terminal and show the results from running this:

```
sudo lshw -C CPU
```

What are the real name/specs of CPU you are using?

---

### Post by qedprigmosynois on 2012-10-19
So what the terminal spits out: 
```
  *-cpu:0                 
       description: CPU
       product: AMD Turion Dual-Core RM-72
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: cpu@0
       version: 15.3.1
       slot: Socket A
       size: 525MHz
       capacity: 2100MHz
       width: 64 bits
       clock: 133MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate lbrv svm_lock nrip_save cpufreq
  *-cpu:1
       physical id: 5
       bus info: cpu@1
       version: 15.3.1
       size: 525MHz
       capacity: 525MHz
       capabilities: cpufreq
  *-processor UNCLAIMED
       description: Co-processor
       product: MCP78S [GeForce 8200] Co-Processor
       vendor: NVIDIA Corporation
       physical id: 1.3
       bus info: pci@0000:00:01.3
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master
       configuration: latency=0 maxlatency=1 mingnt=3
       resources: memory:c0080000-c00fffff

```

And the real specs are: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01634455&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3860190](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01634455&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3860190)

The difference is quite noticeable, i dunno if it's ubuntu or if it's because the processor was malfunctioned in the first place

---

### Post by grahammechanical on 2012-10-19
Why are you saying the Ubuntu has got it wrong? You are using Conky.

The product specification says this:

> AMD Turion X2 RM-72 Dual-Core Mobile Processor

and this

> 2.10 GHz

Ubuntu (sudo lshw -C cpu) says this

> AMD Turion Dual-Core RM-72

and this

> capacity: 2100MHz

That is the listing for cpu0. Now compare it with the listing for cpu1. You will see a difference and that is what Conky is seeing and guessing to be a Pentium D.

Regards.

---

### Post by qedprigmosynois on 2012-10-19
hmm i still don't see the difference. I see it but what's the difference between its current capactiy and overall capacity?
but ok, at least i understand nothing needs to be fixed. Thanks.

---

### Post by Cheesemill on 2012-10-20
Can you post your .conkyrc and a screenshot so we can actually see what's going on please.

---

### Post by Yellow Pasque on 2012-10-20
> **qedprigmosynois said:**
> hmm i still don't see the difference. I see it but what's the difference between its current capactiy and overall capacity?
but ok, at least i understand nothing needs to be fixed. Thanks.
When the CPU is idle, it downclocks to save power. That's probably what's confusing you.
Run:
```
cpufreq-info
```

---

