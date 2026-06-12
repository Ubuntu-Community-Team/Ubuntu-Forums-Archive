---
title: "help, booting trouble!!!"
date: 2008-07-21
forum: General Help
---

### Post by laevatain on 2008-07-21
guys, do you know what is this? hard disk error?
-------------------------------------------------
[17179xxx.xxx000]Buffer I/O error on device dm-1, logical block 1573319
[17179xxx.xxx000]ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17179xxx.xxx000]ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17179xxx.xxx000]ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17179xxx.xxx000]ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17179xxx.xxx000]ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
......
------------------------------------------
the normal driver loading process are interupted by these repeating lines.
xxx.xxx are numbers, and 1573319 in the first line will add 1 next time.
------------------------
ubuntu 6.06

---

### Post by Polygon on 2008-07-21
if ubuntu boots fine, then its most likely something you can ignore.

---

### Post by laevatain on 2008-07-22
thanks for reply
it can boot after these lines. 
Acturely it happens when "staring enterprise volume management system...".
then it acted normally.
So i checked the /var/log/syslog, found something like:
-------------------------------------------------------------
...: [17179596.300000] ata1: status=0x51 { DriveReady SeekComplete Error }
...: [17179596.300000] ata1: error=0x40 { UncorrectableError }
...: [17179600.680000] ata1: status=0x51 { DriveReady SeekComplete Error }
...: [17179600.680000] ata1: error=0x40 { UncorrectableError }
...: [17179605.072000] ata1: status=0x51 { DriveReady SeekComplete Error }
...: [17179605.072000] ata1: error=0x40 { UncorrectableError }
...: [17179609.452000] ata1: status=0x51 { DriveReady SeekComplete Error }
...: [17179609.452000] ata1: error=0x40 { UncorrectableError }
...: [17179613.844000] ata1: status=0x51 { DriveReady SeekComplete Error }
...: [17179613.844000] ata1: error=0x40 { UncorrectableError }
...: [17179613.844000] sd 0:0:0:0: SCSI error: return code = 0x8000002
...: [17179613.844000] sda: Current: sense key: Medium Error
...: [17179613.844000]     Additional sense: Unrecovered read error - auto reallocate failed
...: [17179613.844000] end_request: I/O error, dev sda, sector 26776190
------------------------------------------------------

i googled these lines, respectively. 
Someone has similar problem, and some guys believes that the hard disk is broken.
but when i used the command:
   sudo smartctl --health --attributes --device=ata /dev/sda7
i got:
-----------------
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1980
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       21644368071
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       9018
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1531
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       1066
189 Unknown_Attribute       0x003a   044   044   000    Old_age   Always       -       56
190 Unknown_Attribute       0x0022   045   039   045    Old_age   Always   FAILING_NOW 959119415
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       272
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       295683
194 Temperature_Celsius     0x0022   055   061   000    Old_age   Always       -       55
195 Hardware_ECC_Recovered  0x001a   063   052   000    Old_age   Always       -       138638795
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       6
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

----------------------------------------------
it was a PASSED.
Now i'm confused.
anybody knows what the problem is? and segestions on fix it?

---

### Post by laevatain on 2008-07-22
any ideas?
thanks

---

