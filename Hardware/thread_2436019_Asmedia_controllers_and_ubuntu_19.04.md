---
title: "Asmedia controllers and ubuntu 19.04"
date: 2020-01-30
forum: Hardware
---

### Post by Beanor on 2020-01-30
to start with, I have a 

MOBO: ga-ex58-ub5  

it has 2 onboard sata controllers: a intel based one that works fine, and an asmedia 106 model that many reports on other threads say dont work with cd/dvd drives.  fine: its 2020 and I don't use optical media on this.

to get around this, I purchased a godshark 6-port pcie sata card.  once installed and I was sure power issues were out of the way (external tester,) the **HDD's connected to the card cannot be seen in ubuntu.**  New controller seems to be using a asmedia 109X based sata controller, and this does show in disks as "ASMT109x- Config (2143_5)"

After scouring every single thread on ubuntu forums, and other linux forums....everyone just seems to have a fine time once they 1.  set the bios to ahci, or 2. disuse their optical drive with ubuntu.    The Mobo is on its latest firmware.  I am not using any RAID functions.  I'm stuck.

$lspci shows this: 

```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:09.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 12)
00:10.0 PIC: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:11.0 PIC: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 (rev 12)
00:11.1 PIC: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 (rev 12)
00:13.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 12)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:15.0 PIC: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers (rev 12)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 SATA controller: ASMedia Technology Inc. Device 0625 (rev 01)
03:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)
03:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Xeon 5600 Series QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 0 (rev 02)
3f:02.3 Host bridge: Intel Corporation Xeon 5600 Series Mirror Port Link 1 (rev 02)
3f:02.4 Host bridge: Intel Corporation Xeon 5600 Series QPI Link 1 (rev 02)
3f:02.5 Host bridge: Intel Corporation Xeon 5600 Series QPI Physical 1 (rev 02)
3f:03.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Registers (rev 02)
3f:03.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Target Address Decoder (rev 02)
3f:03.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller RAS Registers (rev 02)
3f:03.4 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Test Registers (rev 02)
3f:04.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Control (rev 02)
3f:04.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Address (rev 02)
3f:04.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Rank (rev 02)
3f:04.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 0 Thermal Control (rev 02)
3f:05.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Control (rev 02)
3f:05.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Address (rev 02)
3f:05.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Rank (rev 02)
3f:05.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 1 Thermal Control (rev 02)
3f:06.0 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Control (rev 02)
3f:06.1 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Address (rev 02)
3f:06.2 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Rank (rev 02)
3f:06.3 Host bridge: Intel Corporation Xeon 5600 Series Integrated Memory Controller Channel 2 Thermal Control (rev 02)
```

lshw -c storage -c disk  
```
 *-storage                 
       description: SATA controller
       product: ASMedia Technology Inc.
       vendor: ASMedia Technology Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
       configuration: driver=ahci latency=0
       resources: irq:27 memory:fbcfe000-fbcfffff memory:fbc00000-fbc7ffff
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
       resources: irq:24 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=32) memory:fbffc000-fbffc7ff
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: ST31000524AS
          vendor: Seagate
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: JC4A
          serial: 5VPAXZB7
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=823afdf8
  *-scsi:1
       physical id: 2
       logical name: scsi1
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: SAMSUNG HD103UJ
          physical id: 0.0.0
          bus info: scsi@1:0.0.0
          logical name: /dev/sdb
          version: 1113
          serial: S13PJ1CQ724829
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=aed13b88
  *-scsi:2
       physical id: 3
       logical name: scsi2
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: Hitachi HDS72101
          vendor: Hitachi
          physical id: 0.0.0
          bus info: scsi@2:0.0.0
          logical name: /dev/sdc
          version: A3MA
          serial: JP9921HD3AMEVH
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=f27ba823
  *-scsi:3
       physical id: 5
       logical name: scsi4
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: WDC WD10EZEX-00R
          vendor: Western Digital
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sdd
          version: 0A80
          serial: WD-WMC1S0936893
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=108ce140
  *-scsi:4
       physical id: 6
       logical name: scsi5
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: Hitachi HDT72101
          vendor: Hitachi
          physical id: 0.0.0
          bus info: scsi@5:0.0.0
          logical name: /dev/sde
          version: A31B
          serial: STF607MH3PS2EK
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=a2814c3f
  *-scsi:5
       physical id: 7
       logical name: scsi6
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: ASMT109x- Config
          physical id: 0.0.0
          bus info: scsi@6:0.0.0
          logical name: /dev/sdf
          version: n/a
          serial: 0123456789
          size: 100MiB (104MB)
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
  *-scsi:6
       physical id: 8
       logical name: scsi7
       capabilities: emulated
     *-disk
          description: ATA Disk
          product: ASMT109x- Config
          physical id: 0.0.0
          bus info: scsi@7:0.0.0
          logical name: /dev/sdg
          version: n/a
          serial: 0123456789
          size: 100MiB (104MB)
          configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512

```


any help or input GREATLY appreciated.

---

