---
title: "All CD/DVD drives die: ata4.00: exception ... limiting speed to UDMA/25:PIO4"
date: 2008-09-12
forum: General Help
---

### Post by mrowth on 2008-09-12
Have working CD/DVD drives only for ten minutes or so each reboot. 
After that:
Discs won't be recognised, 
or released (both the eject button and command do nothing),
kaudocreator freezes (even with no disc inserted), 
audio won't be extracted (0% forever), 
getting an hdparm -I from the drive (not harddisks!) takes ages, 
and dmesg is full of repetitive misery chronicling a deterioration to UDMA/25 or PIO modes.

Using Kubuntu 8.04.1, had same problem with Ubuntu 8.04 and earlier versions (not sure about releases up to & including Feisty though... I think I first noticed the full extent of it with Ubuntu 8.04).

Have tried kernel parameters in GRUB in various combinations without much of a clue: 
irqpoll all-generic-ide combined_mode=combined/ide/libata atapi_enabled=1 -- put "options libata atapi_enabled=1" into /etc/modprobe.d/options -- just trying "solutions" I found online. Undid all those changes for now because they amounted to nothing. Can't say they made it worse because the whole thing's so unpredictable. For the longest time I thought the presence of one particular drive (perhaps only as master or only as slave) was affecting the operation of the others, etc.... now I think it's just generally hosed

Here's what dmesg adds when the problem occurs (with just a single drive for simplicity's sake):

```
[  730.664314] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  730.664326] ata4.00: cmd a0/01:00:00:10:00/00:00:00:00:00/a0 tag 0 dma 16 in
[  730.664327]          cdb 42 02 40 01 00 00 00 00  10 00 00 00 00 00 00 00
[  730.664329]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  730.664331] ata4.00: status: { DRDY }
[  734.248855] ata4: soft resetting link
[  734.740160] ata4.00: configured for UDMA/33
[  734.740174] ata4: EH complete
[  753.327861] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  753.327872] ata4.00: cmd a0/01:00:00:10:00/00:00:00:00:00/a0 tag 0 dma 16 in
[  753.327873]          cdb 42 02 40 01 00 00 00 00  10 00 00 00 00 00 00 00
[  753.327875]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  753.327877] ata4.00: status: { DRDY }
[  753.327895] ata4: soft resetting link
[  753.819138] ata4.00: configured for UDMA/33
[  753.819147] ata4: EH complete
[  781.419268] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  781.419279] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  781.419281]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
[  781.419282]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  781.419284] ata4.00: status: { DRDY }
[  781.419302] ata4: soft resetting link
[  781.912542] ata4.00: configured for UDMA/33
[  781.912566] ata4: EH complete
[  831.328190] ata4.00: limiting speed to UDMA/25:PIO4
[  831.328196] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  831.328204] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  831.328205]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
[  831.328206]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  831.328208] ata4.00: status: { DRDY }
[  831.328225] ata4: soft resetting link
[  831.819363] ata4.00: configured for UDMA/25
[  831.819385] ata4: EH complete
[  844.330005] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  844.330017] ata4.00: cmd a0/01:00:00:10:00/00:00:00:00:00/a0 tag 0 dma 16 in
[  844.330019]          cdb 42 02 40 01 00 00 00 00  10 00 00 00 00 00 00 00
[  844.330020]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  844.330022] ata4.00: status: { DRDY }
[  844.330041] ata4: soft resetting link
[  844.821395] ata4.00: configured for UDMA/25
[  844.821406] ata4: EH complete
[  879.346609] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  879.346620] ata4.00: cmd a0/01:00:00:10:00/00:00:00:00:00/a0 tag 0 dma 16 in
[  879.346622]          cdb 42 02 40 01 00 00 00 00  10 00 00 00 00 00 00 00
[  879.346623]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  879.346625] ata4.00: status: { DRDY }
[  879.346643] ata4: soft resetting link
[  879.838942] ata4.00: configured for UDMA/25
[  879.838957] ata4: EH complete
[  889.841245] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  889.841256] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  889.841258]          cdb 1e 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00
[  889.841259]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  889.841261] ata4.00: status: { DRDY }
[  889.841279] ata4: soft resetting link
[  890.333522] ata4.00: configured for UDMA/25
[  890.333535] ata4: EH complete
```

hdparm -I /dev/scd0:

```
/dev/scd0:

ATAPI CD-ROM, with removable media
        Model Number:       TOSHIBA DVD-ROM SD-M1912
        Serial Number:
        Firmware Revision:  TM00
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-3 -4 -5
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 *udma1 udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                PACKET command feature set
                DEVICE_RESET command
                NOP cmd
           *    DOWNLOAD_MICROCODE
                Removable Media Status Notification feature set
HW reset results:
        CBLID- below Vih
        Device num = 0
```

Or this:

```
/dev/scd0:

**ATA device, with non-removable media** (???)
        Model Number:       TOSHIBA DVD-ROM SD-M1912
        Serial Number:
        Firmware Revision:  TM00
Standards:
        Used: ATA-2 X3T10 948D revision 3
        Supported: 5 4 3 & some of 3
Configuration:
        Logical         max     current
        cylinders       24068   0
        heads           0       0
        sectors/track   0       0
        --
        LBA    user addressable sectors:          0
        device size with M = 1024*1024:           0 MBytes
        device size with M = 1000*1000:           0 MBytes
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Vendor
        R/W multiple sector transfer: Max = 0   Current = ?
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                PACKET command feature set
                DEVICE_RESET command
                NOP cmd
           *    DOWNLOAD_MICROCODE
                Removable Media Status Notification feature set
HW reset results:
        CBLID- below Vih
        Device num = 0
```

In this latter case there's also this in dmesg output:

```
[ 2466.518920] ata4: soft resetting link
[ 2467.214790] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x1)
[ 2467.214797] ata4.00: revalidation failed (errno=-5)
[ 2467.214801] ata4: failed to recover some devices, retrying in 5 secs

```


PS: 
Have tried three different drives, old and new, alone or in varying combinations: DVD ROM, DVD Writer, DVD Dual Layer Writer. All drives are parallel ATA. My harddisks, too (they work). Would it help if I got a SATA drive? Unfortunately, it seems my mainboard can't boot from them. (Whatever else is a "SATA Boot ROM: Enabled" option for, though? I wouldn't know)

