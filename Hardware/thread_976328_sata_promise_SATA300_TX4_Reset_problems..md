---
title: "sata_promise SATA300 TX4 Reset problems."
date: 2008-11-09
forum: Hardware
---

### Post by giga_user_66 on 2008-11-09
Hi there,

I run a raid5 software raid and one of my arrays is based on the disks connected to my Promise SATA300 TX4 controller card.

Today it's been the second time this week and the sixth time this month that my raid5 degraded and one of the disks totally detached itself. As if it was unplugged.
Each time I had to reboot my server for my ubuntu to see it again.
What these degradations have in common is that before they happen the load is very high (around 5) and they keep happening on the same disk on my controller card.
I already replaced the cable with a brand new one and I checked the powercable too. But this was 2 failures ago. So this time it must be something else. The disk survives the rebuilding everytime too. So I have strong reason to suspect it's something with my controller card or a problem with the kernel, a bug somewhere?
On the controller card I have the following disks:

dev/sda - Device Model:     ST3500641AS
dev/sdb - Device Model:     WDC WD5000AAKS-00YGA0
dev/sdc - Device Model:     ST3500641AS
dev/sdd - Device Model:     WDC WD5000AAKS-00YGA0

All of them are 500g.
It's sdb that fails each time.
The exact logs of the system are shown at the end of my post.
After doing some googling I noticed a kernel rebuilt including a patch to set the disks at 1.5Gbps speeds makes the system stable for some people again. However since I'm a newbie Im afraid breaking things just going around and rebuilding my kernel.
I run Ubuntu 8.04, with this kernel: 2.6.24-19-generic
I really hope someone can give me some advice or tell me what to do. I'm really getting desperate.
Thank you very much in advance.
Greets


kern.log

