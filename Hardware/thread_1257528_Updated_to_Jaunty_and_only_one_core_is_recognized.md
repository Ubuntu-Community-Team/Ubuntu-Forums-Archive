---
title: "Updated to Jaunty and only one core is recognized"
date: 2009-09-03
forum: Hardware
---

### Post by fdelpin on 2009-09-03
Hi,

I have a Laptop with a Centrino Duo processor. I had Intrepid and recently updated to Jaunty. The system used to recognize both cores but after the update only one core is found.

The output from "uname -a":

```
Linux tranqui 2.6.28-15-generic #51-Ubuntu SMP Mon Aug 31 13:33:16 UTC 2009 i686 GNU/Linux
```

and "cat /proc/cpuinfo":

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3666.14
clflush size	: 64
power management:

```

and "lshw":

```
tranqui
    description: Notebook
    product: VGN-SZ240P
    vendor: Sony Corporation
    version: A22288QV
    serial: 9594455-3000001
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=C9A93300-5B3C-11D9-80FA-0013A92AD3BE
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0081N0 (04/12/2006)
          size: 110KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 1GHz
          capacity: 1833MHz
          width: 32 bits
          clock: 166MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             capabilities: burst data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR
             physical id: 0
             slot: SODIMM1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR
             physical id: 1
             slot: SODIMM2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1850MHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical

```

and the last piece of information "dmesg | grep CPU" :

```
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004241] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004244] CPU: L2 cache: 2048K
[    0.004247] CPU: Physical Processor ID: 0
[    0.004249] CPU: Processor Core ID: 0
[    0.515040] CPU0: Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[    0.516002] Brought up 1 CPUs
[    0.516002] CPU0 attaching NULL sched-domain.
[    1.036112] Switched to high resolution mode on CPU 0
[    1.270735] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.270758] processor ACPI_CPU:00: registered as cooling_device0
[    1.270762] ACPI: Processor [CPU0] (supports 8 throttling states)
[  140.636672] CPU0 attaching NULL sched-domain.
[  140.652077] CPU0 attaching NULL sched-domain.
```

So it's obvious that both cores are not recognized. Any ideas?
Thanks!!

---

### Post by fdelpin on 2009-09-05
Any Ideas??? I'm trying but haven't worked it out yet...

thanks!

---

### Post by fdelpin on 2009-09-06
OK, I did some testing. 
It looks like the problem is related to ACPI support. If I add acpi=off in the boot menu, the kernel sees both CPUs. Unfortunately I have a bunch of other problems with other hardware not finding acpi support. So I had to turn it on again.

This is very frustrating because kernels 2.6.22-14-generic and 2.6.24-16-generic both had no problems with finding the 2 cores. I am looking at differences in the kernel config files to see if that might give me a clue of what's going on. I didn't want to start re-compiling kernels but it looks like the only option.

Any ideas?????????

Thanks

---

