---
title: "Processor replacement"
date: 2014-08-10
forum: Hardware
---

### Post by Tristan_Williams on 2014-08-10
I've got a Dell Vostro 220: [http://www.dell.com/us/dfb/p/vostro-220/pd](http://www.dell.com/us/dfb/p/vostro-220/pd)
It is a 32-bit machine.

The way I understand it (and I'm probably wrong) is that the processor is what determines if you have 32 or 64-bit machine and OS

That would mean I just need to get a 64-bit processor to make this a 64-bit machine, but that sounds like it wouldn't work...



Basically, can I simply go buy a 64-bit processor with the same pin configuration, and use it in this computer that currently has a 32-bit processor?

---

### Post by mörgæs on 2014-08-10
No, it's not that simple. It's a matter of chipsets.

Besides, first I think we should take a look at the present processor. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by weatherman2 on 2014-08-10
Processors are more complicated than merely the socket and number of pins.  You can't simply install any processor that fits in the socket.  The motherboard and BIOS needs to be able to handle that processor.  The motherboard chipset must support the speed of the front-side bus. The BIOS needs to be aware of that exact processor and know how to handle it when the machine powers up.  The motherboard needs to support the voltage of the processor.

If you want to upgrade the processor, try to find out which processors are explicitly supported.  Sometimes an updated BIOS will support newer processors, but there are still other limitations as noted above.  Dell may provide somewhere a list of all processors ever sold with that Vostro model.

That said, you should also find out exactly what processor is in there now.  I'd bet money that your processor is in fact a 64 bit CPU.  It sounds like that Vostro line came out in 2008 or 2009 - and by then all but the Intel Atom processors (in netbooks) were 64 bit.   Almost all (maybe all) Core 2 Duo processors and their derivatives are 64 bit capable (but you can still install a 32 bit OS on them). A "Celeron" or "Pentium Dual Core" that is a slower/cheaper version of a Core 2 Duo is 64 bit capable.   (The older "Core Duo" - not "Core 2 Duo" - are only 32 bit capable however.)

If you have Ubuntu booted, open a terminal and type:

```
sudo lshw -C CPU
```

to find out the exact processor, if you don't know.  Find the Intel processor number - the name "Pentium" or "Celeron" doesn't mean much.  One of my machines for example has an Intel "Pentium Dual Core" processor - but the processor number is "E2200" - and when I google that I get a link to Intel's website telling me exactly what it is.  (And that is is 64 bit capable.)

Anyway, if you have a 64 bit processor, all you have to do is install a 64 bit OS.

---

### Post by Tristan_Williams on 2014-08-10
Here is the output from 'sudo lshw -sanitize > lshw.txt'
```

computer
    description: Desktop Computer
    product: Vostro 220 Series ()
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0P301D
       vendor: Dell Inc.
       physical id: 0
       version: A02
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.1.4
          date: 04/17/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          slot: Socket 775
          size: 1595MHz
          capacity: 2933MHz
          width: 64 bits
          clock: 266MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix
             physical id: 0
             serial: [REMOVED]
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: DIMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125U64CP8-S6
             vendor: Hynix
             physical id: 2
             serial: [REMOVED]
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: DIMM4
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: [REMOVED]
          size: 2928MHz
          capacity: 2928MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
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
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe900000-fe9fffff
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d880(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:d480(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:feafbc00-feafbfff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:feaf4000-feaf7fff
        *-pci:0
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d400(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d080(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:feafb800-feafbbff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=32) memory:feafb000-feafb7ff
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
             resources: memory:feafac00-feafacff ioport:400(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD3200AAKS-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000a4d50
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 294GiB
                capacity: 294GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-18 22:24:13 filesystem=ext4 lastmountpoint=/ modified=2014-08-02 12:51:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-08-02 12:51:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4060MiB
                capacity: 4060MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4060MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM DH-16D5S
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: VD15
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 5
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK3263GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: GC00
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0006bab0
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: [REMOVED]
                size: 294GiB
                capacity: 294GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-05 21:53:23 filesystem=ext4 lastmountpoint=/ modified=2014-07-15 05:13:18 mounted=2014-07-15 05:13:18 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                size: 4060MiB
                capacity: 4060MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 4060MiB
                   capabilities: nofs

```

And here is the output from 'cat /proc/cpuinfo'
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 2928.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 5851.60
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1595.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips    : 5851.60
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


```

---

### Post by tgalati4 on 2014-08-10
Or

```
cat /proc/cpuinfo
```

If your motherboard supports both 32-bit and 64-bit processors, then you might be OK.  You can get a 10 to 40% speedup on certain applications with 64-bit.  It's not dramatic but enough to pursue.

---

### Post by mörgæs on 2014-08-10
As I expected, you already have a 64 bit processor.

---

### Post by Tristan_Williams on 2014-08-10
> **mörgæs said:**
> As I expected, you already have a 64 bit processor.

Well that's nice to know... I'm not quite sure what made me think it was 32-bit. Probably looked in the wrong place.

---

### Post by mörgæs on 2014-08-10
If this solves your problem please mark the thread so.

---