Nov  8 19:51:31 xpc kernel: [540485.041242] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x180000 action 0xa frozen
Nov  8 19:51:31 xpc kernel: [540485.041248] ata2.00: hotplug_status 0x2
Nov  8 19:51:31 xpc kernel: [540485.041250] ata2: SError: { 10B8B Dispar }
Nov  8 19:51:31 xpc kernel: [540485.041255] ata2.00: cmd c8/00:08:cf:55:e1/00:00:00:00:00/e5 tag 0 dma 4096 in
Nov  8 19:51:31 xpc kernel: [540485.041256]          res ff/ff:ff:ff:ff:ff/00:00:00:00:00/ff Emask 0x12 (ATA bus error)
Nov  8 19:51:31 xpc kernel: [540485.041258] ata2.00: status: { Busy }
Nov  8 19:51:31 xpc kernel: [540485.041259] ata2.00: error: { ICRC UNC IDNF ABRT }
Nov  8 19:51:37 xpc kernel: [540491.106403] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:51:41 xpc kernel: [540495.077085] ata2: device not ready (errno=-16), forcing hardreset
Nov  8 19:51:41 xpc kernel: [540495.077090] ata2: hard resetting link
Nov  8 19:51:48 xpc kernel: [540501.677451] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:51:51 xpc kernel: [540505.088601] ata2: COMRESET failed (errno=-16)
Nov  8 19:51:51 xpc kernel: [540505.088605] ata2: hard resetting link
Nov  8 19:51:58 xpc kernel: [540511.674660] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:01 xpc kernel: [540515.084525] ata2: COMRESET failed (errno=-16)
Nov  8 19:52:01 xpc kernel: [540515.084531] ata2: hard resetting link
Nov  8 19:52:08 xpc kernel: [540521.670044] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:36 xpc kernel: [540550.049959] ata2: COMRESET failed (errno=-16)
Nov  8 19:52:36 xpc kernel: [540550.049966] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:52:36 xpc kernel: [540550.049968] ata2: hard resetting link
Nov  8 19:52:41 xpc kernel: [540555.065889] ata2: COMRESET failed (errno=-16)
Nov  8 19:52:41 xpc kernel: [540555.065895] ata2: reset failed, giving up
Nov  8 19:52:41 xpc kernel: [540555.065898] ata2.00: disabled
Nov  8 19:52:41 xpc kernel: [540555.065907] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4190002 action 0xa frozen t4
Nov  8 19:52:41 xpc kernel: [540555.065909] ata2: hotplug_status 0x20
Nov  8 19:52:41 xpc kernel: [540555.065911] ata2: SError: { RecovComm PHYRdyChg 10B8B Dispar DevExch }
Nov  8 19:52:41 xpc kernel: [540555.065922] ata2: hard resetting link
Nov  8 19:52:48 xpc kernel: [540561.648008] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:51 xpc kernel: [540565.059275] ata2: COMRESET failed (errno=-16)
Nov  8 19:52:51 xpc kernel: [540565.059280] ata2: hard resetting link
Nov  8 19:52:58 xpc kernel: [540571.648545] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:01 xpc kernel: [540575.060154] ata2: COMRESET failed (errno=-16)
Nov  8 19:53:01 xpc kernel: [540575.060159] ata2: hard resetting link
Nov  8 19:53:08 xpc kernel: [540581.640879] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:36 xpc kernel: [540610.057964] ata2: COMRESET failed (errno=-16)
Nov  8 19:53:36 xpc kernel: [540610.057971] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:53:36 xpc kernel: [540610.057974] ata2: hard resetting link
Nov  8 19:53:41 xpc kernel: [540615.073826] ata2: COMRESET failed (errno=-16)
Nov  8 19:53:41 xpc kernel: [540615.073832] ata2: reset failed, giving up
Nov  8 19:53:41 xpc kernel: [540615.073840] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4190002 action 0xa frozen t3
Nov  8 19:53:41 xpc kernel: [540615.073842] ata2: hotplug_status 0x20
Nov  8 19:53:41 xpc kernel: [540615.073843] ata2: SError: { RecovComm PHYRdyChg 10B8B Dispar DevExch }
Nov  8 19:53:41 xpc kernel: [540615.073853] ata2: hard resetting link
Nov  8 19:53:48 xpc kernel: [540621.655380] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:51 xpc kernel: [540625.065550] ata2: COMRESET failed (errno=-16)
Nov  8 19:53:51 xpc kernel: [540625.065555] ata2: hard resetting link
Nov  8 19:53:58 xpc kernel: [540631.654762] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:01 xpc kernel: [540635.065608] ata2: COMRESET failed (errno=-16)
Nov  8 19:54:01 xpc kernel: [540635.065613] ata2: hard resetting link
Nov  8 19:54:08 xpc kernel: [540641.648152] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:36 xpc kernel: [540670.031411] ata2: COMRESET failed (errno=-16)
Nov  8 19:54:36 xpc kernel: [540670.031418] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:54:36 xpc kernel: [540670.031420] ata2: hard resetting link
Nov  8 19:54:41 xpc kernel: [540675.055973] ata2: COMRESET failed (errno=-16)
Nov  8 19:54:41 xpc kernel: [540675.055978] ata2: reset failed, giving up
Nov  8 19:54:41 xpc kernel: [540675.055986] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4190002 action 0xa frozen t2
Nov  8 19:54:41 xpc kernel: [540675.055988] ata2: hotplug_status 0x20
Nov  8 19:54:41 xpc kernel: [540675.055990] ata2: SError: { RecovComm PHYRdyChg 10B8B Dispar DevExch }
Nov  8 19:54:41 xpc kernel: [540675.056000] ata2: hard resetting link
Nov  8 19:54:48 xpc kernel: [540681.652675] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:51 xpc kernel: [540685.064378] ata2: COMRESET failed (errno=-16)
Nov  8 19:54:51 xpc kernel: [540685.064384] ata2: hard resetting link
Nov  8 19:54:58 xpc kernel: [540691.652729] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:01 xpc kernel: [540695.072209] ata2: COMRESET failed (errno=-16)
Nov  8 19:55:01 xpc kernel: [540695.072214] ata2: hard resetting link
Nov  8 19:55:08 xpc kernel: [540701.650453] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:36 xpc kernel: [540730.029556] ata2: COMRESET failed (errno=-16)
Nov  8 19:55:36 xpc kernel: [540730.029563] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:55:36 xpc kernel: [540730.029567] ata2: hard resetting link
Nov  8 19:55:41 xpc kernel: [540735.045274] ata2: COMRESET failed (errno=-16)
Nov  8 19:55:41 xpc kernel: [540735.045280] ata2: reset failed, giving up
Nov  8 19:55:41 xpc kernel: [540735.045287] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4190002 action 0xa frozen t1
Nov  8 19:55:41 xpc kernel: [540735.045289] ata2: hotplug_status 0x20
Nov  8 19:55:41 xpc kernel: [540735.045291] ata2: SError: { RecovComm PHYRdyChg 10B8B Dispar DevExch }
Nov  8 19:55:41 xpc kernel: [540735.045301] ata2: hard resetting link
Nov  8 19:55:48 xpc kernel: [540741.626995] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:51 xpc kernel: [540745.038666] ata2: COMRESET failed (errno=-16)
Nov  8 19:55:51 xpc kernel: [540745.038674] ata2: hard resetting link
Nov  8 19:55:58 xpc kernel: [540751.628514] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:56:01 xpc kernel: [540755.037556] ata2: COMRESET failed (errno=-16)
Nov  8 19:56:01 xpc kernel: [540755.037564] ata2: hard resetting link
Nov  8 19:56:08 xpc kernel: [540761.629549] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:56:36 xpc kernel: [540790.007932] ata2: COMRESET failed (errno=-16)
Nov  8 19:56:36 xpc kernel: [540790.007938] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:56:36 xpc kernel: [540790.007940] ata2: hard resetting link
Nov  8 19:56:41 xpc kernel: [540795.028620] ata2: COMRESET failed (errno=-16)
Nov  8 19:56:41 xpc kernel: [540795.028624] ata2: reset failed, giving up
Nov  8 19:56:41 xpc kernel: [540795.028627] ata2: EH pending after 5 tries, giving up
Nov  8 19:56:41 xpc kernel: [540795.028633] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.028636] sd 1:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Nov  8 19:56:41 xpc kernel: [540795.028640] Descriptor sense data with sense descriptors (in hex):
Nov  8 19:56:41 xpc kernel: [540795.028641]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov  8 19:56:41 xpc kernel: [540795.028647]         0f ff ff ff 
Nov  8 19:56:41 xpc kernel: [540795.028650] sd 1:0:0:0: [sdb] Add. Sense: Scsi parity error
Nov  8 19:56:41 xpc kernel: [540795.028653] end_request: I/O error, dev sdb, sector 98653647
Nov  8 19:56:41 xpc kernel: [540795.028662] sd 1:0:0:0: rejecting I/O to offline device
Nov  8 19:56:41 xpc kernel: [540795.028665] sd 1:0:0:0: rejecting I/O to offline device
Nov  8 19:56:41 xpc kernel: [540795.028671] ata2: EH complete
Nov  8 19:56:41 xpc kernel: [540795.028678] ata2.00: detaching (SCSI 1:0:0:0)
Nov  8 19:56:41 xpc kernel: [540795.028828] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Nov  8 19:56:41 xpc kernel: [540795.029944] sd 1:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.029948] end_request: I/O error, dev sdb, sector 110974415
Nov  8 19:56:41 xpc kernel: [540795.029959] raid5: Disk failure on sdb1, disabling device. Operation continuing on 3 devices
Nov  8 19:56:41 xpc kernel: [540795.029981] raid5:md1: read error not correctable (sector 193025424 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029984] raid5:md1: read error not correctable (sector 213472656 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029987] raid5:md1: read error not correctable (sector 234094736 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029990] raid5:md1: read error not correctable (sector 240648336 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029993] raid5:md1: read error not correctable (sector 489947280 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029996] raid5:md1: read error not correctable (sector 489947296 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029999] raid5:md1: read error not correctable (sector 507073936 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.030031] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.030038] sd 1:0:0:0: [sdb] Stopping disk
Nov  8 19:56:41 xpc kernel: [540795.030044] sd 1:0:0:0: [sdb] START_STOP FAILED
Nov  8 19:56:41 xpc kernel: [540795.030047] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.088385] RAID5 conf printout:
Nov  8 19:56:41 xpc kernel: [540795.088391]  --- rd:4 wd:3
Nov  8 19:56:41 xpc kernel: [540795.088393]  disk 0, o:1, dev:sda1
Nov  8 19:56:41 xpc kernel: [540795.088395]  disk 1, o:0, dev:sdb1
Nov  8 19:56:41 xpc kernel: [540795.088397]  disk 2, o:1, dev:sdc1
Nov  8 19:56:41 xpc kernel: [540795.088398]  disk 3, o:1, dev:sdd1
Nov  8 19:56:41 xpc kernel: [540795.099980] RAID5 conf printout:
Nov  8 19:56:41 xpc kernel: [540795.099984]  --- rd:4 wd:3
Nov  8 19:56:41 xpc kernel: [540795.099987]  disk 0, o:1, dev:sda1
Nov  8 19:56:41 xpc kernel: [540795.099988]  disk 2, o:1, dev:sdc1
Nov  8 19:56:41 xpc kernel: [540795.099990]  disk 3, o:1, dev:sdd1