---

### Post by mrowth on 2008-09-12
Noticed now: A "frozen" CD/DVD drive can start back up while the harddisk is working (e.g. I'm loading a program) - after that it stops again! Usually, though, it stays dead until I reboot. Then it works again for a while, typically until I change the disc...

---

### Post by mrowth on 2008-09-12
I'm sure this isn't going to help either but yesterday, a newish DVD writer (bought May 08) stopped working altogether - not even a grace period anymore. It'll read directories (with staccato grinding noise) but no files or audio tracks

```
[  618.010180] Buffer I/O error on device sr0, logical block 35
[  618.033222] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.033227] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.033231] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.033234] end_request: I/O error, dev sr0, sector 140
[  618.056267] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.056272] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.056276] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.056279] end_request: I/O error, dev sr0, sector 140
[  618.079322] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.079327] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.079330] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.079333] end_request: I/O error, dev sr0, sector 140
[  618.102402] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.102407] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.102411] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.102415] end_request: I/O error, dev sr0, sector 140
[  618.125472] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.125477] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.125480] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.125485] end_request: I/O error, dev sr0, sector 140
[  618.148540] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.148544] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.148548] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.148551] end_request: I/O error, dev sr0, sector 140
[  618.171583] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  618.171587] sr 6:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  618.171591] sr 6:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  618.171594] end_request: I/O error, dev sr0, sector 140
```

```
/dev/scd0:

ATAPI CD-ROM, with removable media
        Model Number:       SONY    DVD RW DRU-190A
        Serial Number:
        Firmware Revision:  1.63
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    PACKET command feature set
           *    DEVICE_RESET command
           *    Mandatory FLUSH_CACHE
HW reset results:
        CBLID- above Vih
        Device num = 0

```

---

### Post by mrowth on 2008-09-14
Bump?

---

### Post by mc4man on 2008-09-14
What does this show after booting up
> grep 'DMA' /var/log/kern.log

Do you know if your ide cable is a 40 wire or an 80 wire?
(80 wire is very smooth, like the cable for most hdd's, on a 40 the wires are obvious.

---

### Post by mrowth on 2008-09-14
> **mc4man said:**
> What does this show after booting up

Depends on the drives I'm trying. Here're two examples.

1) 7 year old AOpen DVD-ROM drive that shows up in the BIOS and plays audio CDs through the headphone jack but is altogether unreachable from an Ubuntu end-userly side of things:

Sep 14 22:48:20 earthworm kernel: [    0.000000]   DMA             0 ->     4096
Sep 14 22:48:20 earthworm kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 14 22:48:20 earthworm kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 14 22:48:20 earthworm kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 14 22:48:20 earthworm kernel: [   37.359202] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Sep 14 22:48:20 earthworm kernel: [   37.359204] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Sep 14 22:48:20 earthworm kernel: [   37.540799] ata1.00: ATA-7: ExcelStor Technology J880, PF2OA21B, max UDMA/133
Sep 14 22:48:20 earthworm kernel: [   37.540971] ata1.01: ATA-7: SAMSUNG HD400LD, WQ100-15, max UDMA/100
Sep 14 22:48:20 earthworm kernel: [   37.564604] ata1.00: configured for UDMA/133
Sep 14 22:48:20 earthworm kernel: [   37.580571] ata1.01: configured for UDMA/100
Sep 14 22:48:20 earthworm kernel: [   37.898240] ata3: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 18
Sep 14 22:48:20 earthworm kernel: [   37.898242] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 18

(UDMA/100 is the highest the Samsung HD goes, that's not an error.)

2) LG DVD writer that tends to work for a while, at least as a CD-ROM drive; DVDs work occasionally. I may then be able to watch an entire movie, but every time I change the disc there's a chance it won't be recognised or I won't get it back out. Once the problems start, they last until the next reboot. Writing speed is down to 0.00x - 0.02x.

Sep 14 23:20:38 earthworm kernel: [    0.000000]   DMA             0 ->     4096
Sep 14 23:20:38 earthworm kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 14 23:20:38 earthworm kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 14 23:20:38 earthworm kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 14 23:20:38 earthworm kernel: [   38.066003] ata1: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 18
Sep 14 23:20:38 earthworm kernel: [   38.066005] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 18
Sep 14 23:20:38 earthworm kernel: [   38.499160] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Sep 14 23:20:38 earthworm kernel: [   38.499169] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Sep 14 23:20:38 earthworm kernel: [   38.676802] ata3.00: ATA-7: ExcelStor Technology J880, PF2OA21B, max UDMA/133
Sep 14 23:20:38 earthworm kernel: [   38.676971] ata3.01: ATA-7: SAMSUNG HD400LD, WQ100-15, max UDMA/100
Sep 14 23:20:38 earthworm kernel: [   38.699646] ata3.00: configured for UDMA/133
Sep 14 23:20:38 earthworm kernel: [   38.715617] ata3.01: configured for UDMA/100
Sep 14 23:20:38 earthworm kernel: [   39.035322] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-4040B, A300, max UDMA/33
Sep 14 23:20:38 earthworm kernel: [   39.207134] ata4.00: configured for UDMA/33

(UDMA/33 is okay, too.)

3) Same LG drive again; this time no discs work (it seems rather random)... 

