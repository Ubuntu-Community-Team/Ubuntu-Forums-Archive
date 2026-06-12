---
title: "Mounting a SCSI Printer"
date: 2010-03-03
forum: Hardware
---

### Post by thisispeace on 2010-03-03
I found an old Sony UP-D2600S SpectaPix digital printer sitting in a dumpster, still unopened and in it's original packaging from 1999.  

Trouble is, it's SCSI and isn't recognized when I search for printers to add, and I do not know how to safely experiment with mounting something like this.  I have a Dell Precision 360 Workstation, and the printer is connected to the **AIC-7892A U160/m** card.  The printer is set to be the SCSI Terminator, and it's SCSI ID is 001b.

Here's my hardware profile:

```
bmunden@ubuntu:~$ sudo lshw
[sudo] password for bmunden: 
ubuntu                    
    description: Mini Tower Computer
    product: Precision WorkStation 360
    vendor: Dell Computer Corporation
    serial: 6QPPK31
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-5100-1050-8050-B6C04F4B3331
  *-core
       description: Motherboard
       product: 0H1639
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN4811138H02ZS.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A02 (07/21/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 2
             slot: CHANNEL A DIMM 1
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns) [empty]
             physical id: 3
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fd000000-feafffff memory:f0000000-f7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV18GL [Quadro NVS 280 SD]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fd000000-fdffffff memory:f0000000-f7ffffff(prefetchable) memory:fea00000-fea1ffff(prefetchable)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fce00000-fcffffff memory:20000000-200fffff(prefetchable)
           *-scsi:0
                description: SCSI storage controller
                product: AHA-2940U/UW/D / AIC-7881U
                vendor: Adaptec
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: scsi4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: scsi bus_master rom scsi-host
                configuration: driver=aic7xxx latency=64 maxlatency=8 mingnt=8
                resources: irq:21 ioport:dd00(size=256) memory:fcede000-fcedefff memory:20020000-2002ffff(prefetchable)
           *-scsi:1
                description: SCSI storage controller
                product: AIC-7892A U160/m
                vendor: Adaptec
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: scsi6
                version: 02
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list rom scsi-host
                configuration: driver=aic7xxx latency=64 maxlatency=25 mingnt=40
                resources: irq:22 ioport:de00(size=256) memory:fcedf000-fcedffff memory:20000000-2001ffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 02
                serial: 00:07:e9:51:ad:1b
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=128.46.190.174 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
                resources: irq:18 memory:fcee0000-fcefffff ioport:dcc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:febffc00-febfffff
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW  CRX216E
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: PD01
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   capabilities: partitioned partitioned:mac
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
                 *-volume:0 UNCLAIMED
                      description: Apple partition map
                      physical id: 1
                      capacity: 1KiB
                 *-volume:1 UNCLAIMED
                      description: Apple HFS
                      physical id: 2
                      size: 56MiB
                      capacity: 56MiB
                      capabilities: hfs initialized
                      configuration: created=1999-05-10 12:07:03 filesystem=hfs label=PRINTER DRIVER UP-D2600S modified=1999-09-14 10:56:00 state=clean
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk
                description: ATA Disk
                product: ST3500418AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: CC34
                serial: 6VM32VRT
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=885d885d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   version: 3.1
                   serial: 229d70f5-d9b8-a144-9cb2-86839b2b7911
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-09 05:15:56 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 80da2a40-a6bc-334d-b2d8-b3c9f9ce5581
                   size: 368GiB
                   capacity: 368GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-02-09 10:35:58 filesystem=ntfs label=New Volume state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:febffa00-febffbff memory:febff900-febff9ff

```

---

