---
title: "[SOLVED] Hard Drives keep locking up"
date: 2008-08-21
forum: General Help
---

### Post by rockerboo on 2008-08-21
Hi,

This is slightly unrelated to Ubuntu, but maybe someone here can give me a hand. I am currently seeing that my hard drive keeps failing or something, and I can hear the drive spinning down. And then maybe 5-10 seconds later it comes back. This is the output from /var/log/kern.log that surrounds the time when the drive fails and comes back.

```
Aug 21 18:17:43 Belefonte kernel: [10954.394050] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xa frozen
Aug 21 18:17:52 Belefonte kernel: [10954.394055] ata3: SError: { PHYRdyChg CommWake Dispar LinkSeq TrStaTrns }
Aug 21 18:17:52 Belefonte kernel: [10954.394059] ata3.00: cmd c8/00:08:c4:81:54/00:00:00:00:00/e1 tag 0 dma 4096 in
Aug 21 18:17:52 Belefonte kernel: [10954.394060]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Aug 21 18:17:52 Belefonte kernel: [10954.394063] ata3.00: status: { DRDY }
Aug 21 18:17:52 Belefonte kernel: [10954.394067] ata3: hard resetting link
Aug 21 18:17:52 Belefonte kernel: [10954.688053] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 18:17:52 Belefonte kernel: [10955.556710] ata3.00: revalidation failed (errno=-2)
Aug 21 18:17:52 Belefonte kernel: [10955.556715] ata3: failed to recover some devices, retrying in 5 secs
Aug 21 18:17:52 Belefonte kernel: [10957.220877] ata3: hard resetting link
Aug 21 18:17:52 Belefonte kernel: [10957.380854] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 18:17:52 Belefonte kernel: [10957.392534] ata3.00: configured for UDMA/133
Aug 21 18:17:52 Belefonte kernel: [10957.392549] ata3: EH complete
Aug 21 18:17:52 Belefonte kernel: [10957.407317] sd 2:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
Aug 21 18:17:52 Belefonte kernel: [10957.407396] sd 2:0:0:0: [sdc] Write Protect is off
Aug 21 18:17:52 Belefonte kernel: [10957.407398] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Aug 21 18:17:52 Belefonte kernel: [10957.410108] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

It looks like I should look into ```
Aug 21 18:17:43 Belefonte kernel: [10954.394050] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x1950000 action 0xa frozen
``` but I am not sure what that error means exactly. This has been happening a lot, and I do not know the cause, or solution..

Thanks

---

### Post by rockerboo on 2008-08-22
Bump, please

---

### Post by az on 2008-08-22
You have a hardware problem.  Try to back up any important dat afrom that drive ASAP.  If you can't read the drive, try using gddrescue

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

You can also use S.M.A.R.T to asses your drive's health:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by Shazaam on 2008-08-22
If you know the manufacturer (Western Digital, Maxtor, Hitachi, etc) of the drives you can go to their website(s) and download drive diagnostics software. They are usually put on a floppy (hope you have one). Some have images you can burn to cd.

---

### Post by rockerboo on 2008-08-28
Ah, thanks for confirming. Does this look like a motherboard issue, or a drive issue? Seems to happen on random drives, though I have moved some of the drives around. And the after a while it seems to work out fine.

To me it seems like the motherboard is at fault. All the data is backed up at the moment. In a side remark, does anyone suggest a good backup program?

Thanks for the help in clarifying.

---

### Post by rockerboo on 2008-08-30
```
Aug 30 15:10:05 Belefonte kernel: [  715.894040]          res 51/40:00:0b:14:7c/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:05 Belefonte kernel: [  715.902726] ata2.00: configured for UDMA/133

Aug 30 15:10:05 Belefonte kernel: [  715.902737] ata2: EH complete

Aug 30 15:10:08 Belefonte kernel: [  716.935002]          res 51/40:00:0b:14:7c/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:08 Belefonte kernel: [  716.939858] ata2.00: configured for UDMA/133

Aug 30 15:10:08 Belefonte kernel: [  716.939868] ata2: EH complete

Aug 30 15:10:11 Belefonte kernel: [  718.025721]          res 51/40:00:0b:14:7c/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:11 Belefonte kernel: [  718.033230] ata2.00: configured for UDMA/133

Aug 30 15:10:11 Belefonte kernel: [  718.033241] ata2: EH complete

Aug 30 15:10:14 Belefonte kernel: [  719.017884]          res 51/40:00:0b:14:7c/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:14 Belefonte kernel: [  719.022749] ata2.00: configured for UDMA/133

Aug 30 15:10:14 Belefonte kernel: [  719.022759] ata2: EH complete