Sep 14 23:42:30 earthworm kernel: [    0.000000]   DMA             0 ->     4096
Sep 14 23:42:30 earthworm kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 14 23:42:30 earthworm kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 14 23:42:30 earthworm kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 14 23:42:30 earthworm kernel: [   47.187712] ata1: SATA max UDMA/133 mmio m4096@0xf9900000 port                              0xf9900200 irq 17
Sep 14 23:42:30 earthworm kernel: [   47.187715] ata2: SATA max UDMA/133 mmio m4096@0xf9900000 port                              0xf9900280 irq 17
Sep 14 23:42:30 earthworm kernel: [   47.187717] ata3: PATA max UDMA/133 mmio m4096@0xf9900000 port                              0xf9900300 irq 17
Sep 14 23:42:30 earthworm kernel: [   48.021702] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma                              0xb800 irq 19
Sep 14 23:42:30 earthworm kernel: [   48.021704] ata5: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma                              0xb808 irq 19
Sep 14 23:42:30 earthworm kernel: [   49.026492] ata6: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0                             xfc00 irq 14
Sep 14 23:42:30 earthworm kernel: [   49.026494] ata7: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0                             xfc08 irq 15
Sep 14 23:42:30 earthworm kernel: [   49.204131] ata6.00: ATA-7: ExcelStor Technology J880, PF2OA21B                             , max UDMA/133
Sep 14 23:42:30 earthworm kernel: [   49.204298] ata6.01: ATA-7: SAMSUNG HD400LD, WQ100-15, max UDMA                             /100
Sep 14 23:42:30 earthworm kernel: [   49.226983] ata6.00: configured for UDMA/133
Sep 14 23:42:30 earthworm kernel: [   49.242950] ata6.01: configured for UDMA/100
Sep 14 23:42:30 earthworm kernel: [   49.562420] ata7.00: ATAPI: HL-DT-ST DVDRAM GSA-4040B, A300, ma                             x UDMA/33
Sep 14 23:42:30 earthworm kernel: [   49.734234] ata7.00: configured for UDMA/33

(The extra ata1-3 here are an unused controller I pointlessly activated in the BIOS, ignore them...)

> Do you know if your ide cable is a 40 wire or an 80 wire?
(80 wire is very smooth, like the cable for most hdd's, on a 40 the wires are obvious.

40. It's labeled "CD-ROM cable" and came with the mainboard. I tried another in between, though (didn't help, obviously)

---

### Post by mc4man on 2008-09-14
If you can get your hands on an 80 for the dvd drives I'd try that.

While soft resets to pio4 aren't as bad as pio1 it would definitely cause problems.

side note : all this switching drives *probably* has made for an interesting 70...cd rules

run this in a maximized terminal

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by mrowth on 2008-09-14
> **mc4man said:**
> If you can get your hands on an 80 for the dvd drives I'd try that.

I may have one somewhere but I doubt it... it's always worked with 40 wire cable...

> While soft resets to pio4 aren't as bad as pio1 it would definitely cause problems.

Would it stop drives from working at all? It's not like they're merely slowing down...

> side note : all this switching drives *probably* has made for an interesting 70...cd rules

