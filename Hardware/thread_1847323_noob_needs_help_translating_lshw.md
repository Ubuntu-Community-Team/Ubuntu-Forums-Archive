---
title: "noob needs help translating lshw"
date: 2011-09-20
forum: Hardware
---

### Post by jrschrock on 2011-09-20
Hello, I got a printout of all my hardware devices and there were several messages I didn't understand, but sound like I should do something about them. Wondering if one of you fine folks could point me in the right direction...

1. "BIOSEEPROM can be upgraded"
2. Display Controller "this device hasn't been claimed"
3. SMBus "This device hasn't been claimed"

I attached screen shots of all three if that helps. Thanks!

---

### Post by .... on 2011-09-20
Please use text for this kind of thing. Post the output of:
```
sudo lshw
```

---

### Post by jrschrock on 2011-09-20
> **.... said:**
> Please use text for this kind of thing. Post the output of:
```
sudo lshw
```

Not sure if this is what you meant by that, but here goes..

jrschrock@Jeremy:~$ sudo lshw
[sudo] password for jrschrock: 
jeremy                    
    description: Notebook
    version: V1.02
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=NetTopSku uuid=9CE64E36-829C-B19C-2111-88AE1D068A72
  *-core
       description: Motherboard
       product: AO533
       vendor: Acer
       physical id: 0
       version: V1.02
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.02
          date: 05/07/2010
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: 000000000000000000000000000000000000
             vendor: 0000000000000000
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 1GiB
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1d
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU
          size: 1666MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 667MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache:0
             description: L2 cache
             physical id: 1e
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1f
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
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
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:58180000-581fffff ioport:60c0(size=8) memory:40000000-4fffffff memory:58000000-580fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:58100000-5817ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:58200000-58203fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:57000000-57ffffff ioport:50000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c1
                serial: 88:ae:1d:06:8a:72
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:57000000-5703ffff ioport:5000(size=128)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:56000000-56ffffff ioport:51000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 78:e4:00:b9:24:f3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:56000000-5600ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:6080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:6060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:58204400-582047ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:60b8(size=8) ioport:60cc(size=4) ioport:60b0(size=8) ioport:60c8(size=4) ioport:60a0(size=16) memory:58204000-582043ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXC1A4072228
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000af63f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1a805a54-f2d3-491d-8f16-8b78a8c0500a
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-26 02:54:30 filesystem=ext4 lastmountpoint=/ modified=2011-09-17 05:44:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-09-20 17:15:59 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1012MiB
                   capacity: 1012MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1012MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:6000(size=32)
jrschrock@Jeremy:~$

---

### Post by Metaxa on 2011-09-20
Acer machine <---Manufacturer

1GB ram DDR3 @ 667Mhz <---Amount and type of ram

Intel Atom Processor @ 1.66 Ghz <---Processor type

N10 Family Integrated Graphics Controller <---- Video card

N10/ICH 7 Family High Definition Audio Controller <----Sound Card

AR8152 v1.1 Fast Ethernet <-----Ethernet controller

AR9285 Wireless Network Adapter (PCI-Express) <---Wireless card

N10/ICH 7 Family USB UHCI Controller #1 <----USB control (Intel)

WDC WD2500BEVT-2 <--- Hard Drive type (Western Digital 230GB)



Generic terms were used for clarification.


Hopes that helps

regards,

Metaxa

---

### Post by .... on 2011-09-20
> 1. "BIOSEEPROM can be upgraded"
2. Display Controller "this device hasn't been claimed"
3. SMBus "This device hasn't been claimed"2 & 3 are benign/unimportant. You may want to update the BIOS, but it will require Windows or FreeDOS because Acer isn't cross-platform friendly. I personally would not mess with the BIOS unless I was having issues.

---

### Post by jrschrock on 2011-09-21
OK, thanks. That's good enough for me.

---

