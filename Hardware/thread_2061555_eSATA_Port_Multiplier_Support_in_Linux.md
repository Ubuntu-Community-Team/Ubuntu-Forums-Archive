---
title: "eSATA Port Multiplier Support in Linux?"
date: 2012-09-22
forum: Hardware
---

### Post by mattlach on 2012-09-22
Hey all,

I have been struggling with this issue for 2 years now without any luck.

Could definitely use some help.

This forum post from 2007 indicates that PMP support is back in linux, and specifically mentions the controller I have as working.


From my lspci:
```

03:00.0 SATA controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
```

The post from 2007 states support will be officially added in the  2.6.24 kernel.

Trying today using the latest release of Ubuntu 12.04 and the 3.2.0-29-generic kernel, it still isn't working.

Relevant sections from my dmesg:
```

[    3.134045] ata4: SATA max UDMA/100 host m128@0xd2405000 port 0xd2402000 irq 18
[    7.533451] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    7.534406] ata4.15: Port Multiplier 1.1, 0x1a62:0x0003 r23, 14 ports, feat 0x0/0x0
[    7.534751] ata4.15: Asynchronous notification not supported, hotplug won't work on fan-out ports. Use warm-plug instead.
[    7.538981] ata4.00: hard resetting link
[    8.340640] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    8.341000] ata4.01: hard resetting link
[    9.112593] ata4.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    9.112944] ata4.02: hard resetting link
[    9.432957] ata4.02: SATA link down (SStatus 0 SControl 320)
[    9.433374] ata4.03: hard resetting link
[    9.752988] ata4.03: SATA link down (SStatus 0 SControl 320)
[    9.753390] ata4.04: hard resetting link
[   10.072946] ata4.04: SATA link down (SStatus 0 SControl 320)
[   10.073353] ata4.05: hard resetting link
[   10.397029] ata4.05: SATA link down (SStatus 0 SControl 320)
[   10.397449] ata4.06: hard resetting link
[   10.717024] ata4.06: SATA link down (SStatus 0 SControl 320)
[   10.717437] ata4.07: hard resetting link
[   11.037025] ata4.07: SATA link down (SStatus 0 SControl 320)
[   11.037436] ata4.08: hard resetting link
[   11.357024] ata4.08: SATA link down (SStatus 0 SControl 320)
[   11.357437] ata4.09: hard resetting link
[   11.677092] ata4.09: SATA link down (SStatus 0 SControl 320)
[   11.677503] ata4.10: hard resetting link
[   11.997069] ata4.10: SATA link down (SStatus 0 SControl 320)
[   11.997482] ata4.11: hard resetting link
[   12.316980] ata4.11: SATA link down (SStatus 0 SControl 320)
[   12.317387] ata4.12: hard resetting link
[   12.636990] ata4.12: SATA link down (SStatus 0 SControl 320)
[   12.637395] ata4.13: hard resetting link
[   12.956992] ata4.13: SATA link down (SStatus 0 SControl 320)
[   12.995061] ata4.00: ATA-6: Drobo   3rd Gen DRDR3-A, v2.0.4, max UDMA/133
[   12.995349] ata4.00: 17179869184 sectors, multi 0: LBA48 
[   13.031616] ata4.00: configured for UDMA/100
[   13.049973] ata4.01: ATA-6: Drobo   3rd Gen DRDR3-A, v2.0.4, max UDMA/133
[   13.050259] ata4.01: 17179869184 sectors, multi 0: LBA48 
[   13.050895] ata4.01: configured for UDMA/100
[   13.051191] ata4: EH complete
[   13.053543] sd 3:1:0:0: [sdc] 17179869184 512-byte logical blocks: (8.79 TB/8.00 TiB)
[   13.053684] sd 3:1:0:0: [sdc] Write Protect is off
[   13.053693] sd 3:1:0:0: [sdc] Mode Sense: 00 3a 00 00
[   13.053761] sd 3:1:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.355696]  sdc: unknown partition table
[   36.356913] sd 3:1:0:0: [sdc] Attached SCSI disk
[   66.848203] ata4.00: failed to read SCR 1 (Emask=0x40)
[   66.848507] ata4.01: failed to read SCR 1 (Emask=0x40)
[   66.848742] ata4.02: failed to read SCR 1 (Emask=0x40)
[   66.848974] ata4.03: failed to read SCR 1 (Emask=0x40)
[   66.849204] ata4.04: failed to read SCR 1 (Emask=0x40)
[   66.849435] ata4.05: failed to read SCR 1 (Emask=0x40)
[   66.849666] ata4.06: failed to read SCR 1 (Emask=0x40)
[   66.849898] ata4.07: failed to read SCR 1 (Emask=0x40)
[   66.850128] ata4.08: failed to read SCR 1 (Emask=0x40)
[   66.850359] ata4.09: failed to read SCR 1 (Emask=0x40)
[   66.850591] ata4.10: failed to read SCR 1 (Emask=0x40)
[   66.850821] ata4.11: failed to read SCR 1 (Emask=0x40)
[   66.851067] ata4.12: failed to read SCR 1 (Emask=0x40)
[   66.851300] ata4.13: failed to read SCR 1 (Emask=0x40)
[   66.851535] ata4.15: exception Emask 0x4 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.851822] ata4.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.852186] ata4.00: failed command: READ DMA
[   66.852405] ata4.00: cmd c8/00:08:38:03:00/00:00:00:00:00/e0 tag 1 dma 4096 in
[   66.854382] ata4.00: status: { DRDY }
[   66.854581] ata4.01: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.854917] ata4.01: failed command: READ DMA
[   66.855157] ata4.01: cmd c8/00:08:30:03:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   66.855812] ata4.01: status: { DRDY }
[   66.856034] ata4.02: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.856364] ata4.03: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.856692] ata4.04: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.857021] ata4.05: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.857350] ata4.06: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.857681] ata4.07: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.858009] ata4.08: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.858337] ata4.09: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.858664] ata4.10: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.859001] ata4.11: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.859328] ata4.12: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.859655] ata4.13: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[   66.859984] ata4.15: hard resetting link
[   69.044183] ata4.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   69.044491] ata4.15: PMP revalidation failed (errno=-19)
[   74.044129] ata4.15: hard resetting link
[   76.228167] ata4.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   76.228497] ata4.15: PMP revalidation failed (errno=-19)
[   76.228738] ata4.15: limiting SATA link speed to 1.5 Gbps
[   81.228088] ata4.15: hard resetting link
[   83.412174] ata4.15: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[   83.412521] ata4.15: PMP revalidation failed (errno=-19)
[   83.412809] ata4.15: failed to recover PMP after 5 tries, giving up
[   83.414321] ata4.15: Port Multiplier detaching
[   83.414565] ata4.00: disabled
[   83.414746] ata4.01: disabled
[   83.414958] ata4.00: disabled
[   88.412142] ata4: hard resetting link
[   90.596147] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   95.596083] ata4.00: qc timeout (cmd 0xec)
[   95.596311] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   95.596575] ata4: hard resetting link
[   97.780176] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[  107.780099] ata4.00: qc timeout (cmd 0xec)
[  107.780339] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  107.780604] ata4: limiting SATA link speed to 1.5 Gbps
[  107.780842] ata4: hard resetting link
[  109.964141] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[  139.964132] ata4.00: qc timeout (cmd 0xec)
[  139.964144] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  139.964153] ata4: hard resetting link
[  142.148156] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[  142.148172] ata4.00: device reported invalid CHS sector 0
[  142.148220] sd 3:1:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  142.148227] sd 3:1:0:0: [sdc]  Sense Key : Aborted Command [current] [descriptor]
[  142.148265] sd 3:1:0:0: [sdc]  Add. Sense: No additional sense information
[  142.148272] sd 3:1:0:0: [sdc] CDB: Read(10): 28 00 00 00 03 30 00 00 08 00
[  142.148288] end_request: I/O error, dev sdc, sector 816
[  142.148594] Buffer I/O error on device sdc, logical block 102
[  142.149546] ata4: EH complete
[  142.149586] ata4.00: detaching (SCSI 3:0:0:0)
[  142.153619] ata4.01: detaching (SCSI 3:1:0:0)
[  142.154820] sd 3:1:0:0: [sdc] Synchronizing SCSI cache
[  142.154943] sd 3:1:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  142.154952] sd 3:1:0:0: [sdc] Stopping disk
[  142.154976] sd 3:1:0:0: [sdc] START_STOP FAILED
[  142.154981] sd 3:1:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
```

