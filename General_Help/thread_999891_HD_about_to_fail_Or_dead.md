---
title: "HD about to fail? Or dead?"
date: 2008-12-02
forum: General Help
---

### Post by quad3d@work on 2008-12-02
I got two 500GB and one 750GB HD. I made 500GB partition on all three and tried to do RAID 5.

During resync, it'll fail after about couple a minutes. When I do mdadm detail on the md2 device I see one active, one spare rebuilding, and one set to faulty.

dmesg shows the following... does that mean the drive about to go bad? smartctl shows SMART on /dev/sdc still good. I'm badblock the drive right now....

```

[31859.608042] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31859.608079] ata5.00: BMDMA stat 0x64
[31859.608108] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31859.608109]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31859.608205] ata5.00: status: { DRDY ERR }
[31859.608251] ata5.00: error: { UNC }
[31859.633012] ata5.00: configured for UDMA/133
[31859.652666] ata5.01: configured for UDMA/133
[31859.652679] ata5: EH complete
[31861.587076] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31861.587110] ata5.00: BMDMA stat 0x64
[31861.587139] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31861.587141]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31861.587236] ata5.00: status: { DRDY ERR }
[31861.587283] ata5.00: error: { UNC }
[31861.609016] ata5.00: configured for UDMA/133
[31861.624666] ata5.01: configured for UDMA/133
[31861.624676] ata5: EH complete
[31863.711277] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31863.711311] ata5.00: BMDMA stat 0x64
[31863.711339] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31863.711341]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31863.711436] ata5.00: status: { DRDY ERR }
[31863.711483] ata5.00: error: { UNC }
[31863.733196] ata5.00: configured for UDMA/133
[31863.748677] ata5.01: configured for UDMA/133
[31863.748687] ata5: EH complete
[31865.678296] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31865.678330] ata5.00: BMDMA stat 0x64
[31865.678358] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31865.678360]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31865.678455] ata5.00: status: { DRDY ERR }
[31865.678501] ata5.00: error: { UNC }
[31865.701217] ata5.00: configured for UDMA/133
[31865.716680] ata5.01: configured for UDMA/133
[31865.716690] ata5: EH complete
[31867.636289] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31867.636323] ata5.00: BMDMA stat 0x64
[31867.636352] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31867.636354]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31867.636450] ata5.00: status: { DRDY ERR }
[31867.636496] ata5.00: error: { UNC }
[31867.661258] ata5.00: configured for UDMA/133
[31867.676680] ata5.01: configured for UDMA/133
[31867.676690] ata5: EH complete
[31869.903621] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31869.903655] ata5.00: BMDMA stat 0x64
[31869.903683] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31869.903685]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31869.903780] ata5.00: status: { DRDY ERR }
[31869.903826] ata5.00: error: { UNC }
[31869.924555] ata5.00: configured for UDMA/133
[31869.940637] ata5.01: configured for UDMA/133
[31869.940649] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[31869.940654] sd 4:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[31869.940660] Descriptor sense data with sense descriptors (in hex):
[31869.940663]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[31869.940677]         00 6f 95 53 
[31869.940683] sd 4:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[31869.940690] end_request: I/O error, dev sdc, sector 7312723
[31869.940732] Buffer I/O error on device sdc, logical block 914090
[31869.940778] ata5: EH complete
[31869.941329] sd 4:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[31869.941843] sd 4:0:0:0: [sdc] Write Protect is off
[31869.941851] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[31872.149934] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31872.149968] ata5.00: BMDMA stat 0x64
[31872.149996] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31872.149997]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31872.150091] ata5.00: status: { DRDY ERR }
[31872.150127] ata5.00: error: { UNC }
[31872.173838] ata5.00: configured for UDMA/133
[31872.188680] ata5.01: configured for UDMA/133
[31872.188694] ata5: EH complete
[31874.270111] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31874.270144] ata5.00: BMDMA stat 0x64
[31874.270172] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31874.270173]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31874.270267] ata5.00: status: { DRDY ERR }
[31874.270303] ata5.00: error: { UNC }
[31874.294038] ata5.00: configured for UDMA/133
[31874.308661] ata5.01: configured for UDMA/133
[31874.308673] ata5: EH complete
[31876.536445] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31876.536480] ata5.00: BMDMA stat 0x64
[31876.536509] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31876.536510]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31876.536606] ata5.00: status: { DRDY ERR }
[31876.536633] ata5.00: error: { UNC }
[31876.561379] ata5.00: configured for UDMA/133
[31876.580644] ata5.01: configured for UDMA/133
[31876.580656] ata5: EH complete
[31878.951897] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[31878.951931] ata5.00: BMDMA stat 0x64
[31878.951959] ata5.00: cmd c8/00:08:50:95:6f/00:00:00:00:00/e0 tag 0 dma 4096 in
[31878.951960]          res 51/40:00:53:95:6f/40:00:00:00:00/e0 Emask 0x9 (media error)
[31878.952055] ata5.00: status: { DRDY ERR }
[31878.952091] ata5.00: error: { UNC }
[31878.972846] ata5.00: configured for UDMA/133
[31878.988683] ata5.01: configured for UDMA/133
[31878.988693] ata5: EH complete

```

---

### Post by tgalati4 on 2008-12-02
What model are the drives?  What is the RAID controller chipset?  What does a google search on both tell you?

Buffer I/O errors can be caused by all sorts of things.  How is the cabling?  Is the power supply dropping voltage during boot?  Check the 5V and 12V lines with a meter during boot.  Any droppage could be a power supply problem.

---

### Post by fjgaude on 2008-12-02
After you have booted what gets mounted? Show us what

```
df -h
```

looks like.

---

### Post by quad3d@work on 2008-12-02
@tgalati4
I don't have a voltmeter. Could be the PSU, it's Antec 380W running Core2Quad 6600, 4GB RAM, 2x250GB 2X500GB 1X750GB HDs. ):P

I can pull those 250GBs out tonight and see that works.


@fjgaude
I'm stunnel into the box sitting at home from work right now. Can't reboot or I'll lose the tunnel... :)

I will check when I get home tonight.

----------------
The same box was running 2X250GB and 1x200GB HD before. I upgraded HDs last night.

---

### Post by quad3d@work on 2008-12-02
Well shoot.... HD IS bad.

badblocks reveals....
```

Pass completed, 464 bad blocks found.

```

---

