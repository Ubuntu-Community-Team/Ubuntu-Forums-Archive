---
title: "CPU power management"
date: 2008-10-28
forum: Hardware
---

### Post by simion314 on 2008-10-28
Hi all. It seams that my laptop doesn't have a CPU power management driver.
More info:

kernel 2.6.27-7-generic

```

simi@laptop:~$ cpufreq-info          
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.             
analyzing CPU 0:                                              
  no or unknown cpufreq driver is active on this CPU   

```

About my laptop model is an ASUS X51 and the windows driver cd has an application for CPU management, i need some help to find out if i can find some driver and set it up (my old laptop worked out of the box and when it was idle it automaticaly lowed the CPU freqvency from 1200 to 800 that maked the fan stop or run slower)

CPU  info
```

simi@laptop:~$ cat /proc/cpuinfo                              
processor       : 0                                           
vendor_id       : GenuineIntel                                
cpu family      : 6                                           
model           : 22                                          
model name      : Intel(R) Celeron(R) CPU          550  @ 2.00GHz
stepping        : 1                                              
cpu MHz         : 1995.108                                       
cache size      : 1024 KB                                        
fdiv_bug        : no                                             
hlt_bug         : no                                             
f00f_bug        : no                                             
coma_bug        : no                                             
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm      
bogomips        : 3990.21                                                                                         
clflush size    : 64                                                                                              
power management:                                                                                                 

simi@laptop:~$ cat /proc/meminfo
MemTotal:      1942664 kB       
MemFree:       1064036 kB       
Buffers:         48508 kB       
Cached:         389260 kB       
SwapCached:          0 kB       
Active:         515476 kB       
Inactive:       271352 kB       
HighTotal:     1048224 kB       
HighFree:       300204 kB       
LowTotal:       894440 kB       
LowFree:        763832 kB       
SwapTotal:     1052248 kB
SwapFree:      1052248 kB
Dirty:             108 kB
Writeback:           0 kB
AnonPages:      349112 kB
Mapped:         107708 kB
Slab:            37260 kB
SReclaimable:    23504 kB
SUnreclaim:      13756 kB
PageTables:       3460 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   2023580 kB
Committed_AS:   664700 kB
VmallocTotal:   110584 kB
VmallocUsed:     38984 kB
VmallocChunk:    70860 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:      8192 kB
DirectMap4M:    909312 kB
simi@laptop:~$

```

Any help is welcome.

P.S. Please excuse my bad english

---

