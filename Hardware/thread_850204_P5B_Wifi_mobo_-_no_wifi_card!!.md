---
title: "P5B Wifi mobo - no wifi card!!"
date: 2008-07-05
forum: Hardware
---

### Post by diafanos on 2008-07-05
Hello there,
I have an asus p5b deluxe wifi-ap mobo.

These days I tried to install a wireless network, but no matter what I do my system does not detect the usb wifi card!

Yesterday I tried the same through windows, but nether windows detect it!
(In BIOS, Wifi is enabled)

Do you think that I have a faulty mobo? 
Is there any way to verify it (through BIOS maybe) or should I send it for repair?

Thanx in advance.

---

### Post by pytheas22 on 2008-07-05
What is the output in Linux of:
```

lshw -C Network
lspci
lsusb
```

If the output mentions your wireless device, then it's *probably* not faulty; it just needs a driver to run (in Windows and Linux).  If lsusb doesn't see your device at all, chances are that there's a hardware problem.

---

### Post by diafanos on 2008-07-05
lshw -C network output:

```

*-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 12
       serial: 00:18:f3:5e:7b:c1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:5e:4a:38
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=10.0.0.13 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s

```

nothing about wireless card, just the two ethernet ones...
It's a hardware problem, isn't it?

@pytheas22 
thanks

---

### Post by avtolle on 2008-07-05
What does ```
lsusb
```show?

---

### Post by diafanos on 2008-07-05
lsusb output:

> 
Bus 004 Device 003: ID 045e:00d1 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  


I barely understand what are all these...:confused:

---

### Post by starcannon on 2008-07-05
I googled those device ID's and I think:

> Bus 004 Device 003: ID 045e:00d1 Microsoft Corp. 

is a Microsoft USB Comfort Optical Mouse.

and
> Bus 003 Device 003: ID 045e:00dd Microsoft Corp.  

is a Microsoft USB Keyboard.

The device ID's that come up as 0000:0000 are just empty usb ports.

I would try plugging your usb wifi device into a different USB port, avoid using a usb hub for now.

---

### Post by pytheas22 on 2008-07-05
Yes, as starcannon says, it could just be a bad USB port, not a bad device.  Try plugging it in all the different USB ports and run the lsusb command on each one.  If you see anything in the lsusb output besides the two Microsoft devices, then that's good.  Otherwise, there's probably a problem.

You could also look at the output of dmesg (just type "dmesg | tail" after plugging the wireless device in) in a terminal) to see if it notices anything when you plug the wifi card in...it may notice that something gets plugged in but give errors about trying to communicate with it, which could be another indication  of hardware failure.

You could also try your USB device in another computer.  But at this point, if neither Linux nor Windows is able to see your device at all, I'd blame bad hardware.

---

### Post by diafanos on 2008-07-06
thank you all for your suggestions, 

but my wifi card is not just plugged in a usb port, is somehow connected with the motherboard, so I can't extract it without damaging it..

I'll give it a try, though...

---

### Post by starcannon on 2008-07-06
Lets get all the hardware listed, and see whats there:

```
sudo lshw > ~/Desktop/hardware_list.txt
```

Then attach the "hardware_list.txt" file to a forum reply.

GL

---

