---
title: "Hot-plugging SATA drive (via backplane)"
date: 2010-07-31
forum: Hardware
---

### Post by scouter on 2010-07-31
I installed 4 SATA drives to SATA backplane for RAID-5 array.  Drives are connected to terrible Silicon Image 3114 (4 SATA 150 Ports) PCI card. This card should, according its specs and my interpretation, support hot-plugging (connecting/disconnecting SATA drive on fly) if using SATA backplane. 

The drives contain yet no partitions. I booted computer and saw from dmesg that all the drives were detected correcly. Then I disconnected (shutdown) one SATA drive via SATA backplane (pushing disable button on it). After a while I connected (enable) the SATA drive again.

I got following lines to dmesg:

```

[  600.941797] ata6: SError: { PHYRdyChg }
[  600.941814] ata6: hard resetting link
[  601.664044] ata6: SATA link down (SStatus 0 SControl 310)
[  606.664038] ata6: hard resetting link
[  606.984039] ata6: SATA link down (SStatus 0 SControl 310)
[  611.984046] ata6: hard resetting link
[  612.304041] ata6: SATA link down (SStatus 0 SControl 310)
[  612.304059] ata6.00: disabled
[  612.304084] ata6: EH complete
[  612.304105] ata6.00: detaching (SCSI 5:0:0:0)
[  612.320867] sd 5:0:0:0: [sdc] Synchronizing SCSI cache
[  612.321842] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  612.321856] sd 5:0:0:0: [sdc] Stopping disk
[  612.321894] sd 5:0:0:0: [sdc] START_STOP FAILED
[  612.321899] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  622.214344] ata6: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[  622.214357] ata6: SError: { PHYRdyChg CommWake }
[  622.214376] ata6: hard resetting link
[  627.976033] ata6: link is slow to respond, please be patient (ready=-19)
[  631.392061] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  631.400384] ata6.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[  631.400392] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[  631.408898] ata6.00: configured for UDMA/100
[  631.408916] ata6: EH complete
[  631.409129] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[  631.409517] sd 5:0:0:0: Attached scsi generic sg5 type 0
[  631.409591] sd 5:0:0:0: [sdf] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  631.409756] sd 5:0:0:0: [sdf] Write Protect is off
[  631.409764] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[  631.409847] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  631.410321]  sdf: unknown partition table
[  631.420982] sd 5:0:0:0: [sdf] Attached SCSI disk
```what I can understand is that the SATA drive was disconnected and later connected again. The question is, was the disconnection/reconnection completely successful ? 

Dare I do this again when the proper RAID-5 array is built and it will contain real data?

---

### Post by dreamgear on 2010-08-06
Boy I hope there's someone in here who can give some kind of knowledgeable answer.  I have an almost identical question.

I'm running 10.04 Lucid Lynx server on an newly built system - Intel H55HC board with Intel I3-540 processor.

I have a hot-swap disk cage with 4x WD 2TB 7200RPM drives.

