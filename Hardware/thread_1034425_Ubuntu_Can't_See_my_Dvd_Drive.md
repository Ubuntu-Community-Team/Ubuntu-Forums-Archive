---
title: "Ubuntu Can't See my Dvd Drive"
date: 2009-01-08
forum: Hardware
---

### Post by Sugi on 2009-01-08
I have never been able to get my dvd drive working within ubuntu.  But my bios sees the drive, but linux does not.

First, what's the command to show all my connected cd drives?

Sugi

---

### Post by Sugi on 2009-01-08
Memorex dvd burner.  BUMP

---

### Post by Sugi on 2009-01-08
Memorex dvd burner.  BUMP

---

### Post by Guille Damke on 2009-01-08
Hi,

I guess DVD drives should be recognized out of the box. Have you checked the hardware compatibility or incompatibility lists?

[HTML]http://ubuntuforums.org/showthread.php?t=361236[/HTML]

[HTML]http://ubuntuforums.org/showthread.php?t=361237[/HTML]

You can check your hardware doing:

```
sudo lshw
```

Good luck.

---

### Post by Sugi on 2009-01-09
```
  description: Mini Tower Computer
    product: P6320A-ABA 760N
    vendor: HP Pavilion 04
    version: 70000TG101DANUB
    serial: MX21214356 NA240
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=008F7551-7B38-D611-9B74-8AE127278698
  *-core
       description: Motherboard
       product: P4B266LA
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: 3.02 (11/22/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.1.2
          slot: PGA 478
          size: 1800MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:e0:18:5e:61:ab
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 9
                bus info: pci@0000:02:09.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy LS
                vendor: Creative Labs
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2 module=snd_ca0106
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ST340016A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.10
                serial: 3HS28KH5
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2ff87bf4
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: 07e7c12e-2270-4191-961c-3fe603afa122
                   size: 486MiB
                   capacity: 486MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b8906b2b-5c70-4b0c-9de0-cf28c6e1b52f
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-25 02:07:37 filesystem=ext3 modified=2009-01-09 08:50:02 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-01-09 08:50:02 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 8fa91302-1449-4b49-8d20-10c135eddf28
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-25 02:07:43 filesystem=ext3 modified=2009-01-09 08:50:47 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2009-01-09 08:50:47 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD1200BB-22C
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 16.0
                serial: WD-WMA8C1273010
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=204e2518
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /mnt/sdb
                   version: 1.0
                   serial: b1042781-901c-47b7-83c6-64c5ad4b4833
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-01 11:14:10 filesystem=ext3 label=/mnt/sdb modified=2009-01-09 08:50:47 mount.fstype=ext3 mount.options=rw,noatime,relatime,data=ordered mounted=2009-01-09 08:50:47 state=mounted
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

```

I will check out the list later on today.  Thank you for the information.

Sugi

---

### Post by forger on 2009-01-09
try this:
```
lspci -nn
```

Perhaps some ATA/SATA controllers aren't identified.
Did you connect the dvd yourself? Are you **100% SURE** you have connected your DVD correctly on the machine?

---

### Post by Sugi on 2009-01-09
Yep, I built this old computer ages ago.  I press the button on the dvd drive and it opens and closes, but it can't read anything.

```
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 05)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 05)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 05)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 05)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:09.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1)
02:0b.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]

```

Sugi

---

### Post by forger on 2009-01-11
Have you tried other operating systems?
Can you boot using the Live CD from that drive?

It's probably getting old and needs replacement.. dvd drives usually fail to respond after some time. :confused:

---

### Post by Sugi on 2009-01-11
I have tried it with an hard installation of fedora, opensuse, puppy, and dsl.  (dsl was on a disk)  Every single one of them got installed from that dvd drive.  So the drive does work....

Sugi

---

### Post by forger on 2009-01-12
> I have never been able to get my dvd drive working within ubuntu.
So what exactly does not work?

Maybe you should file a bug about it: [http://bugs.launchpad.net/ubuntu/+filebug](http://bugs.launchpad.net/ubuntu/+filebug)

In your bug report include the output of:
```

lspci -nn
sudo lshw -C disk

```

---

