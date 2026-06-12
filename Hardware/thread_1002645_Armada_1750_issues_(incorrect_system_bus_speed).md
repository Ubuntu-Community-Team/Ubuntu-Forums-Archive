---
title: "Armada 1750 issues (incorrect system bus speed?)"
date: 2008-12-05
forum: Hardware
---

### Post by wtangerine on 2008-12-05
Hi

I'm having issues trying to get an old Armada 1750 laptop back to life with linux. Previously, it was running WinXP quite well, so I thought on linux it would be even smoother, which would turn it into fully functional desktop, despite its age. Preferring to stick with Ubuntu, but taking resources in consideration, I installed Crunchbang Intrepid.
The hardware is: P-II processor, UDMA-capable 6GB hard disk, 3D Rage LT Pro AGP-133 video card (should have internal 4 MB memory), 192MB SDRAM (upgraded from original 64MB).
Amazingly, this lightweight Ubuntu-based distro runs terribly slow, much worse than Windoz. Launching a simple terminal emulator takes about 20-25 seconds. Everything seems slow: the hard-disk, the CDROM, the graphics.
Trying to investigate, I came up to an idea that the problem is incorrect system board handling.  This system board should run on 66Mhz, as stated here: [http://www.ciao.co.uk/Compaq_Armada_1750__17117]("http://www.ciao.co.uk/Compaq_Armada_1750__17117")

Here is my "sudo lshw" output:
```

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 191MiB
     *-cpu
          product: Mobile Pentium II
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.10
          size: 350MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage LT Pro AGP-133
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: dc
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: ATA Disk
                product: IBM-DBCA-206480
                vendor: IBM
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BC4O
                serial: HR0HRM08623
                size: 6194MiB (6495MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2cf52cf4
              *-volume:0
                   description: Windows FAT volume
                   vendor: IBM  53y
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT12
                   serial: 4153-4945
                   size: 15EiB
                   capabilities: primary bootable boot fat initialized
                   configuration: FATs=2 filesystem=fat label=DIAGS
              *-volume:1
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 5212MiB
                   capacity: 5212MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 287MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 4769MiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /boot
                      capacity: 154MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM XM-1902B
                vendor: TOSHIBA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1218
                capabilities: removable audio
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: <masked>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5523 driverversion=1.53+TP-LINK,07/27/2005,1.5.0.10 link=no multicast=yes wireless=IEEE 802.11g

```

If I read this right, it's showing that system bus runs only on 33 Mhz. Could someone please approve this? And is there a way to get things working as they should? Also, there are some strange messages in dmesg.

Thanks in advance.

---

### Post by snowpine on 2008-12-06
Hi Wtangerine, welcome to the Ubuntu Forums! Here's a free BUMP for you. :)

---

### Post by wtangerine on 2008-12-06
Hi there Snowpine ):P

It's nice to meet you again!

As you can see, I duplicated my post here. Hope it's not against the rules.

Just need to get some help... :confused:

---