messages:

Nov  8 19:51:37 xpc kernel: [540491.106403] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:51:41 xpc kernel: [540495.077085] ata2: device not ready (errno=-16), forcing hardreset
Nov  8 19:51:41 xpc kernel: [540495.077090] ata2: hard resetting link
Nov  8 19:51:48 xpc kernel: [540501.677451] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:51:51 xpc kernel: [540505.088605] ata2: hard resetting link
Nov  8 19:51:58 xpc kernel: [540511.674660] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:01 xpc kernel: [540515.084531] ata2: hard resetting link
Nov  8 19:52:08 xpc kernel: [540521.670044] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:36 xpc kernel: [540550.049966] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:52:36 xpc kernel: [540550.049968] ata2: hard resetting link
Nov  8 19:52:41 xpc kernel: [540555.065898] ata2.00: disabled
Nov  8 19:52:41 xpc kernel: [540555.065922] ata2: hard resetting link
Nov  8 19:52:48 xpc kernel: [540561.648008] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:52:51 xpc kernel: [540565.059280] ata2: hard resetting link
Nov  8 19:52:58 xpc kernel: [540571.648545] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:01 xpc kernel: [540575.060159] ata2: hard resetting link
Nov  8 19:53:08 xpc kernel: [540581.640879] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:36 xpc kernel: [540610.057971] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:53:36 xpc kernel: [540610.057974] ata2: hard resetting link
Nov  8 19:53:41 xpc kernel: [540615.073853] ata2: hard resetting link
Nov  8 19:53:48 xpc kernel: [540621.655380] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:53:51 xpc kernel: [540625.065555] ata2: hard resetting link
Nov  8 19:53:58 xpc kernel: [540631.654762] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:01 xpc kernel: [540635.065613] ata2: hard resetting link
Nov  8 19:54:08 xpc kernel: [540641.648152] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:36 xpc kernel: [540670.031418] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:54:36 xpc kernel: [540670.031420] ata2: hard resetting link
Nov  8 19:54:41 xpc kernel: [540675.056000] ata2: hard resetting link
Nov  8 19:54:48 xpc kernel: [540681.652675] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:54:51 xpc kernel: [540685.064384] ata2: hard resetting link
Nov  8 19:54:58 xpc kernel: [540691.652729] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:01 xpc kernel: [540695.072214] ata2: hard resetting link
Nov  8 19:55:08 xpc kernel: [540701.650453] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:36 xpc kernel: [540730.029563] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:55:36 xpc kernel: [540730.029567] ata2: hard resetting link
Nov  8 19:55:41 xpc kernel: [540735.045301] ata2: hard resetting link
Nov  8 19:55:48 xpc kernel: [540741.626995] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:55:51 xpc kernel: [540745.038674] ata2: hard resetting link
Nov  8 19:55:58 xpc kernel: [540751.628514] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:56:01 xpc kernel: [540755.037564] ata2: hard resetting link
Nov  8 19:56:08 xpc kernel: [540761.629549] ata2: port is slow to respond, please be patient (Status 0xff)
Nov  8 19:56:36 xpc kernel: [540790.007938] ata2: limiting SATA link speed to 1.5 Gbps
Nov  8 19:56:36 xpc kernel: [540790.007940] ata2: hard resetting link
Nov  8 19:56:41 xpc kernel: [540795.028633] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.028636] sd 1:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Nov  8 19:56:41 xpc kernel: [540795.028641]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov  8 19:56:41 xpc kernel: [540795.028647]         0f ff ff ff 
Nov  8 19:56:41 xpc kernel: [540795.028650] sd 1:0:0:0: [sdb] Add. Sense: Scsi parity error
Nov  8 19:56:41 xpc kernel: [540795.028671] ata2: EH complete
Nov  8 19:56:41 xpc kernel: [540795.028678] ata2.00: detaching (SCSI 1:0:0:0)
Nov  8 19:56:41 xpc kernel: [540795.028828] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Nov  8 19:56:41 xpc kernel: [540795.029944] sd 1:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.029981] raid5:md1: read error not correctable (sector 193025424 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029984] raid5:md1: read error not correctable (sector 213472656 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029987] raid5:md1: read error not correctable (sector 234094736 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029990] raid5:md1: read error not correctable (sector 240648336 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029993] raid5:md1: read error not correctable (sector 489947280 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029996] raid5:md1: read error not correctable (sector 489947296 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.029999] raid5:md1: read error not correctable (sector 507073936 on sdb1).
Nov  8 19:56:41 xpc kernel: [540795.030031] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov  8 19:56:41 xpc kernel: [540795.030038] sd 1:0:0:0: [sdb] Stopping disk
Nov  8 19:56:41 xpc kernel: [540795.030044] sd 1:0:0:0: [sdb] START_STOP FAILED
Nov  8 19:56:41 xpc kernel: [540795.030047] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