run this in a maximized terminal

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRAM_GSA-4040B (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVDRAM_GSA-4040B (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DVD_RW_DRU-190A (pci-0000:00:0f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"

Interesting enough? I've never seen that file before...

---

### Post by mc4man on 2008-09-14
actually it's not that bad, one drive is duplicated, do you know which one is the a-open? (DVD_RW_DRU-190A)

I'd try the 80 wire if you can, pick a drive to use and delete all the entries in 70....rules (gets rewritten when you boot. 70..rules controls all the /dev/links for your cd/dvd drives - whish sometimes can be an problem
for instance a player might default to /dev/dvd or /dev/cdrom but your drive might have /dev/dvd2 or /dev/cdrom2 as it's links 

If you want to see now delete the entries and re boot
Leave it like this
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


```
When ever you switch drives you should reset 70....rules

```
 gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by mrowth on 2008-09-14
> **mc4man said:**
> actually it's not that bad, one drive is duplicated, do you know which one is the a-open? (DVD_RW_DRU-190A)
The DVD_RW_DRU-190A is the Sony drive from post #3. I took it back to the store last week. Ubuntu doesn't seem to have acknowledged the AOpen drive's existence. 

Another (Toshiba) DVD-ROM drive isn't mentioned either, although unlike the AOpen it at least works (for the usual 10-20 minutes)


> I'd try the 80 wire if you can, pick a drive to use and delete all the entries in 70....rules (gets rewritten when you boot. 70..rules controls all the /dev/links for your cd/dvd drives - whish sometimes can be an problem
for instance a player might default to /dev/dvd or /dev/cdrom but your drive might have /dev/dvd2 or /dev/cdrom2 as it's links 
Seems /dev/scd0 and /dev/scd1 always (invariably) correspond to the "master" & "slave" optical drives... really not much of a problem there.

I'll try to find such a cable. 

> If you want to see now delete the entries and re boot
Leave it like this
```

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


```
When ever you switch drives you should reset 70....rules

```
 gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
Ok, done. Though I use vim. :guitar:

---

### Post by mc4man on 2008-09-14
> Seems /dev/scd0 and /dev/scd1 always (invariably) correspond to the "master" & "slave" optical drives
That's 'set in stone' so to speak, master gets scd0, slave scd1. As mentioned the links can cause minor issues, like when a player is looking to /dev/cdrom for an audio cd and the drive is something else 

They're cheap to buy, another possibility is when you buy an internal hdd one is usually in the box and invariably unused.

---

### Post by slowth5 on 2008-09-14
Same resetting problem with my Lite-On drive.  Found this thread and it solved my issue.


> **ArcherB said:**
> I had the same problem and was beating my head against the desk trying to figure it out.  Finally, I found a post that suggested adding noapic to the end of the kernel line in your /boot/grub/menu.lst file.  The post suggested a few other items that didn't work (made my mouse disappear), but just the noapic seemed to fix the problem for me.

However, before changing your menu.lst file, try typing it in at boot just to make sure it works out OK before making the change permenent.

---

### Post by mrowth on 2008-09-14
edit: running more tests first.

---

### Post by mrowth on 2008-09-15
> **slowth5 said:**
> Same resetting problem with my Lite-On drive.  Found this thread and it solved my issue.
Thanks. It does make a bit of a difference in that those "drive features" available after boot seem to *remain* available. 

Toshiba DVD-ROM (SD-M1912): Works with DVDs and CDs -- reliably so far.

LG DVD writer (GSA-4040B): If it works, it works with CDs only. Doesn't "recognize" DVDs anymore, doesn't always eject them again either. A couple days ago I could still burn a DVD with it. If it doesn't work, I'm getting stuff about soft resets, failures to identify, and finally "ata 4.01: disabled".

AOpen DVD-ROM: Doesn't work at all.

Sony DVD writer (DRU-190A): Back at Sony, unfortunately. Wasn't working at all anymore. Two weeks ago or so I used it to burn the Hardy Heron CD. Although I had to use the LG DVD writer to successfully *install* it (without stopping at 50%). 

So at least the brokenness seems more consistent now. Still I'm left with several drives that mysteriously stopped working.

---

### Post by mrowth on 2008-09-15
Not sure it's the "noapic", but the computer's spontaneously locked up hard three times since then. It's not usually done that before.

---

### Post by mrowth on 2008-09-15
Yet if I remove the noapic again, X won't start anymore (not with the Nvidia drivers, anyway. They've been working without noapic for 5+ years.)

(EE) NVIDIA(0): The interrupt for NVIDIA graphics device PCI:1:0:0 appears to
(EE) NVIDIA(0):     be edge-triggered.  Please see Chapter 8: Common Problems
(EE) NVIDIA(0):     in the README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!

---

### Post by slowth5 on 2008-09-15
Your issue sounds much more complicated than mine, so I'm sorry if my information resulted in more problems.  My drive worked perfectly with Gutsy, but exhibited identical symptoms to yours when I upgraded to Hardy.  I also noticed that the same problem was present with Fedora 9, so I linked the issues to the kernel.  

Adding noapic has cured my issues, but I just do not know enough about hardware to suggest any more solutions to your problems. I hope you sort it out, since not having a cd/dvd drive is torture.

---

### Post by mrowth on 2008-09-15
> **slowth5 said:**
> Your issue sounds much more complicated than mine, so I'm sorry if my information resulted in more problems.  My drive worked perfectly with Gutsy, but exhibited identical symptoms to yours when I upgraded to Hardy.  I also noticed that the same problem was present with Fedora 9, so I linked the issues to the kernel.  

Adding noapic has cured my issues, but I just do not know enough about hardware to suggest any more solutions to your problems. 

With noapic they at least no longer seem to "just die" as per my opening posts. That nvidia now *depends* on noapic is puzzling, though. And those lockups... bleh. 

> I hope you sort it out, since not having a cd/dvd drive is torture.

Thanks. It is indeed frustrating. Having no graphics is also frustrating. Computer locking up, too. Pick two.

---

### Post by mrowth on 2008-09-17
Also, suspend to RAM now kills the X session  (unless it's relatively soon after originally booting up -- not 3 hours later). It suspends normally, but when I wake the computer up again, the nivida logo reappears and then the kdm login screen. When I leave it suspended for a while (a few hours, say), the comp will simply reset on waking. Alternatively, it'll only lock the session and not suspend at all.  Great choice of bugs I have to pick from via boot-time kernel parameters.

---

### Post by mrowth on 2008-10-02
So I got a new DVD writer. 

I picked an S-ATA drive this time. Samsung "Super Writemaster"... or TSSTcorp CDDVDW SH-S223F, as far as the computer's concerned. I've never had an S-ATA drive before. I'm pretty sure my Asus A8V Deluxe mobo doesn't support current S-ATA speeds. I expected there to be a jumper or something to downgrade the drive, but there isn't.

Reading is ok. I can watch movies and read data CDs and DVDs. 

Writing, though - it finishes "successfully" in K3B (but verification fails); sometimes device buffer drops to nearly 0% in between. 

I've also tried Nero Express 7 Essentials for Windows (came with the drive). Same result, though it mercifully aborts half-way through with a write error, sparing me the extra wait. 

I've got a log from Nero that I'll attach. I can't really parse it, but I did notice DMA is off now. Writing speed used to be 16x, now it's always 4x.

Can my computer, or can Ubuntu, actually destroy drives? Or is there a reason why neither PATA nor SATA DVD writers work anymore? Why did they work at first?

Should I get a PATA drive again so I can ruin it in the same manner? :/

Nero log from burning ~4GB data DVD:

```
katzenmüh
babelcat
4C87-200M-4005-E10K-000X-X640-0800-3700-0000-4072-6K9A-**** (*)

Windows XP 5.1
IA32
WinAspi: -

NT-SPTI used
Nero Version: 7.11.6.0
Internal Version: 7, 11, 6, 0
 (Nero Express)
Recorder:             <TSSTcorp CDDVDW SH-S223F>Version: SB00 - HA 1 TA 3 - 7.11.6.0
 Adapter driver:      <IDE>                     HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default
CD-ROM:               <TOSHIBA  DVD-ROM SD-M1912>Version: TM00 - HA 1 TA 1 - 7.11.6.0
 Adapter driver:      <IDE>                     HA 1

=== Scsi-Device-Map ===
DiskPeripheral       : ExcelStor Technology J880        atapi Port 0 ID 0  DMA: On 
DiskPeripheral       : SAMSUNG HD400LD                  atapi Port 0 ID 1  DMA: On 
CdRomPeripheral      : TOSHIBA DVD-ROM SD-M1912         atapi Port 1 ID 0  DMA: On 
CdRomPeripheral      : TSSTcorpCDDVDW SH-S223F SB00  viasraid Port 2 ID 0  DMA: Off

=== CDRom-Device-Map ===
TOSHIBA DVD-ROM SD-M1912   H:   CdRom1
TSSTcorp CDDVDW SH-S223F   G:   CdRom3
=======================

AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 2047MB (2097151kB)
Free physical memory: 2047MB (2097151kB)
Memory in use       : 27 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

3.10.2008
UDF Zusammenstellung
04:11:44	#1 Text 0 File SCSIPTICommands.cpp, Line 450
	LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	
04:11:44	#2 Text 0 File Isodoc.cpp, Line 6671
	UDF document burn settings
	------------------------------------------
	Determine maximum speed : FALSE
	Simulate                : FALSE
	Write                   : TRUE
	Finalize CD             : TRUE
	Multisession            : FALSE
	Burning mode            : DAO
	Mode                    : 1
	UDF Mode                : pure
	UDF Options             : automatic
	UDF Revision            : 1.02
	UDF Partition Type      : physical
	
04:11:51	#3 Text 0 File Burncd.cpp, Line 3500
	Turn on Disc-At-Once, using DVD media
	
04:11:51	#4 Text 0 File FilesystemSettingsValidator.cpp, Line 142
	FS Settings: using validator 'CUDFSettingsValidatorDVD'
	ParamMode = 'automatic', changing UDF partition type from 'physical' to 'physical'
	Changing UDF revision from '1.02' to '1.02'
	
04:11:55	#5 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2298495 (510:46.45, 4489MB)
	Last address to be written:            2125711 (472:22.61, 4151MB)
	
04:11:55	#6 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO (enabled: CD)
	
04:11:55	#7 Text 0 File DlgWaitCD.cpp, Line 2988
	Recorder: TSSTcorp CDDVDW SH-S223F, Media type: DVD-R
	 Disc Manufacturer ID: <DAXON0> <16S>
	 Disc Application Code: 64, Disc Physical Code: 193
	
04:11:55	#8 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
04:11:55	#9 Text 0 File ThreadedTransferInterface.cpp, Line 785
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 ()
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 2125712 (2125712) = #2125712/472:22.62
	    relocatable, disc pos for caching/writing not required/ required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 2125712 blocks [G: TSSTcorp CDDVDW SH-S223F]
	--------------------------------------------------------------
	
04:11:55	#10 Text 0 File ThreadedTransferInterface.cpp, Line 986
	Prepare [G: TSSTcorp CDDVDW SH-S223F] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    4353458176, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  2125712 |        0 | 0x00
	  2125712 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
04:11:55	#11 Text 0 File SCSIPTICommands.cpp, Line 240
	SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
	
04:11:55	#12 Text 0 File Burncd.cpp, Line 4286
	Caching options: cache CDRom or Network-Yes, small files-Yes (<64KB)
	
04:11:55	#13 Phase 24 File dlgbrnst.cpp, Line 1767
	Caching of files started
	
04:12:08	#14 Text 0 File Burncd.cpp, Line 4405
	Cache writing successful.
	
04:12:08	#15 Phase 25 File dlgbrnst.cpp, Line 1767
	Caching of files completed
	
04:12:08	#16 Phase 36 File dlgbrnst.cpp, Line 1767
	Burn process started at 4x (5.540 KB/s)
	
04:12:08	#17 Text 0 File ThreadedTransferInterface.cpp, Line 2733
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
04:12:08	#18 Text 0 File DVDR.cpp, Line 3262
	Recording mode: Sequential Recording Mode
	
04:12:08	#19 Text 0 File DVDR.cpp, Line 3416
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
04:12:08	#20 Text 0 File Cdrdrv.cpp, Line 10161
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 2.1 (33)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 Outer Limit of Data Recordable Area:          0 h
	 Data in Burst Cutting Area (BCA) does not exist
	  Revision number of maximum recording speed: 6.0
	  Revision number of minimum recording speed: -
	  Revision number table of recording speed: 1.0 2.0 3.0 4.0 5.0 - - 
	  Class: 0,  Extended part version: 33
	  Start PSN of the Extra Border Zone: 0 h
	  Start PSN of Physical format information blocks in Extra Border Zone: 0 h
	 Media Specific [16..783]:
	    00 60 00 10 20 30 40 50 - 00 00 00 21 00 00 00 00    .`...0@P...!....
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    1D 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    01 40 C1 FD 9E D8 52 00 - 02 84 0E 10 87 88 80 00    .@....R.........
	    03 44 41 58 4F 4E 30 00 - 04 31 36 53 00 00 00 00    .DAXON0..16S....
	    05 88 80 00 00 00 01 00 - 06 09 0B 12 A8 88 90 00    ................
	    07 88 80 00 00 00 00 00 - 08 06 13 0A 0E 08 04 00    ................
	    09 96 06 0C 0B 70 88 00 - 0A 80 00 00 00 00 10 00    .....p..........
	    0B 08 18 17 B8 88 85 00 - 0C B6 79 0B B0 33 03 00    ..........y..3..
	    0D 30 00 D0 00 00 00 00 - 0E 0A 20 3B 37 29 1E 00    .0.........;7)..
	    0F 50 1D 2B 15 AA B5 00 - 10 88 80 00 00 00 00 00    .P.+............
	    11 00 00 00 00 00 00 00 - 12 0A 2D 39 35 2B 1D 00    ..........-95+..
	    13 50 1F 2D 19 98 B5 00 - 14 88 80 00 00 00 00 00    .P.-............
	    15 00 00 00 00 00 00 00 - 16 09 3A 45 40 2E 27 00    ..........:E@.'.
	    17 80 21 2E 1F 78 B5 00 - 18 88 8C 00 0C 00 0C 00    ..!..x..........
	    19 00 00 00 00 00 00 00 - 1A 09 4F 47 46 38 26 00    ..........OGF8&.
	    1B 70 21 2D 1B 67 C5 00 - 1C 88 84 00 04 00 04 00    .p!-.g..........
	    1D 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
04:12:08	#21 Text 0 File ThreadedTransfer.cpp, Line 268
	Pipe memory size 83836800
	
04:12:08	#22 Text 0 File CUDFTransferItem2.cpp, Line 637
	 
	GenUDF2 FS Layout:
	=-=-=-=-=-=-=-=-=-=-
	    Sectors to be written: 2125712
	            Session Start: Sector 0
	         Volume Structure: Sector [0, 256] (257 Sectors)
	         Before Meta Data: Sector [257, 272] (16 Sectors)
	                Meta Data: Sector [273, 30737] (30465 Sectors)
	                     Data: Sector [30738, 2125410] (2094673 Sectors)
	               After Data: Sector [2125411, 2125423] (13 Sectors)
	            Trailer Track: Sector [2125424, 2125711] (288 Sectors)
	 
	GenUDF2 Parameters:
	=-=-=-=-=-=-=-=-=-=-
	                 PrepTime: 10-03-2008 04:11:52
	             UDF Revision: 1.02
	       UDF Partition Type: Physical
	         UDF Special Mode: None
	         Bytes per Sector: 2048
	            Session Start: 0
	 Physical Partition Start: -1
	           Total Capacity: 2298496
	       Multi Session Mode: None
	                Disc Type: DVD-R
	                 OS Class: 0
	                Volume ID: stash
	     Allow Unicode Labels: 0
	      Duplicate Meta Data: 1
	             MS Info File: 00000000
	        VMS Rollback File: 00000000
	        Create ISO bridge: 0
	         ECC Block Length: 16
	    Sparing Packet Length: 32
	     Allocation Unit Size: 32
	      Alignment Unit Size: 16
	            Make Writable: 0
	              Access Type: Read-only
	
04:12:23	#23 Text 0 File Cdrdrv.cpp, Line 1405
	04:12:23.158 - G: TSSTcorp CDDVDW SH-S223F : Queue again later
	
04:25:48	#24 SPTI -1135 File SCSIPassThrough.cpp, Line 181
	CdRom3: SCSIStatus(x02) WinError(0) NeroError(-1135)
	Sense Key:  0x03 (KEY_MEDIUM_ERROR)
	Sense Code: 0x0C
	Sense Qual: 0x00
	CDB Data:   0x2A 00 00 13 E4 A0 00 00 20 00 00 00 
	Sense Area: 0x71 00 03 00 00 00 00 0A 00 00 00 00 0C 
	Buffer x1d6f1900: Len x10000
	0xD7 E0 9A AB 2F 0B 7E 79 CD E5 B6 EF 32 AB 77 59 
	0x70 C5 CF 7E 60 75 7E 1A FC C2 D6 AF BD E6 27 D6 
	0xDE 8F 25 A4 86 04 1B 32 6E D7 FF EA A7 C2 E0 9C 
	
04:25:48	#25 CDR -1135 File Writer.cpp, Line 306
	Write error
	G: TSSTcorp CDDVDW SH-S223F
	
04:25:48	#26 Text 0 File DVDR.cpp, Line 3818
	EndDAO: Last written address was 1303711 (13E49Fh)
	
04:25:48	#27 Phase 38 File dlgbrnst.cpp, Line 1767
	Burn process failed at 4x (5.540 KB/s)
	
04:25:48	#28 Text 0 File SCSIPTICommands.cpp, Line 287
	SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
	
04:25:53	#29 Text 0 File Cdrdrv.cpp, Line 11412
	DriveLocker: UnLockVolume completed
	
04:25:53	#30 Text 0 File SCSIPTICommands.cpp, Line 450
	UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
	

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 0 (Security Option) 
```

dmesg. Trying to read burnt DVD. Not likely to be of interest. 

```
[  121.077809] UDF-fs: No VRS found
[  121.213134] ISO 9660 Extensions: Microsoft Joliet Level 3
[  121.298269] ISO 9660 Extensions: RRIP_1991A
[  512.208820] UDF-fs: No VRS found
[  512.292913] ISO 9660 Extensions: Microsoft Joliet Level 3
[  512.319193] ISOFS: changing to secondary root
[ 2470.538051] UDF-fs: No VRS found
[ 2471.630801] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2471.744430] ISOFS: changing to secondary root
[ 2471.788337] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2471.919128] UDF-fs: No VRS found
[ 2472.003400] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2472.093331] ISOFS: changing to secondary root
[ 2472.137138] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2475.347939] UDF-fs: No VRS found
[ 2475.432243] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2475.522241] ISOFS: changing to secondary root
[ 2475.566102] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2475.671292] UDF-fs: No VRS found
[ 2475.755625] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2475.845603] ISOFS: changing to secondary root
[ 2475.889459] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2477.058296] UDF-fs: No VRS found
[ 2477.142537] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2477.232552] ISOFS: changing to secondary root
[ 2477.276411] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2477.381606] UDF-fs: No VRS found
[ 2477.467401] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2477.555913] ISOFS: changing to secondary root
[ 2477.599781] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2478.828110] UDF-fs: No VRS found
[ 2478.912408] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2479.022179] ISOFS: changing to secondary root
[ 2479.071832] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2479.177014] UDF-fs: No VRS found
[ 2479.261341] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2479.351320] ISOFS: changing to secondary root
[ 2479.395166] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2480.810739] UDF-fs: No VRS found
[ 2480.895024] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2480.985034] ISOFS: changing to secondary root
[ 2481.028907] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2481.134085] UDF-fs: No VRS found
[ 2481.218429] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2481.308389] ISOFS: changing to secondary root
[ 2481.352249] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2482.733795] UDF-fs: No VRS found
[ 2482.818096] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2482.908090] ISOFS: changing to secondary root
[ 2482.951943] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 2483.065687] UDF-fs: No VRS found
[ 2483.150169] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2483.239954] ISOFS: changing to secondary root
[ 2483.283805] isofs_fill_super: root inode is not a directory. Corrupted media?
```

---

### Post by mrowth on 2008-10-13
1) Got another new Samsung Writemaster DVD writer. PATA this time.
2) Booted Windows. Installed Nero. Tested drive. Worked great. 
3) Booted Linux. Tested drive. Worked great. Linux rules.
4) ...
5) Booted Linux. Tested drive. Buffer I/O errors, "Sense Key : Hardware Error [current]", the usual. Can't even read pristine, commercial CD-ROMs anymore. Linux sucks.
6) Booted Windows. Tested drive. Worked great.
7) Booted Linux. Tested drive. Nothing works.
8) Booted Windows. Updated drive's firmware. 
7) Rebooted.
8) Rebooted again.
9) Booted Linux. Tested. Worked! Linux rules!
10) Reconnected older (known working) Toshiba DVD ROM drive on same IDE cable. 
11) Samsung writer couldn't write error-free anymore. Verifications always failed. dmesg: Failures to "identify". Toshiba drive "disabled".
12) Whatever.