### Post by diafanos on 2008-07-06
ok. **lshw** output:
```

    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=C0DE0D3F-8EFE-D511-98E0-0018F35E7BC1
  *-core
       description: Motherboard
       product: P5B-Deluxe
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0507 (08/10/2006)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: To Be Filled By O.E.M.
          slot: LGA 775
          size: 2128MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
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
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 43
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-generic:0 UNCLAIMED
          physical id: 2005
          bus info: parisc@2005
        *-generic:0 UNCLAIMED
             physical id: 4
             bus info: parisc@04
           *-generic UNCLAIMED
                physical id: 23
                bus info: parisc@23
        *-generic:1 UNCLAIMED
             physical id: 6
             bus info: parisc@06
           *-generic UNCLAIMED
                physical id: 9
                bus info: parisc@09
     *-generic:1 UNCLAIMED
          physical id: 2006
          bus info: parisc@2006
        *-generic UNCLAIMED
             physical id: 7
             bus info: parisc@07
           *-generic UNCLAIMED
                physical id: 23
                bus info: parisc@23
     *-generic:2 UNCLAIMED
          physical id: 2008
          bus info: parisc@2008
        *-generic:0 UNCLAIMED
             physical id: 1
             bus info: parisc@01
           *-generic:0 UNCLAIMED
                physical id: 18
                bus info: parisc@18
           *-generic:1 UNCLAIMED
                physical id: 22
                bus info: parisc@22
        *-generic:1 UNCLAIMED
             physical id: 2
             bus info: parisc@02
           *-generic:0 UNCLAIMED
                physical id: 23
                bus info: parisc@23
           *-generic:1 UNCLAIMED
                physical id: 24
                bus info: parisc@24
           *-generic:2 UNCLAIMED
                physical id: 27
                bus info: parisc@27
           *-generic:3 UNCLAIMED
                physical id: 29
                bus info: parisc@29
        *-generic:2 UNCLAIMED
             physical id: 3
             bus info: parisc@03
           *-generic:0 UNCLAIMED
                physical id: 1
                bus info: parisc@01
           *-generic:1 UNCLAIMED
                physical id: 2
                bus info: parisc@02
           *-generic:2 UNCLAIMED
                physical id: 3
                bus info: parisc@03
           *-generic:3 UNCLAIMED
                physical id: 6
                bus info: parisc@06
           *-generic:4 UNCLAIMED
                physical id: 7
                bus info: parisc@07
           *-generic:5 UNCLAIMED
                physical id: 10
                bus info: parisc@10
           *-generic:6 UNCLAIMED
                physical id: 11
                bus info: parisc@11
           *-generic:7 UNCLAIMED
                physical id: 14
                bus info: parisc@14
           *-generic:8 UNCLAIMED
                physical id: 15
                bus info: parisc@15
           *-generic:9 UNCLAIMED
                physical id: 17
                bus info: parisc@17
           *-generic:10 UNCLAIMED
                physical id: 18
                bus info: parisc@18
           *-generic:11 UNCLAIMED
                physical id: 20
                bus info: parisc@20
           *-generic:12 UNCLAIMED
                physical id: 22
                bus info: parisc@22
           *-generic:13 UNCLAIMED
                physical id: 23
                bus info: parisc@23
           *-generic:14 UNCLAIMED
                physical id: 24
                bus info: parisc@24
           *-generic:15 UNCLAIMED
                physical id: 25
                bus info: parisc@25
           *-generic:16 UNCLAIMED
                physical id: 28
                bus info: parisc@28
           *-generic:17 UNCLAIMED
                physical id: 29
                bus info: parisc@29
           *-generic:18 UNCLAIMED
                physical id: 30
                bus info: parisc@30
        *-generic:3 UNCLAIMED
             physical id: 4
             bus info: parisc@04
           *-generic:0 UNCLAIMED
                physical id: 1
                bus info: parisc@01
           *-generic:1 UNCLAIMED
                physical id: 2
                bus info: parisc@02
           *-generic:2 UNCLAIMED
                physical id: 3
                bus info: parisc@03
           *-generic:3 UNCLAIMED
                physical id: 4
                bus info: parisc@04
           *-generic:4 UNCLAIMED
                physical id: 5
                bus info: parisc@05
           *-generic:5 UNCLAIMED
                physical id: 6
                bus info: parisc@06
           *-generic:6 UNCLAIMED
                physical id: 7
                bus info: parisc@07
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller

                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi6
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRAM GSA-H10N
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /media/cdrom0
                   version: JL10
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /media/cdrom0
                      configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 12
                serial: 00:18:f3:5e:7b:c1
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth0
                version: 14
                serial: 00:18:f3:5e:4a:38
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=10.0.0.13 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD2500KS-00M
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WCANK5744644
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f5bbf5bb
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 2ac1a24d-a0ef-3d44-8631-6185b24b5ca5
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-10-04 20:42:27 filesystem=ntfs label=winOS modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 150GiB
                   capacity: 150GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: W95 FAT32 partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 100GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 49GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 66155d0b-7651-43da-9bae-05f321705fca
                   size: 1027MiB
                   capacity: 1027MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/feisty
                   version: 1.0
                   serial: 77c97a94-7445-4584-a6be-0e91a8c57063
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-04-21 19:41:51 filesystem=ext3 label=feisty modified=2008-07-06 18:26:25 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2008-07-06 18:26:25 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
     *-scsi
          physical id: 1
          bus info: firewire@0090a9101b0e48fb
          logical name: scsi8
          logical name: scsi9
        *-disk
             description: SCSI Disk
             product: My Book
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 1028
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5c74ae42
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/storage1
                version: 3.1
                serial: b0b71ff6-8759-0e40-a9be-06b46481b456
                size: 199GiB
                capacity: 199GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-05-01 20:31:51 filesystem=ntfs label=storage1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@8:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/storage2
                version: 3.1
                serial: 9a25a687-e951-bc4c-89df-0afabd435a04
                size: 199GiB
                capacity: 199GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-05-01 20:31:57 filesystem=ntfs label=storage2 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@8:0.0.0,3
                logical name: /dev/sdb3
                logical name: /media/storage3
                version: 1.0
                serial: dcaa0e1a-38d6-40d8-a3bb-260a8a31c364
                size: 65GiB
                capacity: 65GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-05-01 20:32:04 filesystem=ext3 label=storage3 modified=2008-07-06 18:26:25 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-06 18:26:25 state=mounted
        *-enclosure UNCLAIMED
             description: SCSI Enclosure
             product: My Book Device
             vendor: WD
             physical id: 0.1.0
             bus info: scsi@9:0.1.0
             configuration: ansiversion=4

```

