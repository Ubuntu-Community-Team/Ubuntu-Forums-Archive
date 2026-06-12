---
title: "My OS doesn't seem to use more than 3-4G of RAM although I have 16G installed."
date: 2013-10-17
forum: Hardware
---

### Post by Julian_Treadwell on 2013-10-17
Hi,

I'm fairly new to Ubuntu although I have a little experience with other *nix systems.

I've just installed a 64-bit 12.04 OS (dual-boot with Win 7) on a machine with the following specs:

```
julian@ubuntu:~$ sudo lshw | more
ubuntu                    
    description: Desktop Computer
    product: GA-990FXA-D3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=desktop uuid=39303242-3334-3639-3041-4542
FFFFFFFF
  *-core
       description: Motherboard
       product: GA-990FXA-D3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6
          date: 05/17/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: isa pci pnp upgrade shadowing cdboot bootselect socketed
rom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5prints
creen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboo
t biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-4170 Quad-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-4170 Quad-Core Processor
          slot: Socket M2
          size: 4200MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext 
fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apici
d aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx
 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch o
svw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_psta
te npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pa
usefilter pfthreshold cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 2
             slot: A2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
```


As you can see it recognises that I have 16G of RAM but it never uses more than about 3.5G, even when I'm editing a video.

I'm guessing there's some extra config I need to do to enable the remaining 12G, but I've no idea what.

Any suggestions appreciated!

Thanks,

Julian

---

### Post by QIII on 2013-10-17
Hello!

The applications you have running are reserving only the memory they need and your OS is managing it.  There's nothing wrong and nothing to set.

---

### Post by sanderj on 2013-10-18
On top of what QIII says: what is the output of:

```
free -h
```

---

### Post by Yellow Pasque on 2013-10-18
Run a few VM's and allocate a couple GB's to them...

---

### Post by Bucky Ball on 2013-10-18
> **QIII said:**
> Hello!

The applications you have running are reserving only the memory they need and your OS is managing it.  There's nothing wrong and nothing to set.

+1. Move along, nothing to see here, not even breaking a sweat.

> **Temüjin said:**
> Run a few VM's and allocate a couple GB's to them...

+1. Now you'll smell some rubber. You will not touch the sides of 16Gb of RAM unless you are doing something like this. That much RAM is generally totally redundant in domestic machines and a waste of time, energy, money and space (IMHO) unless you intend to use it.

I can edit video with 1Gb of RAM on a P4 processor ...

---

### Post by grahammechanical on 2013-10-18
My machine only has 1GB RAM and with just Chromium loaded it only uses 533MB RAM. I think that is fantastic. Where would people like me be if Ubuntu was greedy? Memory usage has reduced in Ubuntu by 10-15% (of 1GB RAM) since 12.04 and I expect it to get better with all the work being done on Ubuntu for phones/tablets which will filter onto the desktop over the coming months.

This is not Microsoft, where we have to buy a new machine if we want the latest Microsoft operating system. This is Linux. Better still it is Ubuntu!

Regards.

---