> **mc4man said:**
> If you can get your hands on an 80 for the dvd drives I'd try that.

I did, but the drive (now Secondary Master, and all alone on that cable) is still demoted to UDMA/33.

[   30.494923] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB02, max UDMA/66
[   30.494934] ata4.00: limited to UDMA/33 due to 40-wire cable **(no, it's not!)**
[   30.667732] ata4.00: configured for UDMA/33

What's up with that? 

Also, after successfully (?) burning a disc (and just before verification):

[ 1826.535849] ata4: DRQ=1 with device error, dev_stat 0x59
[ 1826.536075] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1826.536084] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 1826.536085]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1826.536086]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
[ 1826.536089] ata4.00: status: { DRDY ERR }
[ 1826.536109] ata4: soft resetting link
[ 1827.024509] ata4.00: configured for UDMA/33
[ 1827.024532] ata4: EH complete

Verification then fails (this is K3B); the discs seem readable but I didn't exactly inspect every bit.

Even more goes wrong when another drive's on the same cable. (See step 11 above.)

My two harddisks do work at their maximum speeds on their 80-wire cable. (133 and 100 respectively.)

---

### Post by mrowth on 2008-10-14
edit: Oh, never mind.

---

### Post by mrowth on 2008-10-16
> **mrowth said:**
> 
9) Booted Linux. Tested. Worked! Linux rules!