Aug 30 15:10:18 Belefonte kernel: [  720.111271]          res 51/40:00:0b:14:7c/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:18 Belefonte kernel: [  720.116448] ata2.00: configured for UDMA/133

Aug 30 15:10:18 Belefonte kernel: [  720.116458] ata2: EH complete

Aug 30 15:10:19 Belefonte kernel: [  720.639112] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:10:19 Belefonte kernel: [  720.639195] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:10:19 Belefonte kernel: [  720.639302] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 30 15:10:19 Belefonte kernel: [  720.639429] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:10:19 Belefonte kernel: [  720.639497] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:10:19 Belefonte kernel: [  720.639634] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 30 15:10:34 Belefonte kernel: [  733.635053]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:34 Belefonte kernel: [  733.643268] ata2.00: configured for UDMA/133

Aug 30 15:10:34 Belefonte kernel: [  733.643278] ata2: EH complete

Aug 30 15:10:37 Belefonte kernel: [  734.627225]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:37 Belefonte kernel: [  734.635755] ata2.00: configured for UDMA/133

Aug 30 15:10:37 Belefonte kernel: [  734.635763] ata2: EH complete

Aug 30 15:10:40 Belefonte kernel: [  735.670668]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:41 Belefonte kernel: [  735.675867] ata2.00: configured for UDMA/133

Aug 30 15:10:41 Belefonte kernel: [  735.675873] ata2: EH complete

Aug 30 15:10:44 Belefonte kernel: [  736.710110]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:44 Belefonte kernel: [  736.714643] ata2.00: configured for UDMA/133

Aug 30 15:10:44 Belefonte kernel: [  736.714651] ata2: EH complete

Aug 30 15:10:47 Belefonte kernel: [  737.746559]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:47 Belefonte kernel: [  737.752092] ata2.00: configured for UDMA/133

Aug 30 15:10:47 Belefonte kernel: [  737.752098] ata2: EH complete

Aug 30 15:10:50 Belefonte kernel: [  738.734733]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:50 Belefonte kernel: [  738.739616] ata2.00: configured for UDMA/133

Aug 30 15:10:50 Belefonte kernel: [  738.739630] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:10:50 Belefonte kernel: [  738.739633] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:10:50 Belefonte kernel: [  738.739637] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:10:50 Belefonte kernel: [  738.739639]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:10:50 Belefonte kernel: [  738.739646]         00 7b c1 5c 

Aug 30 15:10:50 Belefonte kernel: [  738.739649] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:10:50 Belefonte kernel: [  738.739653] end_request: I/O error, dev sdb, sector 8110428

Aug 30 15:10:50 Belefonte kernel: [  738.739690] ata2: EH complete

Aug 30 15:10:53 Belefonte kernel: [  740.839943]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:53 Belefonte kernel: [  740.854255] ata2.00: configured for UDMA/133

Aug 30 15:10:53 Belefonte kernel: [  740.854264] ata2: EH complete

Aug 30 15:10:56 Belefonte kernel: [  742.621056]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:56 Belefonte kernel: [  742.631764] ata2.00: configured for UDMA/133

Aug 30 15:10:56 Belefonte kernel: [  742.631772] ata2: EH complete

Aug 30 15:10:59 Belefonte kernel: [  743.713934]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:10:59 Belefonte kernel: [  743.720883] ata2.00: configured for UDMA/133

Aug 30 15:10:59 Belefonte kernel: [  743.720891] ata2: EH complete

Aug 30 15:11:02 Belefonte kernel: [  745.496726]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:02 Belefonte kernel: [  745.520571] ata2.00: configured for UDMA/133

Aug 30 15:11:02 Belefonte kernel: [  745.520581] ata2: EH complete

Aug 30 15:11:05 Belefonte kernel: [  747.262600]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:05 Belefonte kernel: [  747.267212] ata2.00: configured for UDMA/133

Aug 30 15:11:05 Belefonte kernel: [  747.267219] ata2: EH complete

Aug 30 15:11:08 Belefonte kernel: [  748.249436]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:08 Belefonte kernel: [  748.254724] ata2.00: configured for UDMA/133

Aug 30 15:11:08 Belefonte kernel: [  748.254731] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:11:08 Belefonte kernel: [  748.254733] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:11:08 Belefonte kernel: [  748.254736] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:11:08 Belefonte kernel: [  748.254737]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:11:08 Belefonte kernel: [  748.254741]         00 7b c1 5c 

Aug 30 15:11:08 Belefonte kernel: [  748.254742] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:11:08 Belefonte kernel: [  748.254746] end_request: I/O error, dev sdb, sector 8110428

Aug 30 15:11:08 Belefonte kernel: [  748.254747] printk: 8 messages suppressed.

Aug 30 15:11:08 Belefonte kernel: [  748.254759] ata2: EH complete

