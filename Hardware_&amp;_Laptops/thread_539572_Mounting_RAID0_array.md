---
title: "Mounting RAID0 array"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by markd on 2007-08-31
I've been searching the forums and googling for info on how to mount an existing raid0 array, and getting myself pretty confused.  Here's the setup:

Mobo: ABIT KT7A-RAID (Highpoint 370 Raid)
OS: Feisty 7.04

There are two disks in raid-0 config with data on that I want to mount.  I can't decide from all my searches even whether it's hardware/software/fakeraid.  I'd appreciate some pointers.  

Here's how the disks show up:

*-disk
       description: ATA Disk
       product: IBM-DTLA-307030
       vendor: IBM
       physical id: 0
       bus info: ide@2.0
       logical name: /dev/hde
       version: TX4OA50C
       serial: YKDYKV51722
       size: 28GB
       capacity: 28GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma4 smart=on
     *-volume
          description: Hidden W95 FAT32 partition
          physical id: 1
          bus info: ide@2.0,1
          logical name: /dev/hde1
          capacity: 4102MB
          capabilities: primary hidden
  *-disk
       description: ATA Disk
       product: IBM-DTLA-307030
       vendor: IBM
       physical id: 0
       bus info: ide@3.0
       logical name: /dev/hdg
       version: TX4OA50C
       serial: YKDYKV53101
       size: 28GB
       capacity: 28GB
       capabilities: ata dma lba iordy smart security pm apm
       configuration: apm=off mode=udma4 smart=on

and some dmesg stuff if it's relevant:

[    7.332000] HPT370: IDE controller at PCI slot 0000:00:13.0
[    7.332000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    7.332000] PCI: setting IRQ 11 as level-triggered
[    7.332000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    7.332000] HPT370: chipset revision 3
[    7.332000] HPT370: 100% native mode on irq 11
[    7.332000] HPT37X: no clock data saved by BIOS
[    7.460000] HPT37X: using 33MHz PCI clock
[    7.460000]     ide2: BM-DMA at 0xe800-0xe807, BIOS settings: hde:DMA, hdf:pio
[    7.460000]     ide3: BM-DMA at 0xe808-0xe80f, BIOS settings: hdg:DMA, hdh:pio

---

