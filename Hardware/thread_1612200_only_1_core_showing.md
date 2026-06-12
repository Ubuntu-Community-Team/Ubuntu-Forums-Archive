---
title: "only 1 core showing"
date: 2010-11-02
forum: Hardware
---

### Post by i.r.id10t on 2010-11-02
This is weird.  New box, intel i5-650 cpu w/ 8 gb ram.  Installed 10.04, did updates from a local mirror, and box is *fast*.  

But /proc/cpuinfo only reports one core.  :(

The output of free indicates that all 8gb are recognized, uname reports SMP, dmidecode shows both cores.

I've narrowed it down to needing to use noapic and nolapic in order to boot.  So kernel modules.  Motherboard is an Asus P7H55-M/CSM.  

I'm thinking it is with modules required, etc.  LiveCD had the same issue. 


Ideas?

```

root@sj-desktop:~# dpkg -l | grep linux-image
ii  linux-image-2.6.32-25-generic-pae    2.6.32-25.45                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic-pae              2.6.32.25.27                                    Generic Linux kernel image
root@sj-desktop:~# cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc up arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6422.57
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

root@sj-desktop:~# uname -a
Linux sj-desktop 2.6.32-25-generic-pae #45-Ubuntu SMP Sat Oct 16 21:01:33 UTC 2010 i686 GNU/Linux
root@sj-desktop:~# 
root@sj-desktop:~# 
root@sj-desktop:~# free
             total       used       free     shared    buffers     cached
Mem:       8199176    1284400    6914776          0     163636     770364
-/+ buffers/cache:     350400    7848776
Swap:      4804600          0    4804600

```

---

### Post by dabl on 2010-11-02
> **i.r.id10t said:**
> 

 LiveCD had the same issue. 



That's not a hopeful sign.

I would be trying some other versions, and maybe even other Debian distributions, in order to isolate "what is different".  Try *buntu 10.10.

Try an aptosid Live CD: [http://www.aptosid.net/index.php?module=Content&func=view&pid=2](http://www.aptosid.net/index.php?module=Content&func=view&pid=2)

If you find one that recognizes both CPU cores, as shown with 

```
cat /proc/cpuinfo
```

then run "lsmod" and look at the kernel modules.  You're looking for the one that is not present on your Ubuntu kernel.

---