I want to hot-swap two of the disks.  When I remove them (after unmounting) I get the following messages (as revealed by dmesg):
[FONT="Courier New"][SIZE="2"][INDENT][ 2050.175552] ata3: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 2050.175817] ata3: irq_stat 0x00400040, connection status changed
[ 2050.176107] ata3: SError: { PHYRdyChg 10B8B DevExch }
[ 2050.176420] ata3: hard resetting link
[ 2050.923016] ata3: SATA link down (SStatus 0 SControl 300)
[ 2055.912461] ata3: hard resetting link
[ 2056.261745] ata3: SATA link down (SStatus 0 SControl 300)
[ 2056.261758] ata3: limiting SATA link speed to 1.5 Gbps
[ 2056.605713] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 2056.606248] ata4: irq_stat 0x00400040, connection status changed
[ 2056.606814] ata4: SError: { PHYRdyChg 10B8B DevExch }
[ 2056.607406] ata4: hard resetting link
[ 2057.349479] ata4: SATA link down (SStatus 0 SControl 300)
[ 2061.251193] ata3: hard resetting link
[ 2061.600498] ata3: SATA link down (SStatus 0 SControl 310)
[ 2061.600510] ata3.00: disabled
[ 2061.600523] ata3: EH complete
[ 2061.600562] ata3.00: detaching (SCSI 2:0:0:0)
[ 2061.631552] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
[ 2061.631718] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2061.631724] sd 2:0:0:0: [sdc] Stopping disk
[ 2061.631733] sd 2:0:0:0: [sdc] START_STOP FAILED
[ 2061.631736] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2062.338960] ata4: hard resetting link
[ 2062.688230] ata4: SATA link down (SStatus 0 SControl 300)
[ 2062.688241] ata4: limiting SATA link speed to 1.5 Gbps
[ 2067.677655] ata4: hard resetting link
[ 2068.026983] ata4: SATA link down (SStatus 0 SControl 310)
[ 2068.026994] ata4.00: disabled
[ 2068.027005] ata4: EH complete
[ 2068.027062] ata4.00: detaching (SCSI 3:0:0:0)
[ 2068.058106] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
[ 2068.058144] sd 3:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2068.058149] sd 3:0:0:0: [sdd] Stopping disk
[ 2068.058158] sd 3:0:0:0: [sdd] START_STOP FAILED
[ 2068.058160] sd 3:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
jeff@squirrel:~$
[/INDENT][/SIZE][/FONT]

The question is, is this normal?  I've not been able to see any problem, but I want to know if these messages should be expected.

