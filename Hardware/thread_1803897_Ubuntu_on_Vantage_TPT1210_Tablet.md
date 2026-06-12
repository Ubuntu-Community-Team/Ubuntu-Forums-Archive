---
title: "Ubuntu on Vantage TPT1210 Tablet"
date: 2011-07-14
forum: Hardware
---

### Post by CJay554 on 2011-07-14
Hey everyone, i have my hands on a Vantage TPT1210 tablet PC, it uses windows XP as its default but its very limited as far as touch screen software avaiable, my ultimate goal is to turn this luxury home control tablet into a student tool in my journey through college.

EVERYTHING WORKS FINE!

except... the touchscreen. When i put pressure anywhere on the screen (it is pressure sensitive not capacitive) the mouse will do a very random dance across all axis of the screen, random jumping everywhere, it just goes crazy. Now i know for a fact they use quite a rare set of hardware as they are a small company and look for the best money saving ideals rather than dependable hardware. I have set up HP TX1000 tablets, and countless other touch screen devices with ubuntu, but this one just takes the cake... far far away. Does anyone have any idea where to begin here? I will copy my lshw and my xinput list so you can further see the system, I cannot for the life of me identify the tablet manufacturer...


lshw:
```

    description: Desktop Computer
    version: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: VANTAGE
       physical id: 0
       version: 5678
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080013
          date: 07/01/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        443  @ 1.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: CPU 1
          size: 1200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
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
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:feb80000-febfffff ioport:ec80(size=8) memory:d0000000-dfffffff memory:feb40000-feb7ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fea80000-feafffff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:feb38000-feb3bfff
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
             resources: irq:40 ioport:1000(size=4096) memory:fe400000-fe8fffff ioport:3f800000(size=2097152)
           *-network
                description: Ethernet interface
                product: ET-131x PCI-E Ethernet Controller
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 03
                serial: 00:40:45:30:fa:0f
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=et131x latency=0 multicast=yes
                resources: irq:16 memory:fe600000-fe7fffff memory:fe8e0000-fe8fffff
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
             resources: irq:41 ioport:2000(size=4096) memory:fe300000-fe3fffff ioport:3fa00000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:1c:bf:bb:cf:d2
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.17 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:43 memory:fe3ff000-fe3fffff
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
             resources: irq:23 ioport:dc00(size=32)
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
             resources: irq:19 ioport:dc80(size=32)
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
             resources: irq:18 ioport:e000(size=32)
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
             resources: irq:16 ioport:e080(size=32)
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
             resources: irq:23 memory:feb3f800-feb3fbff
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
             resources: ioport:c000(size=4096) memory:fda00000-fe2fffff ioport:bdf00000(size=33554432)
           *-pcmcia
                description: CardBus bridge
                product: OZ711MP1/MS1 MemoryCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=195
                resources: irq:16 memory:fda00000-fda00fff ioport:c000(size=256) ioport:c400(size=256) memory:40000000-43ffffff memory:44000000-47ffffff
           *-generic UNCLAIMED
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64
                resources: memory:fe2fe400-fe2fe4ff
           *-bridge UNCLAIMED
                description: Bridge
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.3
                bus info: pci@0000:01:04.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bridge pm cap_list
                configuration: latency=64
                resources: memory:fe2fd000-fe2fdfff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 4.4
                bus info: pci@0000:01:04.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:16 memory:fda01000-fda01fff memory:fe2fe800-fe2fefff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:feb3fc00-feb3ffff
           *-disk
                description: ATA Disk
                product: FUJITSU MHY2080B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K402T7C28RM6
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d8def77b
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   version: 3.1
                   serial: 52d60544-d3af-694c-a810-644678c9f86f
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-05-15 04:39:11 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
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
             resources: ioport:400(size=32)
```


xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```


my question is, is it logitech? or is it even being identified by ubuntu? if not why is it responding? wacom evtouch to no avail, and other countless drivers, let me know if you have any ideas, consider this device your Guinea pig! I'm not afraid to break it! (software of course)

---

### Post by CJay554 on 2011-07-14
Further Digging in the Windows XP install i discover it is a "TouchSet PS/2 Touch Panel Controller"

I found a website for its drivers which include linux packages, let's hope for the best, i'll keep this updated with my progress!

---

### Post by CJay554 on 2011-07-14
Out of luck, it seems like most of the dependencies in the linux packages require old packages, such that which used to be included in Ubuntu 7.04 and before... Seems they haven't updated their drivers in a while...

---