---

### Post by giga_user_66 on 2008-11-09
Anyone?

---

### Post by big_rapoza on 2008-11-19
I am having the exact same issue with the Promise SATA 300 TX4. Mine is running on a Dell Precision Workstation with 2 P3 CPUs and 4 WD10EACS drives running Ubuntu Server 8.04LTS. In my case, the errors have always occurred on the first drive and only after an intense file transfer, such as rsync of a 53 gig file. The controller would reset, fail and the drive would be completely inaccessible. With a reboot, the drive would be fully visible and work until is was stressed again. It also only seemed to happpen to a file on the first part of the drive. Have you tried running a manufacturer's diagnostic on the drive itself? 

I will try and post kernel logs tomorrow.

---

### Post by ryan8613 on 2008-11-24
Hello,

I'm having the exact same problem, but with Ubuntu's parent OS Debian. Same card, same error messages, same pattern.

Which kernel version are you both running? (uname -a)

Thanks!

Ryan Ticer

---

### Post by ryan8613 on 2008-11-25
I tried a fresh install of Ubuntu 8.10 x64 and am having the exact same problem. 

Anyone?

---

### Post by big_rapoza on 2008-11-26
I am running ubuntu 2.6.24-21-server.

Also as I promised, here are the kernel logs that occurred during the failure. I shortened them to only include entries related to the promise controller and the drive errors.