When I reinsert the two drives I get more messages:
[FONT="Courier New"][SIZE="2"][INDENT][ 7447.305647] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 7447.305653] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 7447.305658] ata1: irq_stat 0x00400040, connection status changed
[ 7447.305662] ata1: SError: { PHYRdyChg 10B8B DevExch }
[ 7447.305670] ata1: hard resetting link
[ 7447.310217] ata2: irq_stat 0x00400040, connection status changed
[ 7447.311511] ata2: SError: { PHYRdyChg 10B8B DevExch }
[ 7447.312836] ata2: hard resetting link
[ 7447.538488] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[ 7447.539719] ata4: irq_stat 0x00000040, connection status changed
[ 7447.541077] ata4: SError: { RecovComm PHYRdyChg CommWake DevExch }
[ 7447.542584] ata4: hard resetting link
[ 7448.282797] ata4: SATA link down (SStatus 0 SControl 300)
[ 7448.282808] ata4: EH complete
[ 7448.532302] ata1: SATA link down (SStatus 0 SControl 300)
[ 7448.532311] ata1.00: link offline, clearing class 1 to NONE
[ 7448.578091] ata1: hard resetting link
[ 7448.609857] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[ 7448.611254] ata4: irq_stat 0x00400040, connection status changed
[ 7448.612854] ata4: SError: { RecovComm PHYRdyChg CommWake DevExch }
[ 7448.614597] ata4: hard resetting link
[ 7453.082668] ata2: link is slow to respond, please be patient (ready=0)
[ 7453.960820] ata1: link is slow to respond, please be patient (ready=0)
[ 7454.399892] ata4: link is slow to respond, please be patient (ready=0)
[ 7456.744952] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7456.780966] ata2.00: configured for UDMA/133
[ 7456.780972] ata2: EH complete
[ 7457.713237] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7457.749425] ata1.00: configured for UDMA/133
[ 7457.749431] ata1: EH complete
[ 7458.601053] ata4: COMRESET failed (errno=-16)
[ 7458.602755] ata4: hard resetting link
[ 7460.129404] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 7460.129410] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 7460.129415] ata2: irq_stat 0x00400040, connection status changed
[ 7460.129420] ata2: SError: { PHYRdyChg 10B8B DevExch }
[ 7460.129427] ata2: hard resetting link
[ 7460.135809] ata1: irq_stat 0x00400040, connection status changed
[ 7460.137465] ata1: SError: { PHYRdyChg 10B8B DevExch }
[ 7460.139145] ata1: hard resetting link
[ 7460.212549] ata3: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[ 7460.214059] ata3: irq_stat 0x00000040, connection status changed
[ 7460.215770] ata3: SError: { RecovComm PHYRdyChg CommWake DevExch }
[ 7460.217548] ata3: hard resetting link
[ 7464.389159] ata4: link is slow to respond, please be patient (ready=0)
[ 7465.915634] ata1: link is slow to respond, please be patient (ready=0)
[ 7465.915946] ata2: link is slow to respond, please be patient (ready=0)
[ 7466.005447] ata3: link is slow to respond, please be patient (ready=0)
[ 7468.600294] ata4: COMRESET failed (errno=-16)
[ 7468.601779] ata4: hard resetting link
[ 7469.039366] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7469.075254] ata1.00: configured for UDMA/133
[ 7469.075261] ata1: EH complete
[ 7469.338725] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7469.377672] ata2.00: configured for UDMA/133
[ 7469.377679] ata2: EH complete
[ 7470.186664] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7470.196873] ata4.00: ATA-8: WDC WD2001FASS-00U0B0, 01.00101, max UDMA/133
[ 7470.196878] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[ 7470.200350] ata4.00: configured for UDMA/133
[ 7470.200358] ata4: EH complete
[ 7470.200500] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2001FASS-0 01.0 PQ: 0 ANSI: 5
[ 7470.200700] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 7470.200968] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 7470.201049] sd 3:0:0:0: [sdc] Write Protect is off
[ 7470.201055] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[ 7470.201101] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7470.201366]  sdc: unknown partition table
[ 7470.206602] sd 3:0:0:0: [sdc] Attached SCSI disk
[ 7470.206882] ata3: COMRESET failed (errno=-16)
[ 7470.208588] ata3: hard resetting link
[ 7475.984419] ata3: link is slow to respond, please be patient (ready=0)
[ 7480.235462] ata3: COMRESET failed (errno=-16)
[ 7480.236981] ata3: hard resetting link
[ 7481.283272] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7481.302440] ata3.00: ATA-8: WDC WD2001FASS-00U0B0, 01.00101, max UDMA/133
[ 7481.302446] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[ 7481.305596] ata3.00: configured for UDMA/133
[ 7481.305607] ata3: EH complete
[ 7481.305752] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2001FASS-0 01.0 PQ: 0 ANSI: 5
[ 7481.305954] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 7481.306100] sd 2:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 7481.306157] sd 2:0:0:0: [sdd] Write Protect is off
[ 7481.306161] sd 2:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[ 7481.306191] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7481.306552]  sdd: unknown partition table
[ 7481.312636] sd 2:0:0:0: [sdd] Attached SCSI disk
jeff@squirrel:~$
[/INDENT][/SIZE][/FONT]

I can then mount and use the drives without incident:
[FONT="Courier New"][SIZE="2"][INDENT][ 7648.578187] EXT4-fs (sdc): mounted filesystem with ordered data mode
[ 7650.243049] EXT4-fs (sdd): mounted filesystem with ordered data mode
jeff@squirrel:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0              96121548   1568132  89670632   2% /
none                   1921120       268   1920852   1% /dev
none                   1925676         0   1925676   0% /dev/shm
none                   1925676       268   1925408   1% /var/run
none                   1925676         0   1925676   0% /var/lock
none                   1925676         0   1925676   0% /lib/init/rw
none                  96121548   1568132  89670632   2% /var/lib/ureadahead/debugfs
/dev/md2             1845856816 132421664 1621130620   8% /home
/dev/sdc             1953267136 105394424 1750196984   6% /bigd1
/dev/sdd             1953267136 104402004 1751189404   6% /bigd2
jeff@squirrel:~$
[/INDENT][/SIZE][/FONT]

I'm somewhat concerned because the links to ata1 and ata2 are also reset - these drives hold the raid set with the system disk.

So what can you all tell me?  Thanks in advance...

---

