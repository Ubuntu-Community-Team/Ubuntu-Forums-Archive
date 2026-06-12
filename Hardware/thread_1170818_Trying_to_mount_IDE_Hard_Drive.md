---
title: "Trying to mount IDE Hard Drive"
date: 2009-05-26
forum: Hardware
---

### Post by paulie_chan on 2009-05-26
Hi All,

I have a 300Gb IDE hard drive Im trying to mount under ubuntu.  My Machine uses SATA, so I've purchased a IDE to SATA adapter.

The BIOS detects the drive, and booting into XP, I can see the drive no problem.  I can't see it under Ubuntu however.

'fdisk -l' only shows my primary drive, ie:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be23b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         973     7815591   82  Linux swap / Solaris
/dev/sda2   *         974        3405    19535040    7  HPFS/NTFS
/dev/sda3            3406       60801   461033370   83  Linux
```Doing 'fdisk -l /dev/sdb' or 'fdisk -l /dev/sdc' returns nothing.

I think its a FAT32 partition, if that matters.

Anyone got any ideas?

Thanks in advance!

-Paul

---

### Post by paulie_chan on 2009-05-28
Hi again,

Still having problems...

dmesg gives me this:

```
[    0.000000] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 11
[    0.000000] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 11
[    0.000000] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 11
[    0.000000] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 11
[    0.000000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.000000] ata1.00: ATA-8: WDC WD5000AAKS-00C8A0, 12.01C02, max UDMA/133
[    0.000000] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (not used)
[    0.000000] ata1.00: configured for UDMA/133
[    0.000000] ata2: SATA link down (SStatus 1 SControl 300)
[    0.000000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0xa frozen
[    0.000000] ata2: irq_stat 0x00000040, connection status changed
[    0.000000] ata2: SError: { CommWake 10B8B DevExch }
[    0.000000] ata3: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata4: SATA link down (SStatus 0 SControl 300)
```And then repeatedly gives this error:

```
[    0.000000] ata2: soft resetting link
[    0.000000] ata2: SATA link down (SStatus 1 SControl 300)
[    0.000000] ata2: EH complete
[    0.000000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0xa frozen
[    0.000000] ata2: irq_stat 0x00000040, connection status changed
[    0.000000] ata2: SError: { CommWake 10B8B DevExch }
```Here is what lspci -vvvnn has to say about my SATA controller

```
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Unknown device [1043:81ef]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64
    Interrupt: pin A routed to IRQ 11
    Region 0: I/O ports at ff00 [size=8]
    Region 1: I/O ports at fe00 [size=4]
    Region 2: I/O ports at fd00 [size=8]
    Region 3: I/O ports at fc00 [size=4]
    Region 4: I/O ports at fb00 [size=16]
    Region 5: Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [70] #12 [0010]
```

Any ideas?

-Paul

---

