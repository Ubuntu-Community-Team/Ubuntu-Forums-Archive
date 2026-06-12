---
title: "amd radeon hd8570 not working with sober"
date: 2024-11-09
forum: Hardware
---

### Post by harji on 2024-11-09
Hello everyone,
I am trying to run sober for roblox on my 10 years desktop (for my son) as I ditched Windows.I followed some online instructions for this but Its not working with sober. Not a geek here. Please see imgur images for my system info.
[https://imgur.com/a/6bLrsbq](https://imgur.com/a/6bLrsbq)
I followed these links for instructions.[https://wiki.debian.org/AtiHowTo#AMDGPU.2FVulkan_on_older_cards](https://wiki.debian.org/AtiHowTo#AMDGPU.2FVulkan_on_older_cards)



 >    @hp-desktop:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Oland [Radeon HD 8570 / R5 430 OEM / R7 240/340 / Radeon 520 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
       resources: irq:42 memory:c0000000-cfffffff memory:fea00000-
fea3ffff ioport:e000(size=256) memory:c0000-dffff


@hp-desktop:~$ lsmod | grep amd
amdgpu              17104896  0
amdxcp                 12288  1 amdgpu
drm_exec               12288  1 amdgpu
gpu_sched              61440  1 amdgpu
drm_buddy              20480  1 amdgpu
edac_mce_amd           28672  0
drm_suballoc_helper    16384  2 amdgpu,radeon
drm_ttm_helper         12288  2 amdgpu,radeon
ttm                   110592  3 amdgpu,radeon,drm_ttm_helper
drm_display_helper    237568  2 amdgpu,radeon
i2c_algo_bit           16384  2 amdgpu,radeon
video                  73728  2 amdgpu,radeon

@hp-desktop:~$ sudo dmesg | grep -i amdgpu
[   10.804578] [drm] amdgpu kernel modesetting enabled.
[   10.804825] amdgpu: Virtual CRAT table created for CPU
[   10.804855] amdgpu: Topology: Add CPU node



GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.cik_support=0 amdgpu.cik_support=1"

GRUB_CMDLINE_LINUX=""


#GRUB_DISABLE_OS_PROBER=false


#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


#GRUB_TERMINAL=console


#GRUB_GFXMODE=640x480


#GRUB_DISABLE_LINUX_UUID=true

#GRUB_DISABLE_RECOVERY="true"

#GRUB_INIT_TUNE="480 440 1"

System info

@hp-desktop:~$ uname
Linux

@hp-desktop:~$ uname -n
hp-desktop

@hp-desktop:~$ uname -v
#48-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 14:04:52 UTC 2024

@hp-desktop:~$ uname -r
6.8.0-48-generic

@hp-desktop:~$ uname -m
x86_64

@hp-desktop:~$ uname -a
Linux hp-desktop 6.8.0-48-generic #48-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 14:04:52 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Architecture:             x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          48 bits physical, 48 bits virtual
  Byte Order:             Little Endian
CPU(s):                   4
  On-line CPU(s) list:    0-3
Vendor ID:                AuthenticAMD
  Model name:             AMD FX(tm)-770K Quad Core Processor
    CPU family:           21
    Model:                48
    Thread(s) per core:   2
    Core(s) per socket:   2
    Socket(s):            1
    Stepping:             1
    Frequency boost:      enabled
    CPU(s) scaling MHz:   43%
    CPU max MHz:          3500.0000
    CPU min MHz:          1400.0000
    BogoMIPS:             6987.18
    Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_g
                          ood nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy extapic cr8_legacy
                           abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc cpb hw_pstate ssbd vmmcall fsgsb
                          ase bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold overflow_recov


---

### Post by Yellow Pasque on 2024-11-10
The problem is that your GPU is based on a "Southern Islands" chip rather than a "Sea Islands" chip.
In other words, you should use:
```
radeon.si_support=0 amdgpu.si_support=1
```
instead of:
```
radeon.cik_support=0 amdgpu.cik_support=1
```

---

### Post by harji on 2024-11-10
> **Yellow Pasque said:**
> The problem is that your GPU is based on a "Southern Islands" chip rather than a "Sea Islands" chip.
In other words, you should use:
```
radeon.si_support=0 amdgpu.si_support=1
```
instead of:
```
radeon.cik_support=0 amdgpu.cik_support=1
```

Thank you, It works.

---

### Post by Yellow Pasque on 2024-11-10
You're welcome. Please mark thread solved ('Thread Tools' menu above first post)

---