Aug 30 15:11:08 Belefonte kernel: [  748.254625] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:11:11 Belefonte kernel: [  749.238940]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:11 Belefonte kernel: [  749.244560] ata2.00: configured for UDMA/133

Aug 30 15:11:11 Belefonte kernel: [  749.244567] ata2: EH complete

Aug 30 15:11:14 Belefonte kernel: [  750.275387]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:14 Belefonte kernel: [  750.280675] ata2.00: configured for UDMA/133

Aug 30 15:11:14 Belefonte kernel: [  750.280682] ata2: EH complete

Aug 30 15:11:17 Belefonte kernel: [  751.319161]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:17 Belefonte kernel: [  751.323776] ata2.00: configured for UDMA/133

Aug 30 15:11:17 Belefonte kernel: [  751.323784] ata2: EH complete

Aug 30 15:11:21 Belefonte kernel: [  752.465149]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:21 Belefonte kernel: [  752.472762] ata2.00: configured for UDMA/133

Aug 30 15:11:21 Belefonte kernel: [  752.472769] ata2: EH complete

Aug 30 15:11:24 Belefonte kernel: [  753.454648]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:24 Belefonte kernel: [  753.457605] ata2.00: configured for UDMA/133

Aug 30 15:11:24 Belefonte kernel: [  753.457612] ata2: EH complete

Aug 30 15:11:27 Belefonte kernel: [  754.438499]          res 51/40:00:5c:c1:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:27 Belefonte kernel: [  754.444445] ata2.00: configured for UDMA/133

Aug 30 15:11:27 Belefonte kernel: [  754.444453] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:11:27 Belefonte kernel: [  754.444455] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:11:27 Belefonte kernel: [  754.444457] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:11:27 Belefonte kernel: [  754.444459]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:11:27 Belefonte kernel: [  754.444462]         00 7b c1 5c 

Aug 30 15:11:27 Belefonte kernel: [  754.444463] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:11:27 Belefonte kernel: [  754.444467] end_request: I/O error, dev sdb, sector 8110428

Aug 30 15:11:27 Belefonte kernel: [  754.444477] ata2: EH complete

Aug 30 15:11:27 Belefonte kernel: [  754.444363] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:11:27 Belefonte kernel: [  754.444480] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 30 15:11:27 Belefonte kernel: [  754.444601] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:11:27 Belefonte kernel: [  754.444660] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:11:27 Belefonte kernel: [  754.447098] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 30 15:11:30 Belefonte kernel: [  756.602686]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:30 Belefonte kernel: [  756.623521] ata2.00: configured for UDMA/133

Aug 30 15:11:30 Belefonte kernel: [  756.623529] ata2: EH complete

Aug 30 15:11:31 Belefonte kernel: [  757.103883] UDF-fs: No VRS found

Aug 30 15:11:33 Belefonte kernel: [  758.827428]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:33 Belefonte kernel: [  758.849864] ata2.00: configured for UDMA/133

Aug 30 15:11:33 Belefonte kernel: [  758.849874] ata2: EH complete

Aug 30 15:11:36 Belefonte kernel: [  760.327860]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:36 Belefonte kernel: [  760.352727] ata2.00: configured for UDMA/133

Aug 30 15:11:36 Belefonte kernel: [  760.352735] ata2: EH complete

Aug 30 15:11:40 Belefonte kernel: [  761.838356]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:40 Belefonte kernel: [  761.843695] ata2.00: configured for UDMA/133

Aug 30 15:11:40 Belefonte kernel: [  761.843704] ata2: EH complete

Aug 30 15:11:43 Belefonte kernel: [  762.876465]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:43 Belefonte kernel: [  762.900053] ata2.00: configured for UDMA/133

Aug 30 15:11:43 Belefonte kernel: [  762.900063] ata2: EH complete

Aug 30 15:11:46 Belefonte kernel: [  764.951827]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:46 Belefonte kernel: [  764.973151] ata2.00: configured for UDMA/133

Aug 30 15:11:46 Belefonte kernel: [  764.973166] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:11:46 Belefonte kernel: [  764.973170] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:11:46 Belefonte kernel: [  764.973174] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:11:46 Belefonte kernel: [  764.973176]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:11:46 Belefonte kernel: [  764.973184]         00 7b c8 cf 

Aug 30 15:11:46 Belefonte kernel: [  764.973187] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:11:46 Belefonte kernel: [  764.973191] end_request: I/O error, dev sdb, sector 8112335

Aug 30 15:11:46 Belefonte kernel: [  764.973206] ata2: EH complete

Aug 30 15:11:49 Belefonte kernel: [  767.231940]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:49 Belefonte kernel: [  767.245032] ata2.00: configured for UDMA/133

