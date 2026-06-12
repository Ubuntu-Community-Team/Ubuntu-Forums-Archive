---
title: "Hard Disk Errors (Not Ubuntu specific)"
date: 2008-10-04
forum: Hardware
---

### Post by sofamensch on 2008-10-04
Lately my PC acted strange, Vista just hang up at some point, CHKDSK gave some error, i thought its just the usual Windows stuff... but during Boot even Ubuntu encountered some problem. Here some output of dmesg:

>  bus error)
[   67.319841] ata4.00: status: { DRDY ERR }
[   67.319881] ata4.00: error: { ICRC ABRT }
[   67.319926] ata4: soft resetting link
[   67.496175] ata4.00: configured for UDMA/33
[   67.496181] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   67.496184] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   67.496188] Descriptor sense data with sense descriptors (in hex):
[   67.496190]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   67.496200]         03 c4 d1 ad 
[   67.496204] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[   67.496209] end_request: I/O error, dev sda, sector 63230374
[   67.496252] Buffer I/O error on device sda2, logical block 196613
[   67.496294] lost page write due to I/O error on sda2
[   67.496305] ata4: EH complete
[   67.496369] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   67.499831] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   67.499875] ata4.00: BMDMA stat 0x26
[   67.499917] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   67.499918]          res 51/84:28:1e:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   67.500025] ata4.00: status: { DRDY ERR }
[   67.500065] ata4.00: error: { ICRC ABRT }
[   67.500110] ata4: soft resetting link
[   67.676174] ata4.00: configured for UDMA/33
[   67.676180] ata4: EH complete
[   67.680023] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   67.680068] ata4.00: BMDMA stat 0x26
[   67.680110] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   67.680112]          res 51/84:28:1e:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   67.680213] ata4.00: status: { DRDY ERR }
[   67.680253] ata4.00: error: { ICRC ABRT }
[   67.680298] ata4: soft resetting link
[   67.860673] ata4.00: configured for UDMA/33
[   67.860679] ata4: EH complete
[   67.864197] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   67.864241] ata4.00: BMDMA stat 0x26
[   67.864283] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   67.864284]          res 51/84:28:1e:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   67.864385] ata4.00: status: { DRDY ERR }
[   67.864425] ata4.00: error: { ICRC ABRT }
[   67.864469] ata4: soft resetting link
[   68.044175] ata4.00: configured for UDMA/33
[   68.044180] ata4: EH complete
[   68.047379] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.047423] ata4.00: BMDMA stat 0x26
[   68.047465] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   68.047466]          res 51/84:29:1d:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   68.047567] ata4.00: status: { DRDY ERR }
[   68.047608] ata4.00: error: { ICRC ABRT }
[   68.047652] ata4: soft resetting link
[   68.224174] ata4.00: configured for UDMA/33
[   68.224180] ata4: EH complete
[   68.227560] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.227604] ata4.00: BMDMA stat 0x26
[   68.227646] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   68.227647]          res 51/84:28:1e:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   68.227748] ata4.00: status: { DRDY ERR }
[   68.227788] ata4.00: error: { ICRC ABRT }
[   68.227832] ata4: soft resetting link
[   68.404176] ata4.00: configured for UDMA/33
[   68.404182] ata4: EH complete
[   68.407741] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.407786] ata4.00: BMDMA stat 0x26
[   68.407828] ata4.00: cmd ca/00:38:0e:ca:cf/00:00:00:00:00/e3 tag 0 dma 28672 out
[   68.407829]          res 51/84:28:1e:ca:cf/00:00:00:00:00/e3 Emask 0x30 (host bus error)
[   68.407930] ata4.00: status: { DRDY ERR }
[   68.407971] ata4.00: error: { ICRC ABRT }
[   68.408016] ata4: soft resetting link
[   68.588674] ata4.00: configured for UDMA/33
[   68.588680] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   68.588683] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   68.588687] Descriptor sense data with sense descriptors (in hex):
[   68.588690]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   68.588699]         03 cf ca 1e 
[   68.588703] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[   68.588707] end_request: I/O error, dev sda, sector 63949326
[   68.588750] Buffer I/O error on device sda2, logical block 286482
[   68.588793] lost page write due to I/O error on sda2
[   68.588796] Buffer I/O error on device sda2, logical block 286483
[   68.588838] lost page write due to I/O error on sda2
[   68.588841] Buffer I/O error on device sda2, logical block 286484
[   68.588883] lost page write due to I/O error on sda2
[   68.588887] Buffer I/O error on device sda2, logical block 286485
[   68.588930] lost page write due to I/O error on sda2
[   68.588933] Buffer I/O error on device sda2, logical block 286486
[   68.588975] lost page write due to I/O error on sda2
[   68.588978] Buffer I/O error on device sda2, logical block 286487
[   68.589021] lost page write due to I/O error on sda2
[   68.589028] ata4: EH complete
[   68.589090] sd 3:0:0:0: [sda] Write Protect is off
[   68.589093] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   68.595923] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.595967] ata4.00: BMDMA stat 0x26
[   68.596010] ata4.00: cmd ca/00:08:ca:72:25/00:00:00:00:00/e6 tag 0 dma 4096 out
[   68.596011]          res 51/84:00:d2:72:25/00:00:00:00:00/e6 Emask 0x30 (host bus error)
[   68.596112] ata4.00: status: { DRDY ERR }
[   68.596153] ata4.00: error: { ICRC ABRT }
[   68.596197] ata4: soft resetting link
[   68.776175] ata4.00: configured for UDMA/33
[   68.776181] ata4: EH complete
[   68.788117] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.788161] ata4.00: BMDMA stat 0x26
[   68.788203] ata4.00: cmd ca/00:08:ca:72:25/00:00:00:00:00/e6 tag 0 dma 4096 out
[   68.788204]          res 51/84:01:d1:72:25/00:00:00:00:00/e6 Emask 0x30 (host bus error)
[   68.788309] ata4.00: status: { DRDY ERR }
[   68.788349] ata4.00: error: { ICRC ABRT }
[   68.788394] ata4: soft resetting link
[   68.968175] ata4.00: configured for UDMA/33
[   68.968180] ata4: EH complete
[   68.971304] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   68.971349] ata4.00: BMDMA stat 0x26
[   68.971391] ata4.00: cmd ca/00:08:ca:72:25/00:00:00:00:00/e6 tag 0 dma 4096 out
[   68.971392]          res 51/84:01:d1:72:25/00:00:00:00:00/e6 Emask 0x30 (host bus error)
[   68.971493] ata4.00: status: { DRDY ERR }
[   68.971533] ata4.00: error: { ICRC ABRT }
[   68.971577] ata4: soft resetting link
[   69.148175] ata4.00: configured for UDMA/33
[   69.148180] ata4: EH complete
[   69.151484] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   69.151529] ata4.00: BMDMA stat 0x26
[   69.151571] ata4.00: cmd ca/00:08:ca:72:25/00:00:00:00:00/e6 tag 0 dma 4096 out
[   69.151572]          res 51/84:01:d1:72:25/00:00:00:00:00/e6 Emask 0x30 (host bus error)
[   69.151673] ata4.00: status: { DRDY ERR }
[   69.151714] ata4.00: error: { ICRC ABRT }
[   69.151759] ata4: soft resetting link
[   69.328178] ata4.00: configured for UDMA/33
[   69.328184] ata4: EH complete


Looks like some Hard Disk Fault. But the Hard DISK's SMART tells me that everything is ok (Western Digital 500AACS). I not know how to interpret this.

Thanks in advance. Alex

---

### Post by iponeverything on 2008-10-04
humm..

You might have a bad cable, bent pin or messed up drive.

My money is on the later.

---

### Post by bigken on 2008-10-04
looks to me like you have some bad sectors on the hdd western digital have some tools on there site for testing their drives (windows based)

---

