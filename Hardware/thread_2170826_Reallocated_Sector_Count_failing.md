---
title: "Reallocated Sector Count failing"
date: 2013-08-27
forum: Hardware
---

### Post by foxy123 on 2013-08-27
I've got the following error on my ASUS 1015px when go into SMART Data and Tests:

```
**ID** 5 
**Attribute** Reallocated Sector Count
**Value** 0 sectors
**Assessment** [COLOR="#FF0000"]FAILING[/COLOR]

```

The Overall Assessment is [COLOR="#FF0000"]DISK IS LIKELY TO FAIL SOON[/COLOR].

I wonder if the disk is almost dead? My only concern that in value it shows 0 sectors.

---

### Post by tgalati4 on 2013-08-27
Back up your data.  Now.

Open a terminal:

```
sudo smartctl -a /dev/sda
```

Either the sector relocation count is really 0, or the Attribute was read incorrectly--some undecipherable hex number--so a 0 was used instead.  Or the number was so large that it also caused 0 to be output.  Either way, do a backup.

---

### Post by foxy123 on 2013-08-28
Here you are:
```
lubuntu@lubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS543232A7A384
Serial Number:    E24312430N76BH
LU WWN Device Id: 5 000cca 694c93278
Firmware Version: ES2OA60W
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Wed Aug 28 20:47:57 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   45) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  95) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   086   086   062    Pre-fail  Always       -       7733252
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   212   212   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       2985
  5 Reallocated_Sector_Ct   0x0033   001   001   005    Pre-fail  Always   FAILING_NOW 0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       1393
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       2908
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       515
193 Load_Cycle_Count        0x0012   096   096   000    Old_age   Always       -       49906
194 Temperature_Celsius     0x0002   187   187   000    Old_age   Always       -       32 (Min/Max 13/45)
196 Reallocated_Event_Count 0x0032   054   054   000    Old_age   Always       -       1264
197 Current_Pending_Sector  0x0022   001   001   000    Old_age   Always       -       2980
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 5702 (device log contains only the most recent five errors)
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

Error 5702 occurred at disk power-on lifetime: 1393 hours (58 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 bd 0b 00 00  Error: UNC at LBA = 0x00000bbd = 3005

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 10 43 da 40 00      00:10:04.517  READ FPDMA QUEUED
  60 08 00 a8 0b 80 40 00      00:10:04.517  READ FPDMA QUEUED
  60 08 00 a0 0b 80 40 00      00:10:04.498  READ FPDMA QUEUED
  60 08 08 08 43 da 40 00      00:10:04.498  READ FPDMA QUEUED
  60 08 00 98 0b 80 40 00      00:10:04.498  READ FPDMA QUEUED

Error 5701 occurred at disk power-on lifetime: 1393 hours (58 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 bd 0b 00 00  Error: UNC at LBA = 0x00000bbd = 3005

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 b8 41 da 40 00      00:10:01.268  READ FPDMA QUEUED
  60 08 08 b8 0b 00 40 00      00:10:01.268  READ FPDMA QUEUED
  60 08 10 48 0b 80 40 00      00:10:01.268  READ FPDMA QUEUED
  60 08 00 b0 41 da 40 00      00:10:01.268  READ FPDMA QUEUED
  60 08 08 b0 0b 00 40 00      00:10:01.268  READ FPDMA QUEUED

Error 5700 occurred at disk power-on lifetime: 1393 hours (58 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 bd 0b 00 00  Error: UNC at LBA = 0x00000bbd = 3005

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 c8 41 da 40 00      00:09:43.378  READ FPDMA QUEUED
  60 08 08 b8 0b 00 40 00      00:09:43.364  READ FPDMA QUEUED
  60 08 00 c0 41 da 40 00      00:09:43.364  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:09:43.364  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:09:43.364  READ NATIVE MAX ADDRESS EXT

Error 5699 occurred at disk power-on lifetime: 1393 hours (58 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 bd 0b 00 00  Error: UNC at LBA = 0x00000bbd = 3005

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 c0 41 da 40 00      00:09:40.166  READ FPDMA QUEUED
  60 08 08 b8 0b 00 40 00      00:09:40.166  READ FPDMA QUEUED
  60 08 00 b8 41 da 40 00      00:09:40.166  READ FPDMA QUEUED
  60 08 08 b0 0b 00 40 00      00:09:40.166  READ FPDMA QUEUED
  60 08 00 b0 41 da 40 00      00:09:40.166  READ FPDMA QUEUED

Error 5698 occurred at disk power-on lifetime: 1393 hours (58 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 bd 0b 00 00  Error: UNC at LBA = 0x00000bbd = 3005

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 08 0b 80 40 00      00:09:23.091  READ FPDMA QUEUED
  60 08 08 b8 0b 00 40 00      00:09:23.074  READ FPDMA QUEUED
  60 08 00 00 0b 80 40 00      00:09:23.074  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:09:23.074  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:09:23.074  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1379         219
# 2  Extended offline    Completed: read failure       90%      1379         5014428
# 3  Short offline       Completed: read failure       50%      1369         219

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


```

---

### Post by tgalati4 on 2013-08-29
Well you have almost 50K of load cycles in 1400 hours of use.  You might have an issue with head parking since it parks 35 times per hour.  It's probably too late to save this drive, but in the future keep an eye on it and use *hdparm* to change the head park cycle time.  You have 5700 ATA or communication errors.  You have 1264 relocated sectors.  Your disk did not pass a complete read test, failing at the 10% disk location.  So there are several errors on your disk and it is truly failing.

What was your question?

---

### Post by foxy123 on 2013-08-29
OK, thanks a lot. To be honest I do not use this netbook at all at the moment and everything that is on the HD has been backed up. I was thinking to install some lightweight distro and use it occasionally for travelling but now I guess I will just forget about it. It is probably not worth trying to replace the drive. Or I could buy a small 250Gb HDD for 35 quid (or even smaller SSD for the same money) but not sure if I will do.

I just wonder why it failed. It had Ubuntu 12.04 installed without any major modifications.

---

### Post by tgalati4 on 2013-08-29
Because Linux writes many log files, all the time, the drive spin-down time can cause the drive to spin down and wake up and spin down in an endless cycle, wearing out the drive.  Did you not hear the annoying clicks while using the machine?  The disk should remain spinning for several minutes when in use and only spin-down when the machine is put to sleep or if left, unused for several minutes.

An SSD would be a good upgrade for this machine.

---

### Post by foxy123 on 2013-08-30
Could anyone recommend a 64gb SSD for ASUS 1015PX? Will any 2.5 SSD fit?

---

### Post by jonnyboysmithy on 2013-08-31
Interestingly my laptops drive had the same issue of constantly clicking. Mine has 106K load unload cycle count and 7519hrs running time and no errors whatsoever. I fixed it early but its second hand and the last owner just used it: click click click... hence the high number. 
Its supposed to be a "green" harddisk made by western digital, meaning by default it shuts off after 8 seconds. I don't see how that is green because I think its going to end up dead if it wears itself out like this. 

Does anyone know if the OP's disk failure is related to the high cycle count or is it just a disk failure?

---

### Post by tgalati4 on 2013-08-31
Some reading:  [https://bbs.archlinux.org/viewtopic.php?id=73573](https://bbs.archlinux.org/viewtopic.php?id=73573)

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

I'm just guessing, because of the moderately high cycle count and low number of hours.  Besides, notebooks in general have poor build quality and cheap parts to keep the price-point low.  

The small size of notebooks means that they get tossed around more and that can lead to head crashes--which is a possibility, because it did not pass the surface read tests.

---

