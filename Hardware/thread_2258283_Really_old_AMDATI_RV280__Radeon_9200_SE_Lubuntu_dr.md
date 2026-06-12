---
title: "Really old AMD/ATI RV280 / Radeon 9200 SE Lubuntu drivers"
date: 2014-12-26
forum: Hardware
---

### Post by tuomas4 on 2014-12-26
Greetings again! i just got this really old desktop running lubuntu surprisingly fast, i would like to watch flash based content like youtube on this.
i have tried all of the tidbits regarding similiar problems but since this card is so old im unsure now could this run youtube at all?
```
~$ dmesg | egrep 'drm|radeon'
[    1.571911] [drm] Initialized drm 1.1.0 20060810
[    1.852163] [drm] radeon kernel modesetting enabled.
[    1.852289] fb: switching to radeondrmfb from VESA VGA
[    1.853346] [drm] initializing kernel modesetting (RV280 0x1002:0x5964 0x1002:0x2002).
[    1.853367] [drm] register mmio base: 0xE5000000
[    1.853369] [drm] register mmio size: 65536
[    1.854096] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[    1.854104] radeon 0000:01:00.0: GTT: 64M 0xE0000000 - 0xE3FFFFFF
[    1.854109] [drm] Generation 2 PCI interface, using max accessible memory
[    1.854115] radeon 0000:01:00.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (128M used)
[    1.854134] [drm] Detected VRAM RAM=128M, BAR=128M
[    1.854136] [drm] RAM width 64bits DDR
[    1.854324] [drm] radeon: 128M of VRAM memory ready
[    1.854327] [drm] radeon: 64M of GTT memory ready.
[    1.855714] radeon 0000:01:00.0: WB disabled
[    1.855731] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000e0000000 and cpu addr 0xf8018000
[    1.855737] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.855739] [drm] Driver supports precise vblank timestamp query.
[    1.855794] [drm] radeon: irq initialized.
[    1.855822] [drm] Loading R200 Microcode
[    1.856855] [drm] radeon: ring at 0x00000000E0001000
[    1.856879] [drm] ring test succeeded in 1 usecs
[    1.857082] [drm] ib test succeeded in 0 usecs
[    1.858085] [drm] Radeon Display Connectors
[    1.858088] [drm] Connector 0:
[    1.858090] [drm]   VGA-1
[    1.858093] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    1.858095] [drm]   Encoders:
[    1.858097] [drm]     CRT1: INTERNAL_DAC1
[    1.858099] [drm] Connector 1:
[    1.858100] [drm]   SVIDEO-1
[    1.858102] [drm]   Encoders:
[    1.858103] [drm]     TV1: INTERNAL_DAC2
[    1.915442] [drm] fb mappable at 0xD0040000
[    1.915445] [drm] vram apper at 0xD0000000
[    1.915447] [drm] size 5242880
[    1.915448] [drm] fb depth is 24
[    1.915450] [drm]    pitch is 5120
[    1.915617] fbcon: radeondrmfb (fb0) is primary device
[    1.915779] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    1.915782] radeon 0000:01:00.0: registered panic notifier
[    1.915793] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0


```

that is what i found out about ubuntu.help regarding this card. i pasted that from my own terminal, if it helps or clarifies anything?
but i hope some of you could help me with getting this old desktop somewhat usable again! 
the computer has 1g of ram

thank you from your time and patience :smile:

---

### Post by mörgæs on 2014-12-26
Your computer is from a time when not all processors had SSE2 which Flash requires. To find out if it's the case please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by tuomas4 on 2014-12-26
```
computer
    description: Desktop Computer
    product: DW165A-ABX T469.FI
    vendor: HP Pavilion 061
    version: 0e+0211RE101KAME210
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Kamet2
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 2.01
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.06
          date: 12/19/2003
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2083MHz
          capacity: 3GHz
          width: 32 bits
          clock: 166MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:a000(size=4096) memory:e4000000-e5ffffff memory:d0000000-dfffffff
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:d0000000-d7ffffff ioport:a000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d8000000-dfffffff memory:e5010000-e501ffff
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:e6000000-e600ffff ioport:b000(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=32
             resources: irq:19 memory:e6010000-e60107ff ioport:b400(size=128)
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:20 ioport:b800(size=8) ioport:bc00(size=4) ioport:c000(size=8) ioport:c400(size=4) ioport:c800(size=16) ioport:cc00(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:e000(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:e6011000-e60110ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:e400(size=256)
        *-communication:1 UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:e800(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: 78
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:ec00(size=256) memory:e6012000-e60120ff
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160021A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.06
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=7d31a67d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 145GiB
                capacity: 145GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-26 00:11:38 filesystem=ext4 lastmountpoint=/ modified=2014-12-26 17:28:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-26 17:28:34 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 4094MiB
                capacity: 4094MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4094MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD Writer 300n
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 3.11
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@5:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512


```

---

### Post by mörgæs on 2014-12-26
Yes, as I expected an Athlon XP. 
Please see the link in my signature, especially second post in the thread.

---

### Post by tuomas4 on 2014-12-26
thank you, ill let you know if i get this working with your guide :)

---

### Post by mörgæs on 2014-12-26
Yes, please post your results.

---

### Post by tuomas4 on 2014-12-26
i found out that the device has 2 audio devices that the pulse audio displays as playing an really short mp3 loop but i cant hear anything, but the thing with the flash is that i tried earlyer today to install newer flash and now the package installer detects an conflict with the newer version? how can i uninstall the version that is causing this error it says ''flashplugin-installer'' is causing the error

edit: (thanks from the quick boot guide aswell)

edit2: got the youtube working now thank you from your guides!
         if you can help me with the audio issue i would greatly appreciate that too, but it might be that it is an hardware issue. thanks and happy holidays!

---

### Post by mörgæs on 2014-12-26
Have you tried installing the volume control as mentioned in the guide?

---

