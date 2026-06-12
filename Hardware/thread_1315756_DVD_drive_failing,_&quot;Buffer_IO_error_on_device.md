---
title: "DVD drive failing, &quot;Buffer I/O error on device sr0, logical block 0&quot;"
date: 2009-11-05
forum: Hardware
---

### Post by ilja on 2009-11-05
Xubuntu 9.10 Karmic 2.6.31-14-generic

Hardware:
Asus A7N8X-X motherboard
IDE1: 2x Seagate Barracuda 7200.10 320GB PATA (ST3320620A)
IDE2: Samsung DVDRW SH-S222A PATA

I can't seem to get my DVD drive to work reliably. I've searched the forums and googled around a bit, but couldn't find any solutions. I did find people with similar problems though.

Issue #1: I/O errors when reading, burning fails at verification. I have actually gotten a few successful burns and can play a DVD movie (with the I/O errors), but the problem persists. I just seem to get a different result every time.

**dmesg**
```

[ 1176.601603] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1176.601610] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1176.601615] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 1176.601621] end_request: I/O error, dev sr0, sector 0
[ 1176.601627] Buffer I/O error on device sr0, logical block 0
[ 1176.603731] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1176.603736] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1176.603740] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 1176.603745] end_request: I/O error, dev sr0, sector 0
[ 1176.603750] Buffer I/O error on device sr0, logical block 0
[ 1176.643589] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1176.643596] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1176.643601] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 1176.643608] end_request: I/O error, dev sr0, sector 0
[ 1176.643614] Buffer I/O error on device sr0, logical block 0
[ 1176.646081] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1176.646088] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1176.646093] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 1176.646099] end_request: I/O error, dev sr0, sector 0
[ 1176.646105] Buffer I/O error on device sr0, logical block 0

```

Issue #2: Drive "limited to UDMA/33 due to 40-wire cable". And yes I have an 80-wire cable. I've tried a couple of cables, swapped the drive around and even bought a new cable. Same difference.

**dmesg|grep ata**
```

[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  modified: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Embedded 14 pages at c203d000, static data 35612 bytes
[    0.000000] Memory: 2052624k/2097088k available (4565k kernel code, 43096k reserved, 2143k data, 540k init, 1187784k highmem)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.153139] libata version 3.00 loaded.
[    0.412896] cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
[    0.840805] pata_amd 0000:00:09.0: version 0.4.1
[    0.840864] pata_amd 0000:00:09.0: setting latency timer to 64
[    0.840963] scsi0 : pata_amd
[    0.841067] scsi1 : pata_amd
[    0.841859] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.841863] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.059057] ata1.00: ATA-7: ST3320620A, 3.AAE, max UDMA/100
[    1.059061] ata1.00: 625142448 sectors, multi 16: LBA48 
[    1.108865] ata1.01: ATA-7: ST3320620A, 3.AAC, max UDMA/100
[    1.108869] ata1.01: 625142448 sectors, multi 16: LBA48 
[    1.108893] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c6c500) ACPI=0x3f01f (20:20:0x1f)
[    1.108899] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c6c500) ACPI=0x3f01f (20:20:0x1f)
[    1.158915] ata1.00: configured for UDMA/100
[    1.200321] ata1.01: configured for UDMA/100
[    1.364331] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S222A, SB02, **max UDMA/66**
[    1.364357] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c6c500) ACPI=0x1f01f (30:600:0x13)
[    1.364361] ata2.00: **limited to UDMA/33 due to 40-wire cable**
[    1.380265] ata2.00: configured for UDMA/33
[    1.385401] Write protecting the kernel read-only data: 1836k
[    3.627417] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.460532] EXT4-fs (sdb1): mounted filesystem with ordered data mode

```

**hdparm -i /dev/scd0**
```

/dev/scd0:

 Model=TSSTcorp, FwRev=SB02, SerialNo=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```

---

### Post by ilja on 2009-11-06
Well, I'm trying out Windows 7 and I seem to be getting some I/O errors there as well. I think I'll just go and return the drive, maybe pick one from another manufacturer and see what happens. I've tried different cables, interfaces, combinations, OS's and a firmware upgrade so I guess that leaves hardware failure.

Windows does allow UDMA66 for the drive though, so that problems seems to be separate from the I/O errors.

---