Must've been a fluke, because it's back to giving me not a single working disc. Although libata is not throwing up any "HSM violation" or other exceptions/errors and soft resets with this writer as a single drive.

It doesn't seem to matter what cable I use, or if I have one or two drives connected, or if it's SATA or PATA, or if I burn at full speed or not, or if it's CDs or DVDs, or -R or -RW or -RAM, or ISOs or data or audio.

It only matters if I use Ubuntu or not. Out of six drives - three of them brand new - none worked (except maybe in the beginning). 

So 
at 
a 
loss

---

### Post by mrowth on 2008-10-16
I've noticed something...

After "successfully" (?) writing a disc, and prior to verifying it (or just finishing up), do burning apps normally open and close the drive tray (to mount the new disc?)?

Because I remember that happening that last time I got something verified ok -- 

Usually, though, there're error messages such as...

```
[ 1826.535849] ata4: DRQ=1 with device error, dev_stat 0x59
 [ 1826.536075] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 [ 1826.536084] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
 [ 1826.536085] cdb 25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 [ 1826.536086] res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
 [ 1826.536089] ata4.00: status: { DRDY ERR }
 [ 1826.536109] ata4: soft resetting link
 [ 1827.024509] ata4.00: configured for UDMA/33
 [ 1827.024532] ata4: EH complete
```