---

### Post by ryan8613 on 2008-11-26
Try upgrading your power supply. I did that today and haven't had the problem since.

If your drives don't have enough power, they have no way of telling you besides just not working right.

Give it a shot, if it works, spread the word.

Thanks!

Ryan Ticer

---

### Post by rknall on 2009-01-07
Hi

Having the exact same issue, could anyone else confirm, that upgrading the power supply solved this for them? BTW, the drive that mainly failed the first few times had really an error in the end, so I am not sure, if it is only the drive. Also I am using also WDC WD5000AAKS drives, 5 of them to be exact, for a RAID 6.

Before failing, and subsequently resulting in a looot of scsi and reading errors, my system also prints out an IRQ error:


```
irq 50: nobody cared (try booting with the "irqpoll" option)

Call Trace:
 <IRQ> [<ffffffff802a4237>] __report_bad_irq+0x30/0x7d
 [<ffffffff802a4471>] note_interrupt+0x1ed/0x22e
 [<ffffffff802a3970>] __do_IRQ+0xc7/0x105
 [<ffffffff80210371>] __do_softirq+0x5e/0xd5
 [<ffffffff80263749>] do_IRQ+0x65/0x73
 [<ffffffff80258111>] ret_from_intr+0x0/0xa
 <EOI> [<ffffffff882d88ac>] :vmmon:Task_Switch+0x68f/0x1103
 [<ffffffff882daf0a>] :vmmon:Vmx86_RunVM+0x3f/0x1eb
 [<ffffffff882d3bda>] :vmmon:LinuxDriver_Ioctl+0x270/0xb7d
 [<ffffffff8027c8e1>] default_wake_function+0x0/0xe
 [<ffffffff88023d2e>] :e1000:e1000_xmit_frame+0xa21/0xa5b
 [<ffffffff8027b74b>] task_rq_lock+0x3d/0x6f
 [<ffffffff8027b74b>] task_rq_lock+0x3d/0x6f
 [<ffffffff8027b491>] __activate_task+0x27/0x39
 [<ffffffff80242f87>] try_to_wake_up+0x3d5/0x3e6
 [<ffffffff8020d5c3>] current_fs_time+0x3b/0x40
 [<ffffffff8022c2e4>] __wake_up+0x38/0x4f
 [<ffffffff80255e14>] group_send_sig_info+0x18/0x75
 [<ffffffff80288ed1>] kill_proc_info+0x48/0x60
 [<ffffffff8023e041>] do_ioctl+0x55/0x6b
 [<ffffffff8022e022>] vfs_ioctl+0x252/0x26b
 [<ffffffff80248162>] sys_ioctl+0x59/0x78
 [<ffffffff80257c16>] system_call+0x7e/0x83

handlers:
[<ffffffff880b7137>] (pdc_interrupt+0x0/0x1e4 [sata_promise])

```

Maybe this helps someone? Any help is appreciated.

regards, Roland

---

### Post by Pieter1974 on 2009-01-09
This problem seems to be fixed with updating to 

linux-image-2.6.24-23

It's rolled out now on all our servers and the problem seems to be disappeared

Just use apt-get dist-upgrade.

---

