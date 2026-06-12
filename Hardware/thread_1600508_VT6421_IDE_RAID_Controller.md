---
title: "VT6421 IDE RAID Controller"
date: 2010-10-19
forum: Hardware
---

### Post by Tee.Gee on 2010-10-19
Hi,

I recently purchased a PCI PATA/SATA controller with a VIA 6421 chipset. After installing the card I found that only drives connected to the PATA port show up and SATA drives remain undetected.

# uname -a
Linux traalet 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux

# lspci -vvv
00:08.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
        Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at b800 [size=16]
        Region 1: I/O ports at b400 [size=16]
        Region 2: I/O ports at b000 [size=16]
        Region 3: I/O ports at a800 [size=16]
        Region 4: I/O ports at a400 [size=32]
        Region 5: I/O ports at a000 [size=256]
        [virtual] Expansion ROM at 40020000 [disabled] [size=64K]
        Capabilities: [e0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: sata_via
        Kernel modules: sata_via

In the scenario below, I have two drives connected to the controller - 1 PATA (an old Seagate ST340016A) and 1 SATA (a newer Seagate ST31000340AS). Unloading the sata_via kernel module and loading it again shows the folloing messages in syslog:

# rmmod sata_via
Oct 19 15:32:01 traalet kernel: [85706.611954] ata8.00: disabled
Oct 19 15:32:01 traalet kernel: [85706.645862] sd 7:0:0:0: [sdc] Synchronizing SCSI cache
Oct 19 15:32:01 traalet kernel: [85706.646000] sd 7:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 19 15:32:01 traalet kernel: [85706.646013] sd 7:0:0:0: [sdc] Stopping disk
Oct 19 15:32:01 traalet kernel: [85706.646044] sd 7:0:0:0: [sdc] START_STOP FAILED
Oct 19 15:32:01 traalet kernel: [85706.646051] sd 7:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 19 15:32:01 traalet kernel: [85706.650192] sata_via 0000:00:08.0: PCI INT A disabled
# modprobe sata_via
Oct 19 15:32:28 traalet kernel: [85733.857954] sata_via 0000:00:08.0: version 2.6
Oct 19 15:32:28 traalet kernel: [85733.858000] sata_via 0000:00:08.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 19 15:32:28 traalet kernel: [85733.858117] sata_via 0000:00:08.0: routed to hard irq line 11
Oct 19 15:32:28 traalet kernel: [85733.858320] scsi8 : sata_via
Oct 19 15:32:28 traalet kernel: [85733.864935] scsi9 : sata_via
Oct 19 15:32:28 traalet kernel: [85733.870043] scsi10 : sata_via
Oct 19 15:32:28 traalet kernel: [85733.870248] ata9: SATA max UDMA/133 port i16@0xb800 bmdma 0xa400 irq 11
Oct 19 15:32:28 traalet kernel: [85733.870259] ata10: SATA max UDMA/133 port i16@0xb400 bmdma 0xa408 irq 11
Oct 19 15:32:28 traalet kernel: [85733.870268] ata11: PATA max UDMA/133 port i16@0xb000 bmdma 0xa410 irq 11
Oct 19 15:32:29 traalet kernel: [85734.206561] ata9: SATA link down (SStatus 0 SControl 310)
Oct 19 15:32:29 traalet kernel: [85734.534566] ata10: SATA link down (SStatus 0 SControl 310)
Oct 19 15:32:29 traalet kernel: [85734.696582] ata11.00: ATA-5: ST340016A, 3.10, max UDMA/100
Oct 19 15:32:29 traalet kernel: [85734.696594] ata11.00: 78165360 sectors, multi 0: LBA
Oct 19 15:32:29 traalet kernel: [85734.704795] ata11.00: configured for UDMA/100
Oct 19 15:32:29 traalet kernel: [85734.705137] scsi 10:0:0:0: Direct-Access     ATA      ST340016A        3.10 PQ: 0 ANSI: 5
Oct 19 15:32:29 traalet kernel: [85734.705636] sd 10:0:0:0: Attached scsi generic sg3 type 0
Oct 19 15:32:29 traalet kernel: [85734.714498] sd 10:0:0:0: [sdc] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
Oct 19 15:32:29 traalet kernel: [85734.714701] sd 10:0:0:0: [sdc] Write Protect is off
Oct 19 15:32:29 traalet kernel: [85734.714711] sd 10:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Oct 19 15:32:29 traalet kernel: [85734.714788] sd 10:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 19 15:32:29 traalet kernel: [85734.715336]  sdc: sdc1 sdc2 sdc3 < sdc5 sdc6 >
Oct 19 15:32:29 traalet kernel: [85734.765853]  sdc1: <solaris: [s0] sdc7 [s1] sdc8 [s2] sdc9 [s8] sdc10 >
Oct 19 15:32:29 traalet kernel: [85734.771500] sd 10:0:0:0: [sdc] Attached SCSI disk
# lsmod | grep via
sata_via                7472  0
via_agp                 5322  1
via686a                11126  0
i2c_viapro              5841  0
agpgart                32075  3 ttm,drm,via_agp
pata_via                7300  6
# scsiadd -s 10
Oct 19 15:41:20 traalet kernel: [86265.927669] ata11: soft resetting link
Oct 19 15:41:21 traalet kernel: [86266.096452] ata11.00: configured for UDMA/100
Oct 19 15:41:21 traalet kernel: [86266.096469] ata11: EH complete
Oct 19 15:41:21 traalet kernel: [86266.097064] ata11: soft resetting link
Oct 19 15:41:21 traalet kernel: [86266.268453] ata11.00: configured for UDMA/100
Oct 19 15:41:21 traalet kernel: [86266.268469] ata11: EH complete
# lsscsi
[10:0:0:0]   disk    ATA      ST340016A        3.10  /dev/sdc

I have tried the disk on another machine and it worked just fine.
Any suggestions how to get the SATA part of that controller working?

Cheers,
  Tom

---

### Post by Tee.Gee on 2010-10-19
I have spotted a similar card in the 'incompatibility list' and posted an update there.

The PATA port works, the SATA ports don't.
Tested with
Release:        10.10
Codename:       maverick
Linux 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux

---

