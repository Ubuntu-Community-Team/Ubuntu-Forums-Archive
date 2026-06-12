---
title: "WD HDD not recognized by Egdy, dma_timer_expiry: dma status == 0x21"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by nothingworks on 2006-10-31
**Hardware:**
Mobo: GA 7N400 Pro2
Drives: WD800JB on IDE1
        NEC DVDRW on IDE3  (IDE2 & IDE4 not used)
        WD1200JB on eIDE1 (IT8212 raid controller, raid set as IDE in the bios)
        WD1200JB on eIDE3 (IT8212 ...)   

Both WD1200JB drives shows errors when Edgy loads, However the second one works in spite of them
The second one (/dev/hdg) is where I have the root and swap partitions.


Kern.log:
> 
kernel: [17179575.880000] IT8212: IDE controller at PCI slot 0000:01:0c.0
kernel: [17179575.884000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
kernel: [17179575.884000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 177
kernel: [17179575.884000] IT8212: chipset revision 16
kernel: [17179575.884000] it821x: controller in smart mode.
kernel: [17179575.884000] IT8212: 100%% native mode on irq 177
kernel: [17179575.884000]     ide2: BM-DMA at 0x9c00-0x9c07, BIOS settings: hde: DMA, hdf: PIO
kernel: [17179575.884000]     ide3: BM-DMA at 0x9c08-0x9c0f, BIOS settings: hdg: DMA, hdh: PIO
[COLOR="Blue"]kernel: [17179575.884000] Probing IDE interface ide2...
kernel: [17179576.176000] hde: WDC WD1200JB-00CRA1, ATA DISK drive
kernel: [17179576.516000] hde: Performing identify fixups.
kernel: [17179576.516000] ide2 at 0x8c10-0x8c17,0x9002 on irq 177
kernel: [17179576.516000] hde: max request size: 128KiB
kernel: [17179576.516000] hde: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=65535/16/63, BUG
kernel: [17179576.516000]  hde:hde: recal_intr: status=0x51 { DriveReady SeekComplete Error }
kernel: [17179576.516000] hde: recal_intr: error=0x04 { DriveStatusError }
kernel: [17179576.516000] ide: failed opcode was: unknown[/COLOR]
[COLOR="Red"]kernel: [17179596.516000] hde: dma_timer_expiry: dma status == 0x21
kernel: [17179606.516000] hde: DMA timeout error
kernel: [17179606.516000] hde: dma timeout error: status=0xd0 { Busy }
kernel: [17179606.516000] ide: failed opcode was: unknown
kernel: [17179606.516000] hde: DMA disabled
kernel: [17179607.668000] ide2: reset: master: ECC circuitry error
kernel: [17179607.668000] hde: recal_intr: status=0x51 { DriveReady SeekComplete Error }
kernel: [17179607.668000] hde: recal_intr: error=0x04 { DriveStatusError }
kernel: [17179607.668000] ide: failed opcode was: unknown
kernel: [17179617.668000] hde: irq timeout: status=0xd0 { Busy }
kernel: [17179617.668000] ide: failed opcode was: unknown
kernel: [17179638.788000] ide2: reset: master: error (0x00?)
kernel: [17179638.788000] end_request: I/O error, dev hde, sector 0
kernel: [17179638.788000] Buffer I/O error on device hde, logical block 0
kernel: [17179638.788000] end_request: I/O error, dev hde, sector 0
kernel: [17179638.788000] Buffer I/O error on device hde, logical block 0
kernel: [17179638.788000]  **unable to read partition table**[/COLOR]
[COLOR="Blue"]kernel: [17179638.788000] Probing IDE interface ide3...
kernel: [17179639.076000] hdg: WDC WD1200JB-00CRA1, ATA DISK drive
kernel: [17179639.412000] hdg: Performing identify fixups.
kernel: [17179639.412000] ide3 at 0x9410-0x9417,0x9802 on irq 177
kernel: [17179639.412000] hdg: max request size: 128KiB
kernel: [17179639.412000] hdg: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=65535/16/63, BUG
kernel: [17179639.412000]  hdg:hdg: recal_intr: status=0x51 { DriveReady SeekComplete Error }
kernel: [17179639.416000] hdg: recal_intr: error=0x04 { DriveStatusError }
kernel: [17179639.416000] ide: failed opcode was: unknown
kernel: [17179640.568000]  hdg1 < hdg5 hdg6 > hdg2 hdg3[/COLOR]
kernel: [17179640.632000] end_request: I/O error, dev hde, sector 234441472
kernel: [17179640.632000] Buffer I/O error on device hde, logical block 29305184
kernel: [17179640.632000] end_request: I/O error, dev hde, sector 234441472
kernel: [17179640.632000] Buffer I/O error on device hde, logical block 29305184
                          ....Buffer errors continue, followed by I/O errors

**Partitions:** (hdg works, hde does not)
hdg1 < hdg5 hdg6 > hdg2 hdg3         

/dev/hde should look like this: (fdisk & fsck cannot open the device, gparted sees the drive as "UnAllocated")
hde1 < hde2 hde3 >    

Note: hdg1 and hde1 and extended partitions, hdg5,hdg6,hde2,hde3 are logical NTFS partitions)

There is no partition/file problem because Partition Magic 8 and Acronis Disk director see the partitions o.k.
I have run a full checkdisk of the partitions too

Any Ideas ? ](*,)

---

### Post by nothingworks on 2006-11-04
nobody ? ...bump

---