...or these (used Brasero for this one)...

```
[ 1301.053047] attempt to access beyond end of device
[ 1301.053053] sr0: rw=0, want=68, limit=4
[ 1301.063396] attempt to access beyond end of device
[ 1301.063399] sr0: rw=0, want=3646140, limit=4
[ 1301.063403] attempt to access beyond end of device
[ 1301.063405] sr0: rw=0, want=3645116, limit=4
[ 1301.063409] attempt to access beyond end of device
[ 1301.063411] sr0: rw=0, want=3644892, limit=4
[ 1301.063414] attempt to access beyond end of device
[ 1301.063416] sr0: rw=0, want=3646132, limit=4
[ 1301.063420] attempt to access beyond end of device
[ 1301.063421] sr0: rw=0, want=3645108, limit=4
[ 1301.063425] attempt to access beyond end of device
[ 1301.063426] sr0: rw=0, want=3644884, limit=4
[ 1301.063430] attempt to access beyond end of device
[ 1301.063431] sr0: rw=0, want=3645540, limit=4
[ 1301.063435] attempt to access beyond end of device
[ 1301.063436] sr0: rw=0, want=3644516, limit=4
[ 1301.063440] attempt to access beyond end of device
[ 1301.063442] sr0: rw=0, want=3644292, limit=4
[ 1301.063445] attempt to access beyond end of device
[ 1301.063447] sr0: rw=0, want=3645532, limit=4
[ 1301.063450] attempt to access beyond end of device
[ 1301.063452] sr0: rw=0, want=3644508, limit=4
[ 1301.063455] attempt to access beyond end of device
[ 1301.063457] sr0: rw=0, want=3644284, limit=4
[ 1301.063461] attempt to access beyond end of device
[ 1301.063462] sr0: rw=0, want=2991724, limit=4
[ 1301.063466] attempt to access beyond end of device
[ 1301.063468] sr0: rw=0, want=2990700, limit=4
[ 1301.063471] attempt to access beyond end of device
[ 1301.063473] sr0: rw=0, want=2990476, limit=4
[ 1301.063476] attempt to access beyond end of device
[ 1301.063478] sr0: rw=0, want=2991716, limit=4
[ 1301.063481] attempt to access beyond end of device
[ 1301.063483] sr0: rw=0, want=2990692, limit=4
[ 1301.063486] attempt to access beyond end of device
[ 1301.063488] sr0: rw=0, want=2990468, limit=4
[ 1301.063491] attempt to access beyond end of device
[ 1301.063493] sr0: rw=0, want=2991124, limit=4
[ 1301.063496] attempt to access beyond end of device
[ 1301.063497] sr0: rw=0, want=2990100, limit=4
[ 1301.063502] attempt to access beyond end of device
[ 1301.063503] sr0: rw=0, want=2989876, limit=4
[ 1301.063507] attempt to access beyond end of device
[ 1301.063508] sr0: rw=0, want=2991116, limit=4
[ 1301.063512] attempt to access beyond end of device
[ 1301.063513] sr0: rw=0, want=2990092, limit=4
[ 1301.063517] attempt to access beyond end of device
[ 1301.063518] sr0: rw=0, want=2989868, limit=4
[ 1301.063522] attempt to access beyond end of device
[ 1301.063523] sr0: rw=0, want=1252, limit=4
[ 1301.063527] attempt to access beyond end of device
[ 1301.063529] sr0: rw=0, want=1028, limit=4
[ 1301.063530] UDF-fs: No partition found (1)
[ 1301.085514] attempt to access beyond end of device
[ 1301.085517] sr0: rw=0, want=68, limit=4
[ 1301.085519] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1301.548400] attempt to access beyond end of device
[ 1301.548405] sr0: rw=0, want=68, limit=4
[ 1301.558867] attempt to access beyond end of device
[ 1301.558874] sr0: rw=0, want=3646140, limit=4
[ 1301.558880] attempt to access beyond end of device
[ 1301.558882] sr0: rw=0, want=3645116, limit=4
[ 1301.558886] attempt to access beyond end of device
[ 1301.558888] sr0: rw=0, want=3644892, limit=4
[ 1301.558892] attempt to access beyond end of device
[ 1301.558895] sr0: rw=0, want=3646132, limit=4
[ 1301.558898] attempt to access beyond end of device
[ 1301.558901] sr0: rw=0, want=3645108, limit=4
[ 1301.558904] attempt to access beyond end of device
[ 1301.558907] sr0: rw=0, want=3644884, limit=4
[ 1301.558911] attempt to access beyond end of device
[ 1301.558913] sr0: rw=0, want=3645540, limit=4
[ 1301.558918] attempt to access beyond end of device
[ 1301.558921] sr0: rw=0, want=3644516, limit=4
[ 1301.558926] attempt to access beyond end of device
[ 1301.558928] sr0: rw=0, want=3644292, limit=4
[ 1301.558932] attempt to access beyond end of device
[ 1301.558935] sr0: rw=0, want=3645532, limit=4
[ 1301.558938] attempt to access beyond end of device
[ 1301.558941] sr0: rw=0, want=3644508, limit=4
[ 1301.558946] attempt to access beyond end of device
[ 1301.558948] sr0: rw=0, want=3644284, limit=4
[ 1301.558952] attempt to access beyond end of device
[ 1301.558954] sr0: rw=0, want=2991724, limit=4
[ 1301.558959] attempt to access beyond end of device
[ 1301.558962] sr0: rw=0, want=2990700, limit=4
[ 1301.558966] attempt to access beyond end of device
[ 1301.558969] sr0: rw=0, want=2990476, limit=4
[ 1301.558973] attempt to access beyond end of device
[ 1301.558975] sr0: rw=0, want=2991716, limit=4
[ 1301.558979] attempt to access beyond end of device
[ 1301.558982] sr0: rw=0, want=2990692, limit=4
[ 1301.558985] attempt to access beyond end of device
[ 1301.558988] sr0: rw=0, want=2990468, limit=4
[ 1301.558992] attempt to access beyond end of device
[ 1301.558994] sr0: rw=0, want=2991124, limit=4
[ 1301.558997] attempt to access beyond end of device
[ 1301.558998] sr0: rw=0, want=2990100, limit=4
[ 1301.559003] attempt to access beyond end of device
[ 1301.559005] sr0: rw=0, want=2989876, limit=4
[ 1301.559009] attempt to access beyond end of device
[ 1301.559012] sr0: rw=0, want=2991116, limit=4
[ 1301.559015] attempt to access beyond end of device
[ 1301.559018] sr0: rw=0, want=2990092, limit=4
[ 1301.559021] attempt to access beyond end of device
[ 1301.559023] sr0: rw=0, want=2989868, limit=4
[ 1301.559027] attempt to access beyond end of device
[ 1301.559030] sr0: rw=0, want=1252, limit=4
[ 1301.559033] attempt to access beyond end of device
[ 1301.559035] sr0: rw=0, want=1028, limit=4
[ 1301.559038] UDF-fs: No partition found (1)
[ 1301.575370] attempt to access beyond end of device
[ 1301.575373] sr0: rw=0, want=68, limit=4
[ 1301.575375] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1302.055886] attempt to access beyond end of device
[ 1302.055891] sr0: rw=0, want=68, limit=4
[ 1302.066624] attempt to access beyond end of device
[ 1302.066631] sr0: rw=0, want=3646140, limit=4
(continues until it gives up trying to mount the disc)

```

