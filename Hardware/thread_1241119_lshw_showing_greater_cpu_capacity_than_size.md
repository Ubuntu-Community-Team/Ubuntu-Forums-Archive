---
title: "lshw showing greater cpu capacity than size"
date: 2009-08-15
forum: Hardware
---

### Post by awakenDeepBlue on 2009-08-15
sudo lshw -class cpu
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) 64 Processor 2800+
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Athlon(tm) 64 Processor 2800+
       slot: Socket 754
       **size: 1800MHz**
       **capacity: 3GHz**
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up rep_good cpufreq

So what does this mean.  I know the processing speed of this computer is 1.8Ghz, but why is the capacity listed as 3Ghz?  Does this mean that my processor is capable of overclocking to 3Ghz safely?

---

### Post by swudee on 2009-08-16
A quick Google on the CPU suggests it is a 1.8 GHz processor.

[http://www.pcper.com/article.php?aid=33&type=expert](http://www.pcper.com/article.php?aid=33&type=expert)

Here's a quick run down of the features of the Athon 64 2800+ processor being reviewed here.

    * Model: Athlon 64 2800+
    * Frequency: 1.8 GHz
    * L1 Cache: 128 KB
    * L2 Cache: 512 KB
    * Voltage: 1.5v
    * Process: 0.13 micron
    * Socket: Socket 754
    * Packaging: OEM only

I can't even guess at what the 3 GHz is.
It may over clock to that if it had adequate cooling, but unless you are really into over clocking I wouldn't try. You would be best to check with an over clocking forum about that.

---

