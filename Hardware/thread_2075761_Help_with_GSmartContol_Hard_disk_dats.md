---
title: "Help with GSmartContol Hard disk dats"
date: 2012-10-24
forum: Hardware
---

### Post by abduljones on 2012-10-24
Laptop HP Compaq 6720s of unknown provenance and given to me without a hard drive in it. Bought a 160gb sata hard drive in Feb this year (so still under warranty) Started getting problems with the laptop- hanging at boot up, reporting errors at boot up, the wireless disappearing, opening screen not usable until 5-10 mins after log on. Thought it was the motherboard going, but ran some tests on the hard drive, just in case,and now I'm not sure. Here is latest read out from running GSmartContrl

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-32-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Black Serial ATA
Device Model:     WDC WD1600BEKT-00PVMT0
Serial Number:    WD-WX21CC1N2035
LU WWN Device Id: 5 0014ee 602045e43
Firmware Version: 01.01A01
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Oct 24 16:46:09 2012 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		( 2760) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  32) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       3797
  3 Spin_Up_Time            0x0027   162   141   021    Pre-fail  Always       -       883
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       643
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1534
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       601
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       553
193 Load_Cycle_Count        0x0032   197   197   000    Old_age   Always       -       9672
194 Temperature_Celsius     0x0022   116   099   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   199   199   000    Old_age   Always       -       37
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       33
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       8

