---
title: "Problems with ATA1"
date: 2008-09-02
forum: Hardware
---

### Post by Schuttwegraeumer on 2008-09-02
Since the Cahnge to Ubuntu 8.04 there is a TEst-MSG after the bootlogo.
And since this change I can see a ATA1 Error sometimes.
I think this error happend befor too but i could not see it.

> Aug 31 23:26:21 hell kernel: [ 1191.317565] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Aug 31 23:26:21 hell kernel: [ 1191.317604] ata1.00: BMDMA stat 0x64
Aug 31 23:26:21 hell kernel: [ 1191.317646] ata1.00: cmd ca/00:58:2c:e4:10/00:00:00:00:00/e0 tag 0 dma 45056 out
Aug 31 23:26:21 hell kernel: [ 1191.317658]          res 51/84:01:83:e4:10/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 31 23:26:21 hell kernel: [ 1191.317682] ata1.00: status: { DRDY ERR }
Aug 31 23:26:21 hell kernel: [ 1191.317697] ata1.00: error: { ICRC ABRT }
Aug 31 23:26:21 hell kernel: [ 1191.317798] ata1: soft resetting link
Aug 31 23:26:21 hell kernel: [ 1191.495951] ata1.00: configured for UDMA/33
Aug 31 23:26:21 hell kernel: [ 1191.503949] ata1.01: configured for UDMA/33
Aug 31 23:26:21 hell kernel: [ 1191.504015] ata1: EH complete
Aug 31 23:26:21 hell kernel: [ 1191.506699] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Aug 31 23:26:21 hell kernel: [ 1191.506731] ata1.00: BMDMA stat 0x64
Aug 31 23:26:21 hell kernel: [ 1191.506772] ata1.00: cmd ca/00:58:2c:e4:10/00:00:00:00:00/e0 tag 0 dma 45056 out
Aug 31 23:26:21 hell kernel: [ 1191.506784]          res 51/84:01:83:e4:10/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 31 23:26:21 hell kernel: [ 1191.506807] ata1.00: status: { DRDY ERR }
Aug 31 23:26:21 hell kernel: [ 1191.506822] ata1.00: error: { ICRC ABRT }
Aug 31 23:26:21 hell kernel: [ 1191.506916] ata1: soft resetting link
Aug 31 23:26:22 hell kernel: [ 1191.683899] ata1.00: configured for UDMA/33
Aug 31 23:26:22 hell kernel: [ 1191.691924] ata1.01: configured for UDMA/33
Aug 31 23:26:22 hell kernel: [ 1191.691989] ata1: EH complete
Aug 31 23:26:22 hell kernel: [ 1191.694644] ata1.00: limiting speed to UDMA/25:PIO4
Aug 31 23:26:22 hell kernel: [ 1191.694678] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Aug 31 23:26:22 hell kernel: [ 1191.694699] ata1.00: BMDMA stat 0x64
Aug 31 23:26:22 hell kernel: [ 1191.694738] ata1.00: cmd ca/00:58:2c:e4:10/00:00:00:00:00/e0 tag 0 dma 45056 out
Aug 31 23:26:22 hell kernel: [ 1191.694750]          res 51/84:01:83:e4:10/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 31 23:26:22 hell kernel: [ 1191.694773] ata1.00: status: { DRDY ERR }
Aug 31 23:26:22 hell kernel: [ 1191.694788] ata1.00: error: { ICRC ABRT }

> Sep  1 03:42:08 hell kernel: [   79.901827] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  1 03:42:08 hell kernel: [   79.901923] ata1.00: BMDMA stat 0x64
Sep  1 03:42:08 hell kernel: [   79.902015] ata1.00: cmd ca/00:10:44:ab:98/00:00:00:00:00/e0 tag 0 dma 8192 out
Sep  1 03:42:08 hell kernel: [   79.902027]          res 51/84:01:53:ab:98/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  1 03:42:08 hell kernel: [   79.902114] ata1.00: status: { DRDY ERR }
Sep  1 03:42:08 hell kernel: [   79.902180] ata1.00: error: { ICRC ABRT }
Sep  1 03:42:08 hell kernel: [   79.902329] ata1: soft resetting link
Sep  1 03:42:08 hell kernel: [   80.192150] ata1.00: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.200148] ata1.01: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.200194] ata1: EH complete
Sep  1 03:42:08 hell kernel: [   80.200824] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  1 03:42:08 hell kernel: [   80.200910] ata1.00: BMDMA stat 0x64
Sep  1 03:42:08 hell kernel: [   80.200998] ata1.00: cmd ca/00:10:44:ab:98/00:00:00:00:00/e0 tag 0 dma 8192 out
Sep  1 03:42:08 hell kernel: [   80.201010]          res 51/84:01:53:ab:98/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  1 03:42:08 hell kernel: [   80.201095] ata1.00: status: { DRDY ERR }
Sep  1 03:42:08 hell kernel: [   80.201161] ata1.00: error: { ICRC ABRT }
Sep  1 03:42:08 hell kernel: [   80.201298] ata1: soft resetting link
Sep  1 03:42:08 hell kernel: [   80.380122] ata1.00: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.388123] ata1.01: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.388160] ata1: EH complete
Sep  1 03:42:08 hell kernel: [   80.388778] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  1 03:42:08 hell kernel: [   80.388862] ata1.00: BMDMA stat 0x64
Sep  1 03:42:08 hell kernel: [   80.388951] ata1.00: cmd ca/00:10:44:ab:98/00:00:00:00:00/e0 tag 0 dma 8192 out
Sep  1 03:42:08 hell kernel: [   80.388963]          res 51/84:01:53:ab:98/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  1 03:42:08 hell kernel: [   80.389048] ata1.00: status: { DRDY ERR }
Sep  1 03:42:08 hell kernel: [   80.389114] ata1.00: error: { ICRC ABRT }
Sep  1 03:42:08 hell kernel: [   80.389251] ata1: soft resetting link
Sep  1 03:42:08 hell kernel: [   80.568089] ata1.00: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.576081] ata1.01: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.576118] ata1: EH complete
Sep  1 03:42:08 hell kernel: [   80.576735] ata1.00: limiting speed to UDMA/25:PIO4
Sep  1 03:42:08 hell kernel: [   80.576759] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  1 03:42:08 hell kernel: [   80.576840] ata1.00: BMDMA stat 0x64
Sep  1 03:42:08 hell kernel: [   80.576927] ata1.00: cmd ca/00:10:44:ab:98/00:00:00:00:00/e0 tag 0 dma 8192 out
Sep  1 03:42:08 hell kernel: [   80.576939]          res 51/84:01:53:ab:98/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  1 03:42:08 hell kernel: [   80.577024] ata1.00: status: { DRDY ERR }
Sep  1 03:42:08 hell kernel: [   80.577089] ata1.00: error: { ICRC ABRT }
Sep  1 03:42:08 hell kernel: [   80.577227] ata1: soft resetting link
Sep  1 03:42:08 hell kernel: [   80.756046] ata1.00: configured for UDMA/25
Sep  1 03:42:08 hell kernel: [   80.764022] ata1.01: configured for UDMA/33
Sep  1 03:42:08 hell kernel: [   80.764059] ata1: EH complete