...or no error messages, but no ejecting-of-the-disc either...

Am I on to something here? (I know I'm probably talking to myself)

---

### Post by KimBP on 2008-10-17
Well mrowth - you're not completely alone.

I'm experiencing a similar problem. I'm rather new to ubuntu, but managed a week ago or so to RIP a couple of CD's using Sound Juicer. In the beginning my CD's didn't mount, but suddenly it worked. Yesterday I wanted to RIP another one, but can't get it mounted. Have also tryed with some of the ones working last week. Still it won't work. Have been looking for hints but nothing so far. I'll contribute with a few observations though. First result of trying to mount manually. Please ignore some of the danish messages - but choosed to switch from english windows to danish linux in order to make it easier for wife to accept the switch :): 

kbp@kbp2:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=41321748-3ad5-4dbe-83ac-69f889414354 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=e3cecf3a-14f7-4335-a8e2-f21b4f3e27a6 none            swap    sw            
  0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//10.0.0.10/multimedia	/NAS cifs username=kbp,password=<hidden>	0	0
#//10.0.0.10/multimedia	/NAS cifs credentials=~/.smbcredentials 0 0
kbp@kbp2:~$ mount /media/cdrom0
mount: blokenhed /dev/scd0 er skrivebeskyttet, monterer skrivebeskyttet
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       I nogle tilfælde vil du finde nyttige oplysninger i systemlogggen
       - prøv 'dmesg | tail'  eller lignende

kbp@kbp2:~$ dmesg|tail
[31245.865452] sr0: rw=0, want=2476984, limit=912908
[31245.865456] attempt to access beyond end of device
[31245.865459] sr0: rw=0, want=2475960, limit=912908
[31245.865463] attempt to access beyond end of device
[31245.865465] sr0: rw=0, want=2475736, limit=912908
[31245.872839] end_request: I/O error, dev sr0, sector 1248
[31245.877222] end_request: I/O error, dev sr0, sector 1024
[31245.877292] UDF-fs: No partition found (1)
[31248.431221] end_request: I/O error, dev sr0, sector 64
[31248.431375] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

If I put in a data disc it all works fine. 

I did install some updates suggested by the update tool between the day it worked and yesterday. Don't know how to check what packages where updated though.

---

### Post by pauljohn32 on 2008-10-22
Music CDs are NOT SUPPOSED to mount.  That's why data disks mount for you, but music disks do not.  You insert the music disk and then the ripper accesses the disk, but it never gets mounted as a file system.

pj

---

### Post by silentknyght on 2008-11-16
> **mrowth said:**
> So I got a new DVD writer. 

I picked an S-ATA drive this time. Samsung "Super Writemaster"... or TSSTcorp CDDVDW SH-S223F, as far as the computer's concerned. I've never had an S-ATA drive before. I'm pretty sure my Asus A8V Deluxe mobo doesn't support current S-ATA speeds. I expected there to be a jumper or something to downgrade the drive, but there isn't.

Sitting here with the exact same mobo and dvdrw combination.  It does NOT support Sata2, as the drive is, but I can't see how that could be the problem.  Mine just burns coasters left and right for cds, but burned a dvd just fine on the first try.  Seems to read discs of all kinds just fine, too.

I had to plug in an IDE cd-rw drive just to burn an iso.  I'm very new to linux; I used Brasero and it kept reporting an error likely due to overburning.  Wasn't bad media; tried multiple kinds.

I figure it needs either a firmware or a driver update, but I'll be jiggered if I can find one anywhere...

---

### Post by Shant on 2008-11-17
Hey guys, i ve a samsung writer tsstcorp cd dvdw sh-s223f which does not read my dvds any more what should i do and why does this happen. is it due to daemon tools or wat and if it is irrrepairable which one should i buy next. because i have bought two samsungs back to back and boyh screwed up.

---

