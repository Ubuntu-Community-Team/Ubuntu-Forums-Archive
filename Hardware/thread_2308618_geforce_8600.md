---
title: "geforce 8600"
date: 2016-01-04
forum: Hardware
---

### Post by messner on 2016-01-04
I have a problem with ubuntu lts 14.04 and geforce 8600 ...

The card works ok until when the system crashes ...

Then it reboots and I cant use it any more. Ubuntu starts the shell part with distorted font that is still readable ... Boot process doesn't come to sucessfull graphical login. It stucks in the middle of the process ...

When i revert a computer to normal login (using different bizare strategies ... for example with reinstalling driver in shell mode), everything again works beutiful for few days till next crash ...

Any ideas where fo start with debugging.

I have tried different drivers options 340, open source, etc .... I allways end with the same anoying error. I have removed opensource drivers .... noth8ng works ...

---

### Post by mörgæs on 2016-01-05
First of all a system should not crash. 

Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Yellow Pasque on 2016-01-05
I'd start by keeping a close eye on temps, especially if the sporadic crashing/rebooting occurs when the system is loaded (i.e. doing something intensive).

---

### Post by messner on 2016-01-05
Here is the result of "sudo lshw -sanitize > lshw.txt"

```
computer
    description: Desktop Computer
    product: P5K SE (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: P5K SE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0309
          date: 07/04/2007
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: [REMOVED]
          slot: LGA775
          size: 1998MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
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
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
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
          physical id: 30
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: [REMOVED]
          size: 2331MHz
          capacity: 2331MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:46 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:fe9e0000-fe9fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c800(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c880(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:cc00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f9fffc00-f9ffffff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f9ff8000-f9ffbfff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:80000000-803fffff ioport:f8f00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:80400000(size=2097152)
           *-ide
                description: IDE interface
                product: 88SE6121 SATA II / PATA Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:16 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:febffc00-febfffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=4096) memory:fea00000-feafffff ioport:80600000(size=2097152)
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:45 memory:feac0000-feafffff memory:feaa0000-feabffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c400(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c480(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9fff800-f9fffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IB (ICH9) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IB (ICH9) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9fff400-f9fff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=16) ioport:b400(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD4000AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1C01
             serial: [REMOVED]
             size: 372GiB (400GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ca96c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 370GiB
                capacity: 370GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-06-17 17:39:13 filesystem=ext4 lastmountpoint=/ modified=2016-01-05 17:16:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-01-05 17:16:06 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2046MiB
                capacity: 2046MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2046MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW SH-S182D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB06
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

What are the next steps ?

---

### Post by messner on 2016-01-05
"I'd start by keeping a close eye on temps"

I don't think that is the fault, because I have temp monitors installed and running as widget ...

---

### Post by mörgæs on 2016-01-06
The BIOS is old. You could consider upgrading it to see if it gives a more stable system. 

[https://www.asus.com/support/Download/1/22/43/8/I2f2e2yHI0XF2Vf9/25/](https://www.asus.com/support/Download/1/22/43/8/I2f2e2yHI0XF2Vf9/25/)

---

### Post by messner on 2016-01-06
I have upgraded the BIOS to the last available version ob ASUS website ...

I am attaching the new lshw.txt and syslog of the boot process ...

What should I do next ?

```
computer
    description: Desktop Computer
    product: P5K SE (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: P5K SE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1402
          date: 06/25/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: [REMOVED]
          slot: LGA775
          size: 2331MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
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
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
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
          physical id: 30
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: [REMOVED]
          size: 1998MHz
          capacity: 1998MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:46 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:fe9e0000-fe9fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c800(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c880(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:cc00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f9fffc00-f9ffffff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f9ff8000-f9ffbfff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:80000000-803fffff ioport:f8f00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:80400000(size=2097152)
           *-ide
                description: IDE interface
                product: 88SE6121 SATA II / PATA Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:16 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:febffc00-febfffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=4096) memory:fea00000-feafffff ioport:80600000(size=2097152)
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:45 memory:feac0000-feafffff memory:feaa0000-feabffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c400(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c480(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9fff800-f9fffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IB (ICH9) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IB (ICH9) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9fff400-f9fff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=16) ioport:b400(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD4000AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1C01
             serial: [REMOVED]
             size: 372GiB (400GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ca96c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 370GiB
                capacity: 370GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-06-17 17:39:13 filesystem=ext4 lastmountpoint=/ modified=2016-01-06 18:20:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-01-06 18:20:33 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2046MiB
                capacity: 2046MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2046MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW SH-S182D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB06
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

I am attaching my syslog of boot process:

```
Jan  6 18:23:32 dragica-P5K-SE dbus[625]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jan  6 18:23:32 dragica-P5K-SE dbus[625]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jan  6 18:23:32 dragica-P5K-SE rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="706" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan  6 18:24:23 dragica-P5K-SE rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="708" x-info="http://www.rsyslog.com"] start
Jan  6 18:24:23 dragica-P5K-SE rsyslogd: rsyslogd's groupid changed to 104
Jan  6 18:24:23 dragica-P5K-SE rsyslogd: rsyslogd's userid changed to 101
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Linux version 3.16.0-57-generic (buildd@lcy01-20) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #77~14.04.1-Ubuntu SMP Thu Dec 17 23:20:32 UTC 2015 (Ubuntu 3.16.0-57.77~14.04.1-generic 3.16.7-ckt20)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] KERNEL supported cpus:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Intel GenuineIntel
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   AMD AuthenticAMD
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   NSC Geode by NSC
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Cyrix CyrixInstead
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Centaur CentaurHauls
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Transmeta GenuineTMx86
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Transmeta TransmetaCPU
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   UMC UMC UMC UMC
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ff7ffff] usable
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x000000007ff80000-0x000000007ff8dfff] ACPI data
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x000000007ff8e000-0x000000007ffdffff] ACPI NVS
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] SMBIOS 2.4 present.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] DMI: System manufacturer P5K SE/P5K SE, BIOS 1402    06/25/2009
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] e820: last_pfn = 0x7ff80 max_arch_pfn = 0x1000000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] MTRR default type: uncachable
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   00000-9FFFF write-back
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   C0000-DFFFF write-protect
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   E0000-EFFFF write-through
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] MTRR variable ranges enabled:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   1 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   2 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   3 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   4 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   5 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   6 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   7 disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] init_memory_mapping: [mem 0x37400000-0x375fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x37400000-0x375fffff] page 2M
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] init_memory_mapping: [mem 0x34000000-0x373fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x34000000-0x373fffff] page 2M
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] init_memory_mapping: [mem 0x37600000-0x377fdfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]  [mem 0x37600000-0x377fdfff] page 4k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BRK [0x01bd5000, 0x01bd5fff] PGTABLE
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BRK [0x01bd6000, 0x01bd6fff] PGTABLE
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] RAMDISK: [mem 0x35b94000-0x36dc1fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: RSDP 0x00000000000FBDD0 000014 (v00 ACPIAM)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: RSDT 0x000000007FF80000 00003C (v01 A_M_I_ OEMRSDT  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: FACP 0x000000007FF80200 000084 (v02 A_M_I_ OEMFACP  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: DSDT 0x000000007FF805C0 007EB9 (v01 A0807  A0807000 00000000 INTL 20060113)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: FACS 0x000000007FF8E000 000040
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: APIC 0x000000007FF80390 00006C (v01 A_M_I_ OEMAPIC  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: MCFG 0x000000007FF80400 00003C (v01 A_M_I_ OEMMCFG  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: OEMB 0x000000007FF8E040 000081 (v01 A_M_I_ AMI_OEM  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: HPET 0x000000007FF88480 000038 (v01 A_M_I_ OEMHPET  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: OSFR 0x000000007FF884C0 0000B0 (v01 A_M_I_ OEMOSFR  06000925 MSFT 00000097)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] 1159MB HIGHMEM available.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] 887MB LOWMEM available.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   low ram: 0 - 377fe000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] BRK [0x01bd7000, 0x01bd7fff] PGTABLE
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Zone ranges:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Normal   [mem 0x01000000-0x377fdfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   HighMem  [mem 0x377fe000-0x7ff7ffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Movable zone start for each node
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Early memory node ranges
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   node   0: [mem 0x00100000-0x7ff7ffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] On node 0 totalpages: 524060
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   Normal zone: 223230 pages, LIFO batch:31
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   HighMem zone: 2320 pages used for memmap
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]   HighMem zone: 296834 pages, LIFO batch:31
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Using APIC driver default
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] nr_irqs_gsi: 40
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] e820: [mem 0x80000000-0xfedfffff] available for PCI devices
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f6f9f000 s35008 r0 d22336 u57344
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 522284
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-57-generic root=UUID=fbadd670-fff6-4206-9cff-52d00d8306ee ro quiet splash
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing CPU#0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007ff80)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Initializing Movable for node 0 (00000000:00000000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Memory: 2047864K/2096240K available (6757K kernel code, 642K rwdata, 2916K rodata, 896K init, 788K bss, 48376K reserved, 1187336K highmem)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] virtual kernel memory layout:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]       .init : 0xc1a16000 - 0xc1af6000   ( 896 kB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]       .data : 0xc16998a8 - 0xc1a14980   (3564 kB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000]       .text : 0xc1000000 - 0xc16998a8   (6758 kB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Hierarchical RCU implementation.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] CPU 0 irqstacks, hard=f4c08000 soft=f4c0a000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] Console: colour VGA+ 80x25
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] console [tty0] enabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] allocated 4194304 bytes of page_cgroup
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] hpet clockevent registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.000000] tsc: Detected 2336.110 MHz processor
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4672.22 BogoMIPS (lpj=9344440)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.004018] pid_max: default: 32768 minimum: 301
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.004031] ACPI: Core revision 20140424
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013232] ACPI: All ACPI Tables successfully acquired
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013253] Security Framework initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013274] AppArmor: AppArmor initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013276] Yama: becoming mindful.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013325] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013328] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013594] Initializing cgroup subsys memory
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013623] Initializing cgroup subsys devices
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013632] Initializing cgroup subsys freezer
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013637] Initializing cgroup subsys net_cls
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013642] Initializing cgroup subsys blkio
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013648] Initializing cgroup subsys perf_event
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013651] Initializing cgroup subsys net_prio
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013659] Initializing cgroup subsys hugetlb
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013683] CPU: Physical Processor ID: 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013684] CPU: Processor Core ID: 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013689] mce: CPU supports 6 MCE banks
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013697] CPU0: Thermal monitoring enabled (TM2)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013701] process: using mwait in idle threads
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013708] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013708] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.013708] tlb_flushall_shift: -1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.014149] Freeing SMP alternatives memory: 32K (c1af6000 - c1afe000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.016006] ftrace: allocating 28621 entries in 56 pages
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.024082] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.024439] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.067677] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (fam: 06, model: 0f, stepping: 0b)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] perf_event_intel: PEBS disabled due to CPU errata
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... version:                2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... bit width:              40
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... generic registers:      2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... value mask:             000000ffffffffff
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... max period:             000000007fffffff
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... fixed-purpose events:   3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] ... event mask:             0000000700000003
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] CPU 1 irqstacks, hard=f4542000 soft=f4544000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] x86: Booting SMP configuration:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.068000] .... node  #0, CPUs:      #1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.008000] Initializing CPU#1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.079257] x86: Booted up 1 node, 2 CPUs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.079262] smpboot: Total of 2 processors activated (9344.44 BogoMIPS)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.079351] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080146] devtmpfs: initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080380] evm: security.selinux
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080382] evm: security.SMACK64
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080383] evm: security.SMACK64EXEC
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080384] evm: security.SMACK64TRANSMUTE
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080386] evm: security.SMACK64MMAP
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080387] evm: security.ima
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080388] evm: security.capability
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.080481] PM: Registering ACPI NVS region [mem 0x7ff8e000-0x7ffdffff] (335872 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081712] pinctrl core: initialized pinctrl subsystem
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081812] regulator-dummy: no parameters
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081846] RTC time: 18:24:07, date: 01/06/16
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] NET: Registered protocol family 16
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] EISA bus registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] cpuidle: using governor ladder
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] cpuidle: using governor menu
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] ACPI: bus type PCI registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] PCI: not using MMCONFIG
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] PCI: Using configuration type 1 for base access
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] mtrr: your CPUs had inconsistent variable MTRR settings
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] mtrr: probably your BIOS does not setup all CPUs.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.081907] mtrr: corrected configuration.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.092126] ACPI: Added _OSI(Module Device)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.092129] ACPI: Added _OSI(Processor Device)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.092130] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.092132] ACPI: Added _OSI(Processor Aggregator Device)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.097954] ACPI: Executed 1 blocks of module-level executable AML code
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.102587] ACPI: Dynamic OEM Table Load:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.102594] ACPI: SSDT 0x00000000F4C05200 0001D2 (v01 AMI    CPU1PM   00000001 INTL 20060113)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103083] ACPI: Dynamic OEM Table Load:
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103088] ACPI: SSDT 0x00000000F4C05400 000143 (v01 AMI    CPU2PM   00000001 INTL 20060113)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103533] ACPI: Interpreter enabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103553] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103568] ACPI: (supports S0 S1 S3 S4 S5)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103570] ACPI: Using IOAPIC for interrupt routing
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.103592] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.104125] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.104127] PCI: Using MMCONFIG for extended config space
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.104147] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.110819] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.110826] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.110831] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111124] PCI host bridge to bus 0000:00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111128] pci_bus 0000:00: root bus resource [bus 00-ff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111130] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111133] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111135] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111138] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111140] pci_bus 0000:00: root bus resource [mem 0x80000000-0xffffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111150] pci 0000:00:00.0: [8086:29c0] type 00 class 0x060000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111264] pci 0000:00:01.0: [8086:29c1] type 01 class 0x060400
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111307] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111353] pci 0000:00:01.0: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111429] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111470] pci 0000:00:1a.0: reg 0x20: [io  0xc800-0xc81f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111562] pci 0000:00:1a.0: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111619] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111659] pci 0000:00:1a.1: reg 0x20: [io  0xc880-0xc89f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111750] pci 0000:00:1a.1: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111807] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111847] pci 0000:00:1a.2: reg 0x20: [io  0xcc00-0xcc1f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.111938] pci 0000:00:1a.2: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112009] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112030] pci 0000:00:1a.7: reg 0x10: [mem 0xf9fffc00-0xf9ffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112115] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112165] pci 0000:00:1a.7: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112226] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112242] pci 0000:00:1b.0: reg 0x10: [mem 0xf9ff8000-0xf9ffbfff 64bit]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112311] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112406] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112477] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112527] pci 0000:00:1c.0: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112586] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112656] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112707] pci 0000:00:1c.4: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112763] pci 0000:00:1c.5: [8086:294a] type 01 class 0x060400
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112833] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112884] pci 0000:00:1c.5: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112943] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.112983] pci 0000:00:1d.0: reg 0x20: [io  0xc080-0xc09f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113077] pci 0000:00:1d.0: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113133] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113172] pci 0000:00:1d.1: reg 0x20: [io  0xc400-0xc41f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113265] pci 0000:00:1d.1: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113321] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113360] pci 0000:00:1d.2: reg 0x20: [io  0xc480-0xc49f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113450] pci 0000:00:1d.2: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113515] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113536] pci 0000:00:1d.7: reg 0x10: [mem 0xf9fff800-0xf9fffbff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113620] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113670] pci 0000:00:1d.7: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113726] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113811] pci 0000:00:1e.0: System wakeup disabled by ACPI
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113870] pci 0000:00:1f.0: [8086:2918] type 00 class 0x060100
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113943] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113949] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.113953] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114068] pci 0000:00:1f.2: [8086:2921] type 00 class 0x01018f
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114083] pci 0000:00:1f.2: reg 0x10: [io  0xb000-0xb007]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114090] pci 0000:00:1f.2: reg 0x14: [io  0xac00-0xac03]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114098] pci 0000:00:1f.2: reg 0x18: [io  0xa880-0xa887]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114106] pci 0000:00:1f.2: reg 0x1c: [io  0xa800-0xa803]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114114] pci 0000:00:1f.2: reg 0x20: [io  0xa480-0xa48f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114121] pci 0000:00:1f.2: reg 0x24: [io  0xa400-0xa40f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114236] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114251] pci 0000:00:1f.3: reg 0x10: [mem 0xf9fff400-0xf9fff4ff 64bit]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114271] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114369] pci 0000:00:1f.5: [8086:2926] type 00 class 0x010185
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114384] pci 0000:00:1f.5: reg 0x10: [io  0xc000-0xc007]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114391] pci 0000:00:1f.5: reg 0x14: [io  0xbc00-0xbc03]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114399] pci 0000:00:1f.5: reg 0x18: [io  0xb880-0xb887]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114407] pci 0000:00:1f.5: reg 0x1c: [io  0xb800-0xb803]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114415] pci 0000:00:1f.5: reg 0x20: [io  0xb480-0xb48f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114423] pci 0000:00:1f.5: reg 0x24: [io  0xb400-0xb40f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114586] pci 0000:01:00.0: [10de:0402] type 00 class 0x030000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114599] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114610] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114621] pci 0000:01:00.0: reg 0x1c: [mem 0xfa000000-0xfbffffff 64bit]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114629] pci 0000:01:00.0: reg 0x24: [io  0xdc00-0xdc7f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114637] pci 0000:01:00.0: reg 0x30: [mem 0xfe9e0000-0xfe9fffff pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114734] pci 0000:00:01.0: PCI bridge to [bus 01]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114737] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114741] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe9fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114745] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114803] pci 0000:00:1c.0: PCI bridge to [bus 04]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114812] pci 0000:00:1c.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114888] pci 0000:03:00.0: [11ab:6121] type 00 class 0x01018f
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114907] pci 0000:03:00.0: reg 0x10: [io  0xec00-0xec07]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114919] pci 0000:03:00.0: reg 0x14: [io  0xe880-0xe883]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114931] pci 0000:03:00.0: reg 0x18: [io  0xe800-0xe807]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114942] pci 0000:03:00.0: reg 0x1c: [io  0xe480-0xe483]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114954] pci 0000:03:00.0: reg 0x20: [io  0xe400-0xe40f]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.114966] pci 0000:03:00.0: reg 0x24: [mem 0xfebffc00-0xfebfffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115032] pci 0000:03:00.0: supports D1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115034] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115098] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115107] pci 0000:00:1c.4: PCI bridge to [bus 03]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115111] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115115] pci 0000:00:1c.4:   bridge window [mem 0xfeb00000-0xfebfffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115195] pci 0000:02:00.0: [1969:1048] type 00 class 0x020000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115220] pci 0000:02:00.0: reg 0x10: [mem 0xfeac0000-0xfeafffff 64bit]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115270] pci 0000:02:00.0: reg 0x30: [mem 0xfeaa0000-0xfeabffff pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115327] pci 0000:02:00.0: PME# supported from D3hot D3cold
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115393] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115402] pci 0000:00:1c.5: PCI bridge to [bus 02]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115407] pci 0000:00:1c.5:   bridge window [mem 0xfea00000-0xfeafffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115490] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115500] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115502] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115504] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115507] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115509] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xffffffff] (subtractive decode)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.115534] pci_bus 0000:00: on NUMA node 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116168] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12 14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116229] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 12 14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116288] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116347] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116406] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116466] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116525] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116584] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116650] ACPI: Enabled 2 GPEs in block 00 to 3F
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] vgaarb: setting as boot device: PCI:0000:01:00.0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] vgaarb: loaded
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] vgaarb: bridge control possible 0000:01:00.0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] SCSI subsystem initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] libata version 3.00 loaded.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] ACPI: bus type USB registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] usbcore: registered new interface driver usbfs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] usbcore: registered new interface driver hub
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] usbcore: registered new device driver usb
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] PCI: Using ACPI for IRQ routing
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] PCI: pci_cache_line_size set to 64 bytes
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] e820: reserve RAM buffer [mem 0x7ff80000-0x7fffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] NetLabel: Initializing
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] NetLabel:  domain hash size = 128
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] NetLabel:  unlabeled traffic allowed by default
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.116736] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.118116] Switched to clocksource hpet
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125644] AppArmor: AppArmor Filesystem Enabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125684] pnp: PnP ACPI init
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125706] ACPI: bus type PNP registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125793] system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125798] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.125881] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126157] pnp 00:02: [dma 2]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126215] pnp 00:02: Plug and Play ACPI device, IDs PNP0700 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126292] system 00:03: [io  0x0290-0x0297] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126296] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126480] system 00:04: [io  0x04d0-0x04d1] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126484] system 00:04: [io  0x0800-0x087f] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126486] system 00:04: [io  0x0480-0x04bf] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126490] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126493] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126495] system 00:04: [mem 0xfed50000-0xfed8ffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126498] system 00:04: [mem 0xffa00000-0xffafffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126501] system 00:04: [mem 0xffb00000-0xffbfffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126504] system 00:04: [mem 0xffe00000-0xffefffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126507] system 00:04: [mem 0xfff00000-0xfffffffe] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126510] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126770] pnp 00:05: [dma 0 disabled]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126846] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126941] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126944] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.126948] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127019] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127097] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127100] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127300] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127304] system 00:09: [mem 0x000c0000-0x000cffff] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127307] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127310] system 00:09: [mem 0x00100000-0x7fffffff] could not be reserved
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127313] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127443] pnp: PnP ACPI: found 10 devices
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127445] ACPI: bus type PNP unregistered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.127451] PnPBIOS: Disabled by ACPI PNP
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164493] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164497] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 400000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164506] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164514] pci 0000:00:1c.5: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164517] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164527] pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164531] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 400000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164534] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164536] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164539] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164541] pci 0000:00:1c.5: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164548] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x803fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164555] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164561] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164565] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164568] pci 0000:00:1c.5: BAR 13: assigned [io  0x2000-0x2fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164571] pci 0000:00:01.0: PCI bridge to [bus 01]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164574] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164578] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe9fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164581] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164585] pci 0000:00:1c.0: PCI bridge to [bus 04]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164588] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164593] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x803fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164597] pci 0000:00:1c.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164603] pci 0000:00:1c.4: PCI bridge to [bus 03]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164605] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164610] pci 0000:00:1c.4:   bridge window [mem 0xfeb00000-0xfebfffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164614] pci 0000:00:1c.4:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164619] pci 0000:00:1c.5: PCI bridge to [bus 02]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164622] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164627] pci 0000:00:1c.5:   bridge window [mem 0xfea00000-0xfeafffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164631] pci 0000:00:1c.5:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164636] pci 0000:00:1e.0: PCI bridge to [bus 05]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164646] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164648] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164651] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164653] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164655] pci_bus 0000:00: resource 8 [mem 0x80000000-0xffffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164657] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164660] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfe9fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164662] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164664] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164667] pci_bus 0000:04: resource 1 [mem 0x80000000-0x803fffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164669] pci_bus 0000:04: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164671] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164674] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164676] pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164678] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164680] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164683] pci_bus 0000:02: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164685] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164687] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164689] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164692] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164694] pci_bus 0000:05: resource 8 [mem 0x80000000-0xffffffff]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164724] NET: Registered protocol family 2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164938] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164955] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.164981] TCP: Hash tables configured (established 8192 bind 8192)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.165002] TCP: reno registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.165005] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.165013] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.165062] NET: Registered protocol family 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.166189] pci 0000:01:00.0: Video device with shadowed ROM
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.166197] PCI: CLS 32 bytes, default 64
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.166255] Trying to unpack rootfs image as initramfs...
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.524935] Freeing initrd memory: 18616K (f5b94000 - f6dc2000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525268] microcode: CPU0 sig=0x6fb, pf=0x1, revision=0xb6
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525278] microcode: CPU1 sig=0x6fb, pf=0x1, revision=0xb6
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525368] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525405] Scanning for low memory corruption every 60 seconds
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525778] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525821] Initialise system trusted keyring
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525849] audit: initializing netlink subsys (disabled)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.525871] audit: type=2000 audit(1452104647.524:1): initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.526215] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.528669] zpool: loaded
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.528672] zbud: loaded
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.528763] VFS: Disk quotas dquot_6.5.2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.528819] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.529458] fuse init (API version 7.23)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.529584] msgmni has been set to 1717
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.529665] Key type big_key registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530004] Key type asymmetric registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530008] Asymmetric key parser 'x509' registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530027] bounce: pool size: 64 pages
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530038] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530085] io scheduler noop registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530088] io scheduler deadline registered (default)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530164] io scheduler cfq registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530409] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530468] pcieport 0000:00:1c.0: enabling device (0106 -> 0107)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530548] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530690] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530756] pcieport 0000:00:1c.5: enabling device (0106 -> 0107)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530834] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530937] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.530959] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531048] intel_idle: does not run on family 6 model 15
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531151] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531157] ACPI: Power Button [PWRB]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531214] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531217] ACPI: Power Button [PWRF]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531415] GHES: HEST is not enabled!
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531445] isapnp: Scanning for PnP cards...
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.531535] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.551911] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.553835] Linux agpgart interface v0.103
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.555740] brd: module loaded
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.556630] loop: module loaded
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.556812] ata_piix 0000:00:1f.2: version 2.13
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.556894] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.576017] scsi0 : ata_piix
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.576120] scsi1 : ata_piix
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.576183] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.576186] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.576269] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577274] scsi2 : ata_piix
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577369] scsi3 : ata_piix
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577429] ata3: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb480 irq 22
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577432] ata4: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb488 irq 22
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577552] libphy: Fixed MDIO Bus: probed
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577556] tun: Universal TUN/TAP device driver, 1.6
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577557] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577608] PPP generic driver version 2.4.2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577659] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577665] ehci-pci: EHCI PCI platform driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577767] ehci-pci 0000:00:1a.7: EHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577774] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.577787] ehci-pci 0000:00:1a.7: debug port 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.581685] ehci-pci 0000:00:1a.7: cache line size of 32 is not supported
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.581748] ehci-pci 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592014] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592061] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592064] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592066] usb usb1: Product: EHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592069] usb usb1: Manufacturer: Linux 3.16.0-57-generic ehci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592071] usb usb1: SerialNumber: 0000:00:1a.7
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592207] hub 1-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592215] hub 1-0:1.0: 6 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592495] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592501] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.592514] ehci-pci 0000:00:1d.7: debug port 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.596426] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.596444] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf9fff800
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608014] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608052] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608054] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608057] usb usb2: Product: EHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608059] usb usb2: Manufacturer: Linux 3.16.0-57-generic ehci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608061] usb usb2: SerialNumber: 0000:00:1d.7
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608186] hub 2-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608193] hub 2-0:1.0: 6 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608391] ehci-platform: EHCI generic platform driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608404] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608410] ohci-pci: OHCI PCI platform driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608426] ohci-platform: OHCI generic platform driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608438] uhci_hcd: USB Universal Host Controller Interface driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608529] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608535] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608541] uhci_hcd 0000:00:1a.0: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608568] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c800
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608614] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608617] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608619] usb usb3: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608621] usb usb3: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608624] usb usb3: SerialNumber: 0000:00:1a.0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608747] hub 3-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608754] hub 3-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608943] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608949] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608955] uhci_hcd 0000:00:1a.1: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.608983] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c880
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609033] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609035] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609037] usb usb4: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609040] usb usb4: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609042] usb usb4: SerialNumber: 0000:00:1a.1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609167] hub 4-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609174] hub 4-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609359] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609365] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609371] uhci_hcd 0000:00:1a.2: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609387] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000cc00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609433] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609435] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609438] usb usb5: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609440] usb usb5: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609442] usb usb5: SerialNumber: 0000:00:1a.2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609566] hub 5-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609573] hub 5-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609761] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609768] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609773] uhci_hcd 0000:00:1d.0: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609790] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c080
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609835] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609838] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609840] usb usb6: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609842] usb usb6: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609844] usb usb6: SerialNumber: 0000:00:1d.0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609969] hub 6-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.609976] hub 6-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610160] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610167] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610172] uhci_hcd 0000:00:1d.1: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610198] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610246] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610249] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610251] usb usb7: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610253] usb usb7: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610255] usb usb7: SerialNumber: 0000:00:1d.1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610378] hub 7-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610385] hub 7-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610569] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610576] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610581] uhci_hcd 0000:00:1d.2: detected 2 ports
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610598] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610645] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610647] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610650] usb usb8: Product: UHCI Host Controller
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610652] usb usb8: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610654] usb usb8: SerialNumber: 0000:00:1d.2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610780] hub 8-0:1.0: USB hub found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610787] hub 8-0:1.0: 2 ports detected
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610989] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.610991] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.611529] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.611643] mousedev: PS/2 mouse device common for all mice
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.611798] rtc_cmos 00:01: RTC can wake from S4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.611917] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.611941] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612015] device-mapper: uevent: version 1.0.3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612097] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612124] platform eisa.0: Probing EISA bus 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612127] platform eisa.0: EISA: Cannot allocate resource for mainboard
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612130] platform eisa.0: Cannot allocate resource for EISA slot 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612132] platform eisa.0: Cannot allocate resource for EISA slot 2
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612134] platform eisa.0: Cannot allocate resource for EISA slot 3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612137] platform eisa.0: Cannot allocate resource for EISA slot 4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612139] platform eisa.0: Cannot allocate resource for EISA slot 5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612141] platform eisa.0: Cannot allocate resource for EISA slot 6
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612143] platform eisa.0: Cannot allocate resource for EISA slot 7
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612145] platform eisa.0: Cannot allocate resource for EISA slot 8
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612147] platform eisa.0: EISA: Detected 0 cards
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612162] cpufreq-nforce2: No nForce2 chipset.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612170] ledtrig-cpu: registered to indicate activity on CPUs
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612304] TCP: cubic registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612468] NET: Registered protocol family 10
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612691] NET: Registered protocol family 17
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612704] Key type dns_resolver registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.612928] Using IPI No-Shortcut mode
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.613038] Loading compiled-in X.509 certificates
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.616788] Loaded X.509 cert 'Magrathea: Glacier signing key: 16d7bd9a3dd39a4e65d6d769c5f9f5ddc18b81cb'
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.616806] registered taskstats version 1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.618965] Key type trusted registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.622557] Key type encrypted registered
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.622564] AppArmor: AppArmor sha1 policy hashing enabled
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.622568] ima: No TPM chip found, activating TPM-bypass!
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.622588] evm: HMAC attrs: 0x1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.622937]   Magic number: 0:702:442
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.623020] rtc_cmos 00:01: setting system clock to 2016-01-06 18:24:07 UTC (1452104647)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.623341] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.623343] EDD information not available.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.623411] PM: Hibernation image not present or could not be loaded.
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.884393] isapnp: No Plug & Play device found
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.910616] ata3: SATA link down (SStatus 0 SControl 300)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.914606] ata2: SATA link down (SStatus 0 SControl 300)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    0.921194] ata4: SATA link down (SStatus 0 SControl 300)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.056056] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.078305] ata1.00: ATA-7: WDC WD4000AAKS-00TMA0, 12.01C01, max UDMA/133
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.078308] ata1.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093168] ata1.00: configured for UDMA/133
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093280] scsi 0:0:0:0: Direct-Access     ATA      WDC WD4000AAKS-0 1C01 PQ: 0 ANSI: 5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093492] sd 0:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093532] sd 0:0:0:0: [sda] Write Protect is off
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093536] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093541] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.093554] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.118654]  sda: sda1 sda2 < sda5 >
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.118982] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.119276] Freeing unused kernel memory: 896K (c1a16000 - c1af6000)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.119322] Write protecting the kernel text: 6760k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.119425] Write protecting the kernel read-only data: 2920k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.119427] NX-protecting the kernel data: 5528k
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.130756] systemd-udevd[110]: starting version 204
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.164593] ahci 0000:03:00.0: version 3.0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.169276] scsi4 : pata_marvell
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.169389] scsi5 : pata_marvell
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.169460] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.169462] ata6: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.170036] Floppy drive(s): fd0 is 1.44M
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.183176] atl1 0000:02:00.0: version 2.1.3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.187861] FDC 0 is a post-1991 82077
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.224031] usb 5-2: new low-speed USB device number 2 using uhci_hcd
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.332502] ata5.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB06, max UDMA/33
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.348372] ata5.00: configured for UDMA/33
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.350362] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB06 PQ: 0 ANSI: 5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.368836] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.368840] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.369014] sr 4:0:0:0: Attached scsi CD-ROM sr0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.369187] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.400424] usb 5-2: New USB device found, idVendor=046d, idProduct=c517
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.400428] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.400431] usb 5-2: Product: USB Receiver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.400434] usb 5-2: Manufacturer: Logitech
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.411978] hidraw: raw HID events driver (C) Jiri Kosina
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.461563] usbcore: registered new interface driver usbhid
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.461566] usbhid: USB HID core driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.467390] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.474731] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/0003:046D:C517.0001/input/input3
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.474830] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.474846] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.476181] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/0003:046D:C517.0002/input/input4
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.476358] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input1
Jan  6 18:24:23 dragica-P5K-SE kernel: [    1.524029] tsc: Refined TSC clocksource calibration: 2336.065 MHz
Jan  6 18:24:23 dragica-P5K-SE kernel: [    2.247134] random: init urandom read with 77 bits of entropy available
Jan  6 18:24:23 dragica-P5K-SE kernel: [    2.524083] Switched to clocksource tsc
Jan  6 18:24:23 dragica-P5K-SE kernel: [    3.676323] random: nonblocking pool is initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.553436] Adding 2095100k swap on /dev/sda5.  Priority:-1 extents:1 across:2095100k FS
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.723022] systemd-udevd[283]: starting version 204
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.937148] lp: driver loaded but no devices found
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.948692] coretemp coretemp.0: Using relative temperature scale!
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.948708] coretemp coretemp.0: Using relative temperature scale!
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.959850] w83627ehf: Found W83627DHG chip at 0x290
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.959886] ACPI Warning: SystemIO range 0x0000000000000295-0x0000000000000296 conflicts with OpRegion 0x0000000000000290-0x0000000000000299 (\_SB_.PCI0.SBRG.SIOR.HWRE) (20140424/utaddress-254)
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.959893] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.961403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.988772] ppdev: user-space parallel port driver
Jan  6 18:24:23 dragica-P5K-SE kernel: [   13.997290] [drm] Initialized drm 1.1.0 20060810
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.260592] gpio_ich: GPIO from 195 to 255 on gpio_ich
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.323646] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346237] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346242] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346244] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346247] sound hdaudioC0D0:    mono: mono_out=0x0
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346249] sound hdaudioC0D0:    dig-out=0x1e/0x0
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346251] sound hdaudioC0D0:    inputs:
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346253] sound hdaudioC0D0:      Front Mic=0x19
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346256] sound hdaudioC0D0:      Rear Mic=0x18
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.346258] sound hdaudioC0D0:      Line=0x1a
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.359815] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.359910] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.359997] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.360093] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.360178] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.360265] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.360349] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.360432] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384365] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384412] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384455] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384498] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384540] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384583] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384626] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384669] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384712] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384754] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384797] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384840] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.384883] systemd-udevd[305]: Error calling EVIOCSKEYCODE: Invalid argument
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404115] audit: type=1400 audit(1452101061.278:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=350 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404123] audit: type=1400 audit(1452101061.278:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=350 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404129] audit: type=1400 audit(1452101061.278:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=350 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404141] audit: type=1400 audit(1452101061.278:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=344 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404148] audit: type=1400 audit(1452101061.278:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=344 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404154] audit: type=1400 audit(1452101061.278:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=344 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404643] audit: type=1400 audit(1452101061.278:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=350 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404648] audit: type=1400 audit(1452101061.278:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=350 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404668] audit: type=1400 audit(1452101061.278:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=344 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   14.404674] audit: type=1400 audit(1452101061.278:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=344 comm="apparmor_parser"
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.554817] nvidia: module license 'NVIDIA' taints kernel.
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.554821] Disabling lock debugging due to kernel taint
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.564730] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.571143] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.571894] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
Jan  6 18:24:23 dragica-P5K-SE kernel: [   15.571905] NVRM: loading NVIDIA UNIX x86 Kernel Module  340.96  Sun Nov  8 21:45:55 PST 2015
Jan  6 18:24:23 dragica-P5K-SE kernel: [   16.219191] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan  6 18:24:23 dragica-P5K-SE kernel: [   16.562607] init: failsafe main process (600) killed by TERM signal
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.043873] Bluetooth: Core ver 2.19
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.043896] NET: Registered protocol family 31
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.043898] Bluetooth: HCI device and connection manager initialized
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: DIS cannot start: GATT is disabled
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init deviceinfo plugin
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init proximity plugin
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init time plugin
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init alert plugin
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init thermometer plugin
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.044216] Bluetooth: HCI socket layer initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.044220] Bluetooth: L2CAP socket layer initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.044232] Bluetooth: SCO socket layer initialized
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Failed to init gatt_example plugin
Jan  6 18:24:23 dragica-P5K-SE bluetoothd[700]: Bluetooth Management interface initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.057487] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.057491] Bluetooth: BNEP filters: protocol multicast
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.057499] Bluetooth: BNEP socket layer initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.076340] Bluetooth: RFCOMM TTY layer initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.076351] Bluetooth: RFCOMM socket layer initialized
Jan  6 18:24:23 dragica-P5K-SE kernel: [   17.076358] Bluetooth: RFCOMM ver 1.11
Jan  6 18:24:24 dragica-P5K-SE rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jan  6 18:24:24 dragica-P5K-SE ntpdate[649]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jan  6 18:24:24 dragica-P5K-SE ntpdate[649]: no servers can be used, exiting
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Successfully dropped root privileges.
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: avahi-daemon 0.6.31 starting up.
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Successfully called chroot().
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Successfully dropped remaining capabilities.
Jan  6 18:24:24 dragica-P5K-SE kernel: [   17.641247] init: cups main process (744) killed by HUP signal
Jan  6 18:24:24 dragica-P5K-SE kernel: [   17.641260] init: cups main process ended, respawning
Jan  6 18:24:24 dragica-P5K-SE ModemManager[704]: <info>  ModemManager (version 1.0.0) starting...
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: No service file found in /etc/avahi/services.
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Network interface enumeration completed.
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  6 18:24:24 dragica-P5K-SE avahi-daemon[782]: Server startup complete. Host name is dragica-P5K-SE.local. Local service cookie is 1071909024.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> NetworkManager (version 0.9.8.8) is starting...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> WEXT support is enabled
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> DNS: loaded plugin dnsmasq
Jan  6 18:24:25 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan  6 18:24:25 dragica-P5K-SE polkitd[817]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jan  6 18:24:25 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: init!
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: update_system_hostname
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:       interface-parser: parsing file /etc/network/interfaces
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:       interface-parser: finished parsing file /etc/network/interfaces
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPluginIfupdown: management mode: unmanaged
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: end _init.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ofono: init!
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ofono: end _init.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Loaded plugin (null): (null)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    Ifupdown: get unmanaged devices count: 0
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: (158238552) ... get_connections.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ifupdown: (158238552) ... get_connections (managed=false): return empty list.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ofono: (158282776) ... get_connections.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    SCPlugin-Ofono: (158282776) connections count: 0
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]:    Ifupdown: get unmanaged devices count: 0
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Networking is enabled by state file
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <warn> failed to allocate link cache: (-12) Object not found
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): carrier is OFF
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): new Ethernet device (driver: 'atl1' ifindex: 2)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): bringing up device.
Jan  6 18:24:25 dragica-P5K-SE kernel: [   18.703803] atl1 0000:02:00.0: irq 45 for MSI/MSI-X
Jan  6 18:24:25 dragica-P5K-SE kernel: [   18.703867] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
Jan  6 18:24:25 dragica-P5K-SE kernel: [   18.703919] atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): carrier now ON (device state 20)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): preparing device.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Added default wired connection 'Ži&#269;na povezava 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> urfkill disappeared from the bus
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Auto-activating connection 'Ži&#269;na povezava 1'.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) starting connection 'Ži&#269;na povezava 1'
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> NetworkManager state is now CONNECTING
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> dhclient started with pid 848
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Beginning IP6 addrconf.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> ModemManager available in the bus
Jan  6 18:24:25 dragica-P5K-SE dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan  6 18:24:25 dragica-P5K-SE dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan  6 18:24:25 dragica-P5K-SE dhclient: All rights reserved.
Jan  6 18:24:25 dragica-P5K-SE dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 18:24:25 dragica-P5K-SE dhclient: 
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  6 18:24:25 dragica-P5K-SE dhclient: Listening on LPF/eth0/00:1b:fc:d5:11:54
Jan  6 18:24:25 dragica-P5K-SE dhclient: Sending on   LPF/eth0/00:1b:fc:d5:11:54
Jan  6 18:24:25 dragica-P5K-SE dhclient: Sending on   Socket/fallback
Jan  6 18:24:25 dragica-P5K-SE dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x3534c53d)
Jan  6 18:24:25 dragica-P5K-SE dhclient: DHCPREQUEST of 192.168.1.9 on eth0 to 255.255.255.255 port 67 (xid=0x3dc53435)
Jan  6 18:24:25 dragica-P5K-SE dhclient: DHCPOFFER of 192.168.1.9 from 192.168.1.1
Jan  6 18:24:25 dragica-P5K-SE dhclient: DHCPACK of 192.168.1.9 from 192.168.1.1
Jan  6 18:24:25 dragica-P5K-SE dhclient: bound to 192.168.1.9 -- renewal in 33952 seconds.
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info>   address 192.168.1.9
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info>   prefix 24 (255.255.255.0)
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info>   gateway 192.168.1.1
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info>   nameserver '192.168.1.1'
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info>   domain name 'Home'
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan  6 18:24:25 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jan  6 18:24:25 dragica-P5K-SE avahi-daemon[782]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.9.
Jan  6 18:24:25 dragica-P5K-SE avahi-daemon[782]: New relevant interface eth0.IPv4 for mDNS.
Jan  6 18:24:25 dragica-P5K-SE avahi-daemon[782]: Registering new address record for 192.168.1.9 on eth0.IPv4.
Jan  6 18:24:25 dragica-P5K-SE nvidia-persistenced: Started (914)
Jan  6 18:24:25 dragica-P5K-SE nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 124 has read and write permissions for those files.
Jan  6 18:24:25 dragica-P5K-SE nvidia-persistenced: Shutdown (914)
Jan  6 18:24:25 dragica-P5K-SE cron[858]: (CRON) INFO (pidfile fd = 3)
Jan  6 18:24:25 dragica-P5K-SE acpid: starting up with netlink and the input layer
Jan  6 18:24:25 dragica-P5K-SE anacron[920]: Anacron 2.3 started on 2016-01-06
Jan  6 18:24:26 dragica-P5K-SE cron[925]: (CRON) STARTUP (fork ok)
Jan  6 18:24:26 dragica-P5K-SE cron[925]: (CRON) INFO (Running @reboot jobs)
Jan  6 18:24:26 dragica-P5K-SE anacron[920]: Normal exit (0 jobs run)
Jan  6 18:24:26 dragica-P5K-SE kernel: [   19.350651] init: samba-ad-dc main process (821) terminated with status 1
Jan  6 18:24:26 dragica-P5K-SE acpid: 9 rules loaded
Jan  6 18:24:26 dragica-P5K-SE acpid: waiting for events: event logging is off
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> Policy set 'Ži&#269;na povezava 1' (eth0) as default for IPv4 routing and DNS.
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> DNS: starting dnsmasq...
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <warn> dnsmasq not available on the bus, can't update servers.
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <error> [1452101066.811360] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <warn> DNS: plugin dnsmasq update failed
Jan  6 18:24:26 dragica-P5K-SE NetworkManager[811]: <info> Writing DNS information to /sbin/resolvconf
Jan  6 18:24:26 dragica-P5K-SE ModemManager[704]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0': not supported by any plugin
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: started, version 2.68 cache disabled
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: DBus support enabled: connected to system bus
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: warning: no upstream servers configured
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21b:fcff:fed5:1154.
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: New relevant interface eth0.IPv6 for mDNS.
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: Registering new address record for fe80::21b:fcff:fed5:1154 on eth0.*.
Jan  6 18:24:27 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: Got SIGTERM, quitting.
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21b:fcff:fed5:1154.
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.9.
Jan  6 18:24:27 dragica-P5K-SE avahi-daemon[782]: avahi-daemon 0.6.31 exiting.
Jan  6 18:24:27 dragica-P5K-SE avahi: Avahi detected that your currently configured local DNS server serves
Jan  6 18:24:27 dragica-P5K-SE avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jan  6 18:24:27 dragica-P5K-SE avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jan  6 18:24:27 dragica-P5K-SE avahi: contact your administrator and convince him to use a different DNS domain,
Jan  6 18:24:27 dragica-P5K-SE avahi: since .local should be used exclusively for Zeroconf technology.
Jan  6 18:24:27 dragica-P5K-SE avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jan  6 18:24:27 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) successful, device activated.
Jan  6 18:24:27 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  6 18:24:27 dragica-P5K-SE NetworkManager[811]: <warn> dnsmasq appeared on DBus: :1.11
Jan  6 18:24:27 dragica-P5K-SE NetworkManager[811]: <info> Writing DNS information to /sbin/resolvconf
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: setting upstream servers from DBus
Jan  6 18:24:27 dragica-P5K-SE dnsmasq[1023]: using nameserver 192.168.1.1#53
Jan  6 18:24:27 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  6 18:24:27 dragica-P5K-SE accounts-daemon[1105]: started daemon version 0.6.35
Jan  6 18:24:27 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> dhclient started with pid 1249
Jan  6 18:24:28 dragica-P5K-SE dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan  6 18:24:28 dragica-P5K-SE dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan  6 18:24:28 dragica-P5K-SE dhclient: All rights reserved.
Jan  6 18:24:28 dragica-P5K-SE dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 18:24:28 dragica-P5K-SE dhclient: 
Jan  6 18:24:28 dragica-P5K-SE dhclient: Bound to *:546
Jan  6 18:24:28 dragica-P5K-SE dhclient: Listening on Socket/eth0
Jan  6 18:24:28 dragica-P5K-SE dhclient: Sending on   Socket/eth0
Jan  6 18:24:28 dragica-P5K-SE kernel: [   21.746855] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
Jan  6 18:24:28 dragica-P5K-SE nvidia-persistenced: Started (1253)
Jan  6 18:24:28 dragica-P5K-SE dhclient: XMT: Info-Request on eth0, interval 1050ms.
Jan  6 18:24:28 dragica-P5K-SE dhclient: RCV: Reply message on eth0 from fe80::666e:eaff:fe10:3477.
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> (eth0): DHCPv6 state changed nbi -> renew6
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info>   nameserver '2a00:ee0:d::13'
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info>   nameserver '2a00:ee0:d::55'
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) scheduled...
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> (eth0): DHCPv6 client pid 1249 exited with status 0
Jan  6 18:24:28 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) started...
Jan  6 18:24:29 dragica-P5K-SE acpid: client connected from 1101[0:0]
Jan  6 18:24:29 dragica-P5K-SE acpid: 1 client rule loaded
Jan  6 18:24:29 dragica-P5K-SE NetworkManager[811]: <info> Policy set 'Ži&#269;na povezava 1' (eth0) as default for IPv6 routing and DNS.
Jan  6 18:24:29 dragica-P5K-SE NetworkManager[811]: <info> Writing DNS information to /sbin/resolvconf
Jan  6 18:24:29 dragica-P5K-SE dnsmasq[1023]: setting upstream servers from DBus
Jan  6 18:24:29 dragica-P5K-SE dnsmasq[1023]: using nameserver 192.168.1.1#53
Jan  6 18:24:29 dragica-P5K-SE dnsmasq[1023]: using nameserver 2a00:ee0:d::55#53
Jan  6 18:24:29 dragica-P5K-SE kernel: [   22.861690] init: plymouth-upstart-bridge main process ended, respawning
Jan  6 18:24:29 dragica-P5K-SE NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) complete.
Jan  6 18:24:31 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan  6 18:24:31 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan  6 18:24:31 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Successfully called chroot.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Successfully dropped privileges.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Successfully limited resources.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Running.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1385 of process 1385 (n/a) owned by '112' high priority at nice level -11.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Watchdog thread running.
Jan  6 18:24:31 dragica-P5K-SE rtkit-daemon[1387]: Canary thread running.
Jan  6 18:24:31 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan  6 18:24:32 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jan  6 18:24:32 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jan  6 18:24:32 dragica-P5K-SE anacron[1481]: Anacron 2.3 started on 2016-01-06
Jan  6 18:24:32 dragica-P5K-SE anacron[1481]: Normal exit (0 jobs run)
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1513 of process 1385 (n/a) owned by '112' RT at priority 5.
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1517 of process 1385 (n/a) owned by '112' RT at priority 5.
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1525 of process 1525 (n/a) owned by '112' high priority at nice level -11.
Jan  6 18:24:32 dragica-P5K-SE rtkit-daemon[1387]: Supervising 4 threads of 2 processes of 1 users.
Jan  6 18:24:32 dragica-P5K-SE pulseaudio[1525]: [pulseaudio] pid.c: Daemon already running.
Jan  6 18:24:32 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jan  6 18:24:32 dragica-P5K-SE colord: Using config file /etc/colord.conf
Jan  6 18:24:32 dragica-P5K-SE colord: Using mapping database file /var/lib/colord/mapping.db
Jan  6 18:24:32 dragica-P5K-SE colord: Using device database file /var/lib/colord/storage.db
Jan  6 18:24:32 dragica-P5K-SE colord: loaded plugin libcd_plugin_scanner.so
Jan  6 18:24:32 dragica-P5K-SE colord: loaded plugin libcd_plugin_camera.so
Jan  6 18:24:32 dragica-P5K-SE colord: plugin /usr/lib/i386-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jan  6 18:24:32 dragica-P5K-SE colord: Daemon ready for requests
Jan  6 18:24:32 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-82f5d16fcef1fbd987b6a82c94104464
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-fd79463e1808f0d8ea7a8f7eefd3256b
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-94ec9a8cbcf45963ef9bfbe80b33e02f
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-fb41735d46e9e2c5b7dfa641160c3393
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-50e7bd95c5a7d850b2051ad93a63906d
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-8b73141bce6d164037dd46000bafb2a2
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-56cc29b73a685afb027a630b6d5057dc
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-2ee6b6114ddeed0d4f61e0211c23427b
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-288a6f2c3bb54a1d2a29221c9caf5011
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-3c54e22f77a8f6175941c3f39f1029f9
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-b2016991d9b9c2cf940a251d1441c7fc
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-ccebee4c2d6eddc597c1425ac2f128b1
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jan  6 18:24:32 dragica-P5K-SE colord: Device added: xrandr-Lenovo Group Limited-LEN L220xwC-VL-42034
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-28e5af7c5dc371860e60482a37860984
Jan  6 18:24:32 dragica-P5K-SE colord: Automatic metadata add icc-57d815ea36c0147efbc30390acfae68c to xrandr-Lenovo Group Limited-LEN L220xwC-VL-42034
Jan  6 18:24:32 dragica-P5K-SE colord: Profile added: icc-57d815ea36c0147efbc30390acfae68c
Jan  6 18:24:34 dragica-P5K-SE ntpdate[1225]: step time server 91.189.94.4 offset 0.849707 sec
Jan  6 18:24:36 dragica-P5K-SE NetworkManager[811]: <info> WiFi hardware radio set enabled
Jan  6 18:24:39 dragica-P5K-SE colord: device removed: xrandr-Lenovo Group Limited-LEN L220xwC-VL-42034
Jan  6 18:24:39 dragica-P5K-SE colord: Profile removed: icc-28e5af7c5dc371860e60482a37860984
Jan  6 18:24:39 dragica-P5K-SE colord: Profile removed: icc-57d815ea36c0147efbc30390acfae68c
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1931 of process 1931 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Supervising 4 threads of 2 processes of 2 users.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1972 of process 1931 (n/a) owned by '1000' RT at priority 5.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Supervising 5 threads of 2 processes of 2 users.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1973 of process 1931 (n/a) owned by '1000' RT at priority 5.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Supervising 6 threads of 2 processes of 2 users.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1975 of process 1975 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Supervising 7 threads of 3 processes of 2 users.
Jan  6 18:24:41 dragica-P5K-SE pulseaudio[1975]: [pulseaudio] pid.c: Daemon already running.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Successfully made thread 1978 of process 1978 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 18:24:41 dragica-P5K-SE rtkit-daemon[1387]: Supervising 7 threads of 3 processes of 2 users.
Jan  6 18:24:41 dragica-P5K-SE pulseaudio[1978]: [pulseaudio] pid.c: Daemon already running.
Jan  6 18:24:41 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jan  6 18:24:41 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan  6 18:24:41 dragica-P5K-SE colord: Device added: xrandr-Lenovo Group Limited-LEN L220xwC-VL-42034
Jan  6 18:24:42 dragica-P5K-SE colord: Profile added: icc-7b6278a62d7728d34eea6c7572045dc0
Jan  6 18:24:42 dragica-P5K-SE colord: Automatic metadata add icc-45b38598603f53c0e071e8c378be3b90 to xrandr-Lenovo Group Limited-LEN L220xwC-VL-42034
Jan  6 18:24:42 dragica-P5K-SE colord: Profile added: icc-45b38598603f53c0e071e8c378be3b90
Jan  6 18:24:42 dragica-P5K-SE dbus[633]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jan  6 18:24:42 dragica-P5K-SE udisksd[2052]: udisks daemon version 2.1.3 starting
Jan  6 18:24:42 dragica-P5K-SE dbus[633]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jan  6 18:24:42 dragica-P5K-SE udisksd[2052]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jan  6 18:24:54 dragica-P5K-SE kernel: [   47.248608] audit_printk_skb: 168 callbacks suppressed
Jan  6 18:24:54 dragica-P5K-SE kernel: [   47.248612] audit: type=1400 audit(1452101094.972:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2189 comm="apparmor_parser"
Jan  6 18:24:54 dragica-P5K-SE kernel: [   47.248622] audit: type=1400 audit(1452101094.972:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2189 comm="apparmor_parser"
Jan  6 18:24:54 dragica-P5K-SE kernel: [   47.249136] audit: type=1400 audit(1452101094.972:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2189 comm="apparmor_parser"
Jan  6 18:25:12 dragica-P5K-SE gnome-session[1782]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Jan  6 18:25:20 dragica-P5K-SE dbus[633]: [system] Failed to activate service 'org.freedesktop.Avahi': timed out
```

---

### Post by Yellow Pasque on 2016-01-06
```
Linux version 3.16.0-57-generic
```

Have you tried the 3.19.x kernel from the vivid-lts series?

---

### Post by messner on 2016-01-06
> **Temüjin said:**
>  Have you tried the 3.19.x kernel from the vivid-lts series?

Why do you think this could help ?

Should I try to install it with:

```
sudo apt-get install linux-generic-lts-vivid
```

One more interesting thing. When the system crashes and gets into strange behavior, I ha tried to help myself with Fedora live. The system boot marvelous and when I shutdown Fedora (running on the USB) and reboot Ubuntu, the system again goes into the strange mode.

Ubuntu somehow sets the system in wrong mode. I am not totaly sue what gets the system out of this mode, but when it does (after a lot of reboot and trying to do strange things) the system again behaves totaly normal.

---

### Post by Yellow Pasque on 2016-01-06
> Why do you think this could help ?
Bugs get fixed..

---

### Post by messner on 2016-01-10
This command makes the system practically unusable ...

```
sudo apt-get install linux-generic-lts-vivid
```

I removed this kernel.

---

### Post by mörgæs on 2016-01-12
It's not a guarantee but I would try a fresh install of 15.10 using both open- and closed-source drivers.

---

### Post by messner on 2016-01-13
Thank you for your info ...

I have bought an AMD graphic card and I will try to use this new card. Thank you for all the answers and hints, I will let you know how this ends ....

I.

---

