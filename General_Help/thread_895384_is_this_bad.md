---
title: "is this bad?"
date: 2008-08-20
forum: General Help
---

### Post by anv on 2008-08-20
I started to get this error during boot ups, couple of days ago. how should I proceed?



[   54.440670] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   54.440733] ata1.00: BMDMA stat 0x65
[   54.440783] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   54.440784]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   54.440844] ata1.00: status: { DRDY ERR }
[   54.440891] ata1.00: error: { UNC }
[   54.455374] ata1.00: configured for UDMA/100
[   54.455380] ata1: EH complete
[   56.652869] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   56.652919] ata1.00: BMDMA stat 0x65
[   56.652968] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   56.652968]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   56.653029] ata1.00: status: { DRDY ERR }
[   56.653076] ata1.00: error: { UNC }
[   56.682092] ata1.00: configured for UDMA/100
[   56.682096] ata1: EH complete
[   59.180782] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   59.180832] ata1.00: BMDMA stat 0x65
[   59.180881] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   59.180882]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   59.180949] ata1.00: status: { DRDY ERR }
[   59.180996] ata1.00: error: { UNC }
[   59.196120] ata1.00: configured for UDMA/100
[   59.196123] ata1: EH complete
[   61.692121] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   61.692172] ata1.00: BMDMA stat 0x65
[   61.692220] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   61.692221]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   61.692281] ata1.00: status: { DRDY ERR }
[   61.692328] ata1.00: error: { UNC }
[   61.706180] ata1.00: configured for UDMA/100
[   61.706182] ata1: EH complete
[   63.905825] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   63.905876] ata1.00: BMDMA stat 0x65
[   63.905924] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   63.905925]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   63.905986] ata1.00: status: { DRDY ERR }
[   63.906033] ata1.00: error: { UNC }
[   63.920910] ata1.00: configured for UDMA/100
[   63.920913] ata1: EH complete
[   66.118019] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.118069] ata1.00: BMDMA stat 0x65
[   66.118117] ata1.00: cmd c8/00:08:27:55:a8/00:00:00:00:00/e4 tag 0 dma 4096 in
[   66.118118]          res 51/40:05:2a:55:a8/00:00:00:00:00/e4 Emask 0x9 (media error)
[   66.118179] ata1.00: status: { DRDY ERR }
[   66.118226] ata1.00: error: { UNC }
[   66.147649] ata1.00: configured for UDMA/100
[   66.147654] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   66.147656] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   66.147659] Descriptor sense data with sense descriptors (in hex):
[   66.147661]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   66.147665]         04 a8 55 2a 
[   66.147666] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   66.147670] end_request: I/O error, dev sda, sector 78140714
[   66.147676] ata1: EH complete
[   66.147669] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   66.147831] sd 0:0:0:0: [sda] Write Protect is off
[   66.147833] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   66.151493] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.159269] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   66.159279] sd 0:0:0:0: [sda] Write Protect is off
[   66.159281] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   66.159292] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by WRDN on 2008-08-20
How is your actual usage affected, and what had you changed before the errors started appearing? It is usually OK to disregard them if there have been no visible issues.

---

### Post by anv on 2008-08-20
non hardware change, and regular updates only. I don't remember any major installations. 

I remember now it started after one suspend, instead of shutdown, I have before experienced other kind of problems due suspend, hibernate, like they wouldn't actually work so well

side effects:

well yesterday when I opened my machine it went "stuck" when I opened Firestarter software which in some reason inside Hardy wont start in beginning. I don't mean the GUI, but the process fails. so while it were open all other software didn't open after choosing them from menu, and I decided to uninstall Firestarter due I have had problem lately with that software. After it shutting it down (and couple uninstall and install) all software run normally, but I'm little troubled if system is on way to fall soon I don't want to loose my work.
 As in my earlier threads concerning hard disk becoming old sooner than in windows environment I am not sure is this the case again, with my 10 months old hd. This far I haven't had much older than year old disks and some times younger, while using Ubuntu. I do normal desktop work nothing specially demand for the disks

---

### Post by anv on 2008-08-22
after some install and reinstall processes I just noticed yesterday that during boot it didn't anymore give those errors.

---