SMART Error Log Version: 1
ATA Error Count: 285 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 285 occurred at disk power-on lifetime: 1517 hours (63 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 f3 23 00 ec  Error: UNC at LBA = 0x0c0023f3 = 201335795

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 00 00 23 00 ec 00      00:29:22.243  READ VERIFY SECTOR(S)
  40 da 00 00 22 00 ec 00      00:29:22.200  READ VERIFY SECTOR(S)
  40 da 00 00 21 00 ec 00      00:29:22.199  READ VERIFY SECTOR(S)
  40 da 00 00 20 00 ec 00      00:29:22.198  READ VERIFY SECTOR(S)
  40 da 00 00 1f 00 ec 00      00:29:22.197  READ VERIFY SECTOR(S)

Error 284 occurred at disk power-on lifetime: 1517 hours (63 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 18 e8 83 eb  Error: UNC at LBA = 0x0b83e818 = 193194008

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 00 00 e8 83 eb 00      00:28:26.784  READ VERIFY SECTOR(S)
  40 da 00 00 e7 83 eb 00      00:28:26.159  READ VERIFY SECTOR(S)
  40 da 00 00 e6 83 eb 00      00:28:25.758  READ VERIFY SECTOR(S)
  40 da 00 00 e5 83 eb 00      00:28:25.732  READ VERIFY SECTOR(S)
  40 da 00 00 e4 83 eb 00      00:28:25.731  READ VERIFY SECTOR(S)

Error 283 occurred at disk power-on lifetime: 1517 hours (63 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1e 3a 81 eb  Error: UNC at LBA = 0x0b813a1e = 193018398

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 00 00 3a 81 eb 00      00:28:14.988  READ VERIFY SECTOR(S)
  40 da 00 00 39 81 eb 00      00:28:14.978  READ VERIFY SECTOR(S)
  40 da 00 00 38 81 eb 00      00:28:14.977  READ VERIFY SECTOR(S)
  40 da 00 00 37 81 eb 00      00:28:14.976  READ VERIFY SECTOR(S)
  40 da 00 00 36 81 eb 00      00:28:14.975  READ VERIFY SECTOR(S)

Error 282 occurred at disk power-on lifetime: 1517 hours (63 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 20 81 eb  Error: UNC at LBA = 0x0b812077 = 193011831

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 00 00 20 81 eb 00      00:28:12.215  READ VERIFY SECTOR(S)
  40 da 00 00 1f 81 eb 00      00:28:12.213  READ VERIFY SECTOR(S)
  40 da 00 00 1e 81 eb 00      00:28:12.211  READ VERIFY SECTOR(S)
  40 da 00 00 1d 81 eb 00      00:28:12.210  READ VERIFY SECTOR(S)
  40 da 00 00 1c 81 eb 00      00:28:12.209  READ VERIFY SECTOR(S)

Error 281 occurred at disk power-on lifetime: 1517 hours (63 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 44 14 81 eb  Error: UNC at LBA = 0x0b811444 = 193008708

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 da 00 00 14 81 eb 00      00:28:09.859  READ VERIFY SECTOR(S)
  40 da 00 00 13 81 eb 00      00:28:09.857  READ VERIFY SECTOR(S)
  40 da 00 00 12 81 eb 00      00:28:09.856  READ VERIFY SECTOR(S)
  40 da 00 00 11 81 eb 00      00:28:09.855  READ VERIFY SECTOR(S)
  40 da 00 00 10 81 eb 00      00:28:09.853  READ VERIFY SECTOR(S)

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      1534         29097368
# 2  Conveyance offline  Completed: read failure       90%      1517         29369904
# 3  Conveyance offline  Completed: read failure       90%      1515         31592770
# 4  Extended offline    Completed: read failure       90%      1514         31592770
# 5  Short offline       Completed: read failure       90%      1506         31592770
# 6  Extended offline    Completed: read failure       90%      1506         46140825
# 7  Extended offline    Completed: read failure       90%      1506         31592770
# 8  Short offline       Completed without error       00%      1366         -
# 9  Extended offline    Completed without error       00%      1362         -
#10  Short offline       Completed without error       00%      1361         -
#11  Extended offline    Completed without error       00%      1355         -
#12  Extended offline    Aborted by host               90%      1350         -
#13  Conveyance offline  Completed without error       00%      1350         -
#14  Extended offline    Completed without error       00%      1349         -
#15  Short offline       Completed without error       00%      1348         -
#16  Short offline       Completed: read failure       90%      1342         151444365
#17  Conveyance offline  Completed: read failure       90%      1341         155502383
#18  Short offline       Completed: read failure       90%      1340         151444365
#19  Conveyance offline  Completed: read failure       90%      1339         156440234
#20  Conveyance offline  Completed: read failure       90%      1339         171974112
#21  Short offline       Completed: read failure       90%      1338         156440234
6 of 13 failed self-tests are outdated by newer successful extended offline self-test # 9

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


  The last couple of time GSmart hasn't been able to perform either a short or long test and reports 10% completed with read failure 

  The question is, should I be concerned about the HD or is this normal for an 8-9 month old hard drive?

---

### Post by ahallubuntu on 2012-10-24
Look at the attributes.  You'll get them with

```
smartctl -a /dev/sda
```

If you actually use GSmartControl (the graphic version), you'll see the Attributes in one of the tabs.  Any of them highlighted in Red?  If not, they are probably not indications of imminent failure.

In the text version of the attributes, look for Pending Sectors and Reallocated Sectors (raw values).  Pending sectors are sectors that cannot be read.  Sometimes you can clear them by wiping the drive (writing zeros to the whole thing) and then the drive will be fine.

One or two reallocated sectors isn't catastrophic unless that number keeps growing or gets very high, though on a six-month old drive that would be more alarming.

Still, it sure looks like a failing hard drive, and if it's under warranty I'd probably get it replaced.

---

### Post by ahallubuntu on 2012-10-24
Sorry - I see you did provide the attributes in your post, but the tabs were removed so I didn't read it clearly.

You've got 37 pending sectors, which is bad news.  Again, you could try wiping the drive and if all of those sectors go away, you could continue using the drive.  Some people would advise against it, but I have had success doing that (and no future drive problems).  Again, under warranty, I'd probably opt for replacing it.  You might want to wipe the drive anyway before sending it in for replacement, so you could check S.M.A.R.T. again after wiping before you send it back and then decide what to do.

---

### Post by abduljones on 2012-10-24
Thanks for your prompt reply. You have confirmed my suspicions, so i will give ebuyer a ring as they requested and see if i can get a new one sorted. I did wipe the drive and it's been fine for a couple of weeks, but it's starting to wobble again.I check a previous record (3 days before the above) and there were only 5 pending sectors then. As it's under warranty, I'll try for a new one in the first instance. Thanks again for your help.

---