> Sep  2 06:52:23 hell kernel: [   74.993306] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  2 06:52:23 hell kernel: [   74.993442] ata1.00: BMDMA stat 0x64
Sep  2 06:52:23 hell kernel: [   74.993537] ata1.00: cmd ca/00:08:94:ac:54/00:00:00:00:00/e0 tag 0 dma 4096 out
Sep  2 06:52:23 hell kernel: [   74.993549]          res 51/84:01:9b:ac:54/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  2 06:52:23 hell kernel: [   74.993636] ata1.00: status: { DRDY ERR }
Sep  2 06:52:23 hell kernel: [   74.993703] ata1.00: error: { ICRC ABRT }
Sep  2 06:52:23 hell kernel: [   74.993853] ata1: soft resetting link
Sep  2 06:52:23 hell kernel: [   75.173912] ata1.00: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.181887] ata1.01: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.181932] ata1: EH complete
Sep  2 06:52:23 hell kernel: [   75.182359] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  2 06:52:23 hell kernel: [   75.182443] ata1.00: BMDMA stat 0x64
Sep  2 06:52:23 hell kernel: [   75.182531] ata1.00: cmd ca/00:08:94:ac:54/00:00:00:00:00/e0 tag 0 dma 4096 out
Sep  2 06:52:23 hell kernel: [   75.182543]          res 51/84:01:9b:ac:54/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  2 06:52:23 hell kernel: [   75.182628] ata1.00: status: { DRDY ERR }
Sep  2 06:52:23 hell kernel: [   75.182695] ata1.00: error: { ICRC ABRT }
Sep  2 06:52:23 hell kernel: [   75.182832] ata1: soft resetting link
Sep  2 06:52:23 hell kernel: [   75.361873] ata1.00: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.369870] ata1.01: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.369907] ata1: EH complete
Sep  2 06:52:23 hell kernel: [   75.370346] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  2 06:52:23 hell kernel: [   75.370430] ata1.00: BMDMA stat 0x64
Sep  2 06:52:23 hell kernel: [   75.370518] ata1.00: cmd ca/00:08:94:ac:54/00:00:00:00:00/e0 tag 0 dma 4096 out
Sep  2 06:52:23 hell kernel: [   75.370529]          res 51/84:01:9b:ac:54/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  2 06:52:23 hell kernel: [   75.370615] ata1.00: status: { DRDY ERR }
Sep  2 06:52:23 hell kernel: [   75.370681] ata1.00: error: { ICRC ABRT }
Sep  2 06:52:23 hell kernel: [   75.370818] ata1: soft resetting link
Sep  2 06:52:23 hell kernel: [   75.549825] ata1.00: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.557826] ata1.01: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.557863] ata1: EH complete
Sep  2 06:52:23 hell kernel: [   75.558304] ata1.00: limiting speed to UDMA/25:PIO4
Sep  2 06:52:23 hell kernel: [   75.558327] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Sep  2 06:52:23 hell kernel: [   75.558408] ata1.00: BMDMA stat 0x64
Sep  2 06:52:23 hell kernel: [   75.558495] ata1.00: cmd ca/00:08:94:ac:54/00:00:00:00:00/e0 tag 0 dma 4096 out
Sep  2 06:52:23 hell kernel: [   75.558507]          res 51/84:01:9b:ac:54/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Sep  2 06:52:23 hell kernel: [   75.558591] ata1.00: status: { DRDY ERR }
Sep  2 06:52:23 hell kernel: [   75.558657] ata1.00: error: { ICRC ABRT }
Sep  2 06:52:23 hell kernel: [   75.558792] ata1: soft resetting link
Sep  2 06:52:23 hell kernel: [   75.737799] ata1.00: configured for UDMA/25
Sep  2 06:52:23 hell kernel: [   75.745796] ata1.01: configured for UDMA/33
Sep  2 06:52:23 hell kernel: [   75.745833] ata1: EH complete

The errors are visible while booting, this Text is from /var/log/kernel.log

What does this mean?

---

