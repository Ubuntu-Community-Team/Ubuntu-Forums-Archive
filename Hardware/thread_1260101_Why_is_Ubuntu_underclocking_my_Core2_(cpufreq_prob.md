---
title: "Why is Ubuntu underclocking my Core2? (cpufreq problem?)"
date: 2009-09-07
forum: Hardware
---

### Post by bobince on 2009-09-07
I have a Core 2 Quad Q9300 running on an Intel G45 board. This should be a 2.5GHz part. cpuinfo (same for all 4 cores):

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
stepping    : 7
cpu MHz        : 1988.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 4995.03
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```however according to the 'CPU frequency scaling monitor' it is running at only 1.99GHz. This is backed up by all the data in /sys/devices/system/cpu/cpu0/cpufreq, which give 1.99GHz as the only available speed. cpufreq-info agrees:

```
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.99 GHz - 1.99 GHz
  available frequency steps: 1.99 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.99 GHz and 1.99 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.99 GHz (asserted by call to hardware).
  cpufreq stats: 1.99 GHz:100.00%
```Why am I not getting the full speed of my processor? Or am I, and the 1.99Gz thing is a lie? This is a totally vanilla Core 2 box, not overclocked or otherwise messed with; I wouldn't have expected it to cause the kernel any difficulties.

Do I have to install any special frequency scaling stuff just to get the promised speed out of my CPU? "modprobe acpi_cpufreq" gives me "FATAL: Module acpi_cpufreq not found", but I do have a 'sys/module/acpi_cpufreq/parameters' path, so I don't know if that's working or not.

This behaviour seen in both Jaunty and Karmic-A5.

---

### Post by ukblacknight on 2009-09-07
What does the System Monitor have it down as?  It should say the frequency of each clock there.  Also check with the command "sudo lshw", that will tell you.

The operating system doesn't control the clock speed, that is down to the BIOS.  Your first output does say that it's running at 2.5GHz, so to be honest, I wouldn't worry about it.

---

### Post by bobince on 2009-09-08
> **ukblacknight said:**
> What does the System Monitor have it down as?

It quotes "Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz", same as the model name in cpuinfo. But as far as I can tell that really is just a model name.

> Also check with the command "sudo lshw", that will tell you.It says "size: 1988MHz". Whole thing (minus the *-disk and *-network sections which have unique IDs) is pasted below if that's of use. 1988MHz would seem to imply the clock multiplier has got set to 6 instead of 7.5.

("slot: Socket 423" would seem to be an obvious mistake.)

> The operating system doesn't control the clock speed, that is down to the BIOS.FWIW ACPI is on in the BIOS and WinXP dual-booted on it reports 2.5GHz.

(I would, in any case, quite like to have SpeedStep; I expected it to just work and don't know why cpufreq offers no choice of speeds.)

```
stalk
    description: Desktop Computer
    product: SG45
    vendor: Shuttle Inc
    version: V10
    serial: 0
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=01020907-0301-0401-0807-060504030201
  *-core
       description: Motherboard
       product: FG45
       vendor: Shuttle Inc
       physical id: 0
       version: V10
       serial: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/06/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad
          slot: Socket 423
          size: 1988MHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:fd000000-fd3fffff memory:d0000000-dfffffff(prefetchable) ioport:ff00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:fdb00000-fdbfffff
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdfff000-fdfff3ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fdff4000-fdff7fff
        *-pci:0
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:d000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:c000(size=4096) memory:fd600000-fd6fffff ioport:fde00000(size=1048576)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:17 memory:fd6ff000-fd6ff7ff memory:fd6fe000-fd6fe07f memory:fd6fd000-fd6fd07f memory:fd6fc000-fd6fc07f
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fb00(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fa00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f900(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffe000-fdffe3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:a000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=32) memory:fdffd000-fdffd7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffc000-fdffc0ff ioport:500(size=32)
```

---

### Post by Whiffle on 2009-09-08
Check your BIOS settings, specifically the clock multiplier if i remember correctly.  My motherboard didn't autodetect it correctly and had it set to low, so my 3 GHz chip was running at like 2.6.  I set it to the correct one and all is well.

---

### Post by ukblacknight on 2009-09-08
> **Whiffle said:**
> Check your BIOS settings, specifically the clock multiplier if i remember correctly.  My motherboard didn't autodetect it correctly and had it set to low, so my 3 GHz chip was running at like 2.6.  I set it to the correct one and all is well.

Me too.  I've got a Q9550 @ 2.83GHz, and I had to alter the multiplier in my BIOS to get it to that speed.  I think it was on 8.0 by default, I bumped it up to 8.5 (for my processor, don't use that as a guide for your own).

---

### Post by bobince on 2009-09-08
> Check your BIOS settings, specifically the clock multiplier if i remember correctly.Yes, the clock muliplier is unlocked, and set to 7 with +.5 enabled (they are two separate options in my BIOS FSR, as opposed to just saying '7.5'). WinXP reaches the expected 2.5GHz, Ubuntu remains stuck at 1.99GHz.

I can increase the clock itself from the BIOS if I want, but I'm not here to overclock, I just want my CPU to run at its rated speed (ideally with the ability to step down to save power when not in use).

---

### Post by ukblacknight on 2009-09-08
Just to add to this, my "CPU Scaling Monitor" panel applet shows each core at 2GHz (70%).

When I run lshw, it shows the "size" of my CPU at 2ghz.

```

*-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU
          slot: Socket 775
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq


```

I'd take this with a pinch of salt.  I'm going to assume it means the minimum clock speed that the processor runs at, without taking into consideration the multiplier.  When I first installed my CPU, I hadn't changed the multiplier, the System Monitor reported that it was running at about 2.53GHz.

---

### Post by bobince on 2010-07-31
Update: a new BIOS (Shuttle SG45S10T) fixed the 1998MHz problem. It now correctly reports:

```
cpu MHz        : 2500.000
```

The bogomips value is roughly unchanged, so I assume it was only a reporting error and the processor wasn't really running at 1998.

/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies now contains:

```
2500000 2000000 
```

and as expected this allows the CPU Frequency Monitor to switch between 2GHz and 2.5GHz (and ondemand works).

This is still far fewer Speedstep states than I had expected though; 2GHz probably isn't going to be saving a huge amount of power. Anyone know what the proper list of freqs for a Q9300 should be?

FWIW the only difference the BIOS update made to the acpidump/iasl output was:

```
"CPU0IST ", 
0xBBCE8280, 
0x000004BE, 
```

Previously the second dword was 0x0000022A. However I know nothing about AML so I've no idea if this is significant.

---