I DESPERATELY NEED port multiplier working.

Can anyone suggest either:

1.) How I might get it to work with my current controller; or

2.) A controller with which it will work

Thank you very much,
Matt

---

### Post by TomB19 on 2012-10-26
Your system is clearly identifying a port multiplier.  The support is there.  Get your hardware together and it will work.

I have been using a pair of Si3132r5 SATA cards to drive 16 external drives on 4 x 4 port multipliers in a ZFS array for two years now.  It worked well with Ubuntu 11.10 and it's working perfectly with 12.04.

Specifically, I have a pair of Rosewill RSV-S8 enclosures.

Earlier versions, like your r1 card, of the 3132 are buggy and I recommend staying away from them.  Get r5 based cards and you should be good to go.

I've tried about every card out there and can speak to them all.  Marvell 9128 based cards work great in Linux but the port multiplier support is buggy.  There was a firmware fix early this year.  I tried it and it didn't work.  Most also report it not working.  A few people said it works perfectly.  The issue is that I was seeing only 7 of 8 drives on two eSATA connections to a pair of 4 drive port multiplier strings.  All 8 drives show when I use Si3132r5 cards.

The Marvell issue might be Linux related as the firmware fix seems to have solved the problem for Windows users.  I suspect the problem is closer to the chip and the bug work-around is not implemented in linux but I don't know that.  It should be straight up ACPI.

Even better than the 3132 solution is to use your motherboard ports for eSATA.  This is easily done with an eSATA plate such as:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003)

I think AMD and Intel have the only SATA support that is absolutely bug free.

---

### Post by tietze on 2013-01-22
> **TomB19 said:**
> I have been using a pair of Si3132r5 SATA cards [...]

Earlier versions, like your r1 card, of the 3132 are buggy and I recommend staying away from them.  Get r5 based cards and you should be good to go.

Hi, I'm curious about how to find a revision 5 sil 3132 controller out there. I need my sil 3132 revision 1 replaced, so I'm looking for a card with a never revision. But I have found that the revision of the card is usually not disclosed.

---

