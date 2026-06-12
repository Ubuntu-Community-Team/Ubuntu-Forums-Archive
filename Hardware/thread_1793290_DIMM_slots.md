---
title: "DIMM slots"
date: 2011-06-29
forum: Hardware
---

### Post by arno48 on 2011-06-29
I have just bought an assembled (not branded) desktop.
Motherboard has two 240-pin DDR3  DIMM slots, but there is only one DIMM, while the second slot is empty.
As I ordered a Intel Pentium Dual Core E 5700, I wonder if "Dual" means two DIMM and therefore there is a DIMM missing

---

### Post by psusi on 2011-06-29
A dual core CPU has two CPUs - it has nothing to do with DIMMs.  Although it is unusual to have an odd number of DIMMs these days since they usually come in interleaved pairs for performance.

---

### Post by dabl on 2011-06-29
Somewhere on the motherboard printed circuit board is the manufacturer and part number.  That would be good to find -- it might help you learn more about the capabilities and limitations.

Alternatively, with Linux running on it, you can install dmidecode and run it with root privileges.  You might see something like this in the ouput:

```
Handle 0x0006, DMI type 2, 20 bytes
Base Board Information
        Manufacturer: Intel Corporation
        Product Name: D975XBX2
        Version: AAD53350-509
        Serial Number: BQB2745000PP
        Asset Tag: Base Board Asset Tag
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Base Board Chassis Location
```

lshw will also give you informative output:


```
description: Computer
    product: ()
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal uuid=58DC6002-9072-11DC-A6B5-000EA68F7305
  *-core
       description: Motherboard
       product: D975XBX2
       vendor: Intel Corporation
       physical id: 0
       version: AAD53350-509
       serial: BQB2745000PP
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
          slot: J3E1
          size: 2926MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
```

---

### Post by arno48 on 2011-06-30
Thanks for helping.

---

