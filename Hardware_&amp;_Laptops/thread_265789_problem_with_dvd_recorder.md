---
title: "problem with dvd recorder"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by KaSiNiStA on 2006-09-26
Hi, i am a new user from Italy, in the italian ubuntu community i can't find help so i try here... Excuse me for my bad english, i'll try to be as more clear as possible!

My ubuntu 6.06 doesn't read/write any type of DVD (video, data, etc). The device seems to be a normal CD recorder, in fact it can read and write every type of CD... I can't understand... My fstab is:

/dev/hdd        /media/cdrom1   iso9660 ro,user,users     0       0

but i think that the problem is not there.

If i digit, in my shell, cdrecord -checkdrive i obtain:

****************************

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schi lling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian. org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-25-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)sc sitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
cdrecord: Warning: controller returns wrong page 1F for CD capabilities page (2A ).
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : CMDQUE
Vendor_info    : 'TSSVcorr'
Identifikation : 'CF/FVFW"SJ-W162C'
Revision       : 'TS12'
Device seems to be: Generic CD-ROM.
cdrecord: Warning: controller returns wrong page 1F for CD capabilities page (2A ).
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this  target.
cdrecord: Warning: controller returns wrong page 1F for CD capabilities page (2A ).
Using generic SCSI-2       CD-ROM driver (scsi2_cd).
Driver flags   :
Supported modes:

**********************

The more interesting line is "cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this  target."

Please help me... If you need more information, you can ask to me! Thanks to all! :KS

---

### Post by apjone on 2006-09-26
do lshw for us please

---

### Post by KaSiNiStA on 2006-09-26
Here lshw ! Thanks!

*********************************

rebirth
    description: Computer
    product: VT82C692BX
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal
  *-core
       description: Motherboard
       product: 693-596-ITE8661
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 4.51 PG (04/10/00)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: SLOT 1
          size: 667MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-cache:0 UNCLAIMED
          description: L1 cache
          physical id: a
          slot: Internal Cache
          size: 32KB
          capacity: 32KB
          capabilities: synchronous internal write-back
     *-cache:1 UNCLAIMED
          description: L2 cache
          physical id: b
          slot: External Cache
          size: 256KB
          capacity: 2MB
          capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 192MB
        *-bank:0
             description: DIMM EDRAM
             physical id: 0
             slot: BANK_0
             size: 128MB
        *-bank:1
             description: DIMM EDRAM
             physical id: 1
             slot: BANK_1
             size: 64MB
        *-bank:2
             description: DIMM EDRAM [empty]
             physical id: 2
             slot: BANK_2
        *-bank:3
             description: DIMM EDRAM [empty]
             physical id: 3
             slot: BANK_3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: d0000000
          bus info: pci@00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-d3ffffff
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 15
                size: 32MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:d4000000-d4ffffff iomemory:d6000000-d7ffffff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d000-d00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: SAMSUNG SV2044D
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MM101-48
                   serial: 0191J1FN495206
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 18GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 823MB
                      capabilities: extended partitioned partitioned:extended
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6Y080L0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: YAR41BW0
                   serial: Y2AVKGFC
                   size: 76GB
                   capacity: 76GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 15GB
                      capabilities: primary bootable
                 *-volume:1
                      description: W95 Ext'd (LBA) partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      capacity: 61GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: SAMSUNG CD-ROM SC-148F
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: PS06
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: IDE Optical memory
                   product: TSSTcorpCD/DVDW SH-W162C
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: TS10
                   size: 4095MB
                   capabilities: packet atapi removable nonmagnetic dma lba iordy
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
                      size: 4095MB
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-25-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-network
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 00
             serial: 00:40:33:53:cd:f8
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.1.2 multicast=yes
             resources: ioport:d800-d81f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: Xwave QS3000A [FM801]
             vendor: Fortemedia, Inc
             physical id: f
             bus info: pci@00:0f.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=FM801
             resources: ioport:dc00-dc7f irq:5
        *-input
             description: Gameport controller
             product: Xwave QS3000A [FM801 game port]
             vendor: Fortemedia, Inc
             physical id: f.1
             bus info: pci@00:0f.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: extended bus_master cap_list
             configuration: driver=FM801_gameport
             resources: ioport:e000-e00f
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:07.3
          version: 30
          width: 32 bits
          clock: 33MHz


*****************************************

---

### Post by KaSiNiStA on 2006-09-26
Ehm, i add the results of the command "hdparm -i /dev/hdd"

 Model=TSSTcorpCD/DVDW SH-W162C, FwRev=TS10, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/512/512, TrkSize=512, SectSize=512, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

---