---

### Post by starcannon on 2008-07-06
Very odd that its not showing up in Ubuntu or in Windows.
I'm reading this review about your board:
[http://www.pcstats.com/articleview.cfm?articleID=2078](http://www.pcstats.com/articleview.cfm?articleID=2078)

And they are saying this about your wifi, which only further makes this seem odd:
> Wireless networking has really taken off and it's great to see a USB2.0 based 802.11b/g wireless network adapter com standard with the board. Based on the Realtek RTL8186L controller, the wireless network card can also act as an access point.

So now I'm puzzled as to why it does not show up in lshw, or lsusb. 

I did a bit more googling and found out AzureWave made the wifi card thats on that motherboard, indeed its model number is: AW-GA800BT

# Built-in AzureWave AW-GA800BT WiFi 802.11b/g USB adapter (RTL8187L chipset)

I'm not sure what else to do with this, I have an AzureWave AW-GU210 that shipped native in my everex cloudbook, and that thing is notorious for being terrible, at least in my case its truely a usb device just buried inside, but I can replace it with any other usb stick style wifi that I wish.

I looked at screen shots of yours, particularly, [http://www.virtual-hideout.net/reviews/ASUS_P5B_Deluxe/P5B26.jpg](http://www.virtual-hideout.net/reviews/ASUS_P5B_Deluxe/P5B26.jpg) and [http://www.pcstats.com/articleimages/200702/asusp5bdeluxe_m3.jpg](http://www.pcstats.com/articleimages/200702/asusp5bdeluxe_m3.jpg) and I can't tell if its soldered down, but it looks like it probably is. If it isn't, then I'd probably get something a bit more standard than an AzureWave, even the RTL8187L chipset from what I found, looks to be difficult in linux WHEN it is good enough to show up. I'm not 100% convinced that card is a usb card, nothing is said that would indicate that at the ASUS website page for this board:
[http://usa.asus.com/products.aspx?modelmenu=2&model=1179&l1=3&l2=11&l3=307&l4=0](http://usa.asus.com/products.aspx?modelmenu=2&model=1179&l1=3&l2=11&l3=307&l4=0) 
and if it were a usb device that wasn't working, I'd feel better if it were showing up even as some sort of unknown device under lsusb.

There is another possibility I can think of, and that is that it has a soft switch that gets triggered by the windows registry and fires it off, I know the AzureWave usb device in my stupid everex cloudbook has such a soft switch and that it barely works in linux (even though that is its native os). In your case though you may have the ability in bios to turn the wifi to "always on" or something like that, I'd be poking around in there.

Anyway, sorry the post is so long, I don't know what else to do until the blasted thing starts showing up.

GL

P.S.
Oh did you run lshw with sudo? looked like a lot of blank style answers there.

---

### Post by starcannon on 2008-07-06
Just found this and thought I'd post it, it does look promising:
[http://www.phoronix.com/scan.php?page=article&item=621&num=4](http://www.phoronix.com/scan.php?page=article&item=621&num=4)

That is an older article, if its being proclaimed a good linux board on a kernel a few iterations back, then I would like to think that given enough time under the hood it would work great on one of these newer kernels.

I'll kinda dig around some more, but without having my hands on the hardware and doing some trial and error (i'd probably try a fresh clean install with a very methodical approach to driver installs) I doubt I'll be of much more use :(

---

### Post by starcannon on 2008-07-06
Okay, looks like there is definite cause for hope, but your gonna have to get your hands dirty.

[http://ubuntuforums.org/showpost.php?p=5251890&postcount=6](http://ubuntuforums.org/showpost.php?p=5251890&postcount=6)

It looks like this is being dealt with quite actively to, so who knows perhaps 8.10 will have it solved, if your trying to run 64bit ubuntu I'd recommend switching to 32bit, your only running 1gb of ram so you really won't know the difference anyway (other than it will just be easier to work with).

Heres a search link I haven't gone clear through as well, perhaps you can find out more that way:
[http://ubuntuforums.org/search.php?searchid=44179458](http://ubuntuforums.org/search.php?searchid=44179458)

GL and let us know how you get on.

---

### Post by diafanos on 2008-07-08
@starcannon
thanks for your interest!


I sent my motherboard back, to the store I bought it. 
They will probably unable to find a solution, so they are going to give me a brand new one!!!

---

### Post by diafanos on 2008-08-07
ok guys...I got my mobo fixed :-)

Now my wifi card is working. But I have a question for you;


As I had said, I send my broken mobo back to the store I bought it, for repair. 
There, they found out that mobo was problematic, so they decided to replace it with a new P5B. Because P5B does not exist in the market these days, they replaced it with an ASUS P5K, which is the successor of P5B.

My system works fine.  But do I have to change anything to ubuntu configuration (like adding new modules or deleting any...)?

thanx

---

