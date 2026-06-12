---
title: "Problems with changing cpu freq on Asus X50Sr"
date: 2009-04-24
forum: Hardware
---

### Post by sqarq on 2009-04-24
I can't change cpu frequency on my laptop Asus X50SR (Core 2 Duo p7350).
I tried on ubu 8.10, 9.04, fedora 10 (on i383 and amd64 versions) and always I see that the only available freq is 1,34GHz: (now I have 9.04)
**cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies**
```
1344000
```In Gnome cpu freq monitor I can choose only the 1,34GHz, too:[http://i18.photobucket.com/albums/b109/Ketadewl/gnome.png](http://i18.photobucket.com/albums/b109/Ketadewl/gnome.png)
 **cat /proc/cpuinfo**
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping    : 6
cpu MHz        : 1344.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 3998.90
clflush size    : 64
power management:
processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping    : 6
cpu MHz        : 1344.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 3999.09
clflush size    : 64
power management:

```**lshw**```

  *-core
       description: Motherboard
       product: F5SR
       vendor: PEGATRON CORPORATION
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 207 (02/25/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: CPU 1
          size: 1344MHz
          capacity: 2002MHz
          width: 64 bits
          clock: 267MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm cpufreq
```Any ideas how to fix this problem?

---