Aug 30 15:11:49 Belefonte kernel: [  767.245040] ata2: EH complete

Aug 30 15:11:52 Belefonte kernel: [  769.657075]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:52 Belefonte kernel: [  769.664347] ata2.00: configured for UDMA/133

Aug 30 15:11:52 Belefonte kernel: [  769.664355] ata2: EH complete

Aug 30 15:11:55 Belefonte kernel: [  770.651905]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:55 Belefonte kernel: [  770.659179] ata2.00: configured for UDMA/133

Aug 30 15:11:55 Belefonte kernel: [  770.659188] ata2: EH complete

Aug 30 15:11:58 Belefonte kernel: [  771.691358]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:11:58 Belefonte kernel: [  771.697291] ata2.00: configured for UDMA/133

Aug 30 15:11:58 Belefonte kernel: [  771.697299] ata2: EH complete

Aug 30 15:12:02 Belefonte kernel: [  772.779404]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:02 Belefonte kernel: [  772.786689] ata2.00: configured for UDMA/133

Aug 30 15:12:02 Belefonte kernel: [  772.786697] ata2: EH complete

Aug 30 15:12:05 Belefonte kernel: [  774.169210]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:05 Belefonte kernel: [  774.193060] ata2.00: configured for UDMA/133

Aug 30 15:12:05 Belefonte kernel: [  774.193072] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:12:05 Belefonte kernel: [  774.193076] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:12:05 Belefonte kernel: [  774.193081] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:12:05 Belefonte kernel: [  774.193083]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:12:05 Belefonte kernel: [  774.193091]         00 7b c8 cf 

Aug 30 15:12:05 Belefonte kernel: [  774.193094] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:12:05 Belefonte kernel: [  774.193098] end_request: I/O error, dev sdb, sector 8112335

Aug 30 15:12:05 Belefonte kernel: [  774.193113] ata2: EH complete

Aug 30 15:12:05 Belefonte kernel: [  774.193317] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:12:05 Belefonte kernel: [  774.209438] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:12:08 Belefonte kernel: [  777.422821]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:08 Belefonte kernel: [  777.430427] ata2.00: configured for UDMA/133

Aug 30 15:12:08 Belefonte kernel: [  777.430435] ata2: EH complete

Aug 30 15:12:11 Belefonte kernel: [  778.413653]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:11 Belefonte kernel: [  778.418929] ata2.00: configured for UDMA/133

Aug 30 15:12:11 Belefonte kernel: [  778.418935] ata2: EH complete

Aug 30 15:12:14 Belefonte kernel: [  779.459756]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:14 Belefonte kernel: [  779.464717] ata2.00: configured for UDMA/133

Aug 30 15:12:14 Belefonte kernel: [  779.464727] ata2: EH complete

Aug 30 15:12:17 Belefonte kernel: [  780.498206]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:17 Belefonte kernel: [  780.506490] ata2.00: configured for UDMA/133

Aug 30 15:12:17 Belefonte kernel: [  780.506497] ata2: EH complete

Aug 30 15:12:20 Belefonte kernel: [  781.487373]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:20 Belefonte kernel: [  781.494651] ata2.00: configured for UDMA/133

Aug 30 15:12:20 Belefonte kernel: [  781.494658] ata2: EH complete

Aug 30 15:12:23 Belefonte kernel: [  784.201702]          res 51/40:00:cf:c8:7b/00:00:00:00:00/e0 Emask 0x9 (media error)

Aug 30 15:12:23 Belefonte kernel: [  784.204467] ata2.00: configured for UDMA/133

Aug 30 15:12:23 Belefonte kernel: [  784.204475] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

Aug 30 15:12:23 Belefonte kernel: [  784.204477] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]

Aug 30 15:12:23 Belefonte kernel: [  784.204479] Descriptor sense data with sense descriptors (in hex):

Aug 30 15:12:23 Belefonte kernel: [  784.204481]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 

Aug 30 15:12:23 Belefonte kernel: [  784.204484]         00 7b c8 cf 

Aug 30 15:12:23 Belefonte kernel: [  784.204486] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed

Aug 30 15:12:23 Belefonte kernel: [  784.204489] end_request: I/O error, dev sdb, sector 8112335

Aug 30 15:12:23 Belefonte kernel: [  784.204502] ata2: EH complete

Aug 30 15:12:23 Belefonte kernel: [  784.207548] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 30 15:12:23 Belefonte kernel: [  784.207634] sd 1:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)

Aug 30 15:12:23 Belefonte kernel: [  784.207645] sd 1:0:0:0: [sdb] Write Protect is off

Aug 30 15:12:23 Belefonte kernel: [  784.207716] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Some more errors that caused me to not be able to access a NTFS drive

---

