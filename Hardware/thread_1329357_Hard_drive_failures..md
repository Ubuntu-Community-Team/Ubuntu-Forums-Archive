---
title: "Hard drive failures."
date: 2009-11-17
forum: Hardware
---

### Post by dmizer on 2009-11-17
Well, I'm intermittenly getting the following error on both of my 500 gig IDE drives.
```
Nov 17 07:58:06 japan kernel: [104774.578484] sd 6:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 17 07:58:06 japan kernel: [104774.578490] end_request: I/O error, dev sdd, sector 4335
Nov 17 07:58:06 japan kernel: [104774.578501] EXT3-fs error (device sdd1): ext3_find_entry: reading directory #2 offset 0
```
It happens to both drives at the exact same time.

e2fsck shows no problems on either disk.

smartctl test also shows clean for both drives, but in case I've missed something here's the output:
```
$ sudo smartctl --all /dev/sdd1
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3320620A
Serial Number:    6QF3FQXB
Firmware Version: 3.AAF
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Nov 18 00:14:36 2009 JST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 115) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   092   088   006    Pre-fail  Always       -       196283562
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1204
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       760074534
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       14915
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       113
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   054   045    Old_age   Always       -       24 (Lifetime Min/Max 22/28)
194 Temperature_Celsius     0x0022   024   046   000    Old_age   Always       -       24 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   059   053   000    Old_age   Always       -       142042838
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 5
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

Error 5 occurred at disk power-on lifetime: 13240 hours (551 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00      00:00:39.432  READ DMA
  ec 00 00 00 00 00 a0 02      00:00:38.978  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:00:38.969  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      00:00:38.962  IDENTIFY DEVICE
  00 00 08 00 00 00 00 06      00:00:38.953  NOP [Abort queued commands]

Error 4 occurred at disk power-on lifetime: 13240 hours (551 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00      00:00:37.113  READ DMA
  ec 00 00 00 00 00 a0 02      00:00:38.978  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:00:38.969  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      00:00:38.962  IDENTIFY DEVICE
  00 00 08 00 00 00 00 06      00:00:38.953  NOP [Abort queued commands]

Error 3 occurred at disk power-on lifetime: 13240 hours (551 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00      00:00:37.113  READ DMA
  ec 00 00 00 00 00 a0 02      00:00:37.089  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:00:17.068  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      00:00:07.258  IDENTIFY DEVICE
  00 00 08 00 00 00 00 06      09:10:38.209  NOP [Abort queued commands]

Error 2 occurred at disk power-on lifetime: 13240 hours (551 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00      00:00:37.113  READ DMA
  c8 00 08 00 00 00 e0 00      00:00:37.089  READ DMA
  ec 00 00 00 00 00 a0 02      00:00:17.068  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:00:07.258  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      09:10:38.209  IDENTIFY DEVICE

Error 1 occurred at disk power-on lifetime: 13240 hours (551 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      00:00:37.113  READ DMA
  ec 00 00 00 00 00 a0 02      00:00:37.089  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      00:00:17.068  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      00:00:07.258  IDENTIFY DEVICE
  00 00 aa 00 00 00 00 06      09:10:38.209  NOP [Abort queued commands]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     14902         -

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

Any ideas on what might be causing this problem? Obviously, when I get this error, both drives are lost. Unfortunately, this causes my whole server to become unstable because both drives are hosting NFS shares, including a few running VMware images.

At first, obviously I thought that I had a failing drive, but why would two drives fail at the exact same time every time? Is it possible that I have a bad IDE controller, and if so ... is there any way to test that?

---

### Post by cascade9 on 2009-11-17
Exactly the same time? Thats obviously a problem. #-o

Aside from just pulling the drives (and the cables! I've seen IDE cables go dodgy and give all sorts of problems) and trying them in a different system, there is one thing I can think of that will test your IDE controller, PC Check-

[http://www.eurosoft-uk.com/pc_check.htm](http://www.eurosoft-uk.com/pc_check.htm)

Great tool, but its not cheap though.

---

### Post by dmizer on 2009-11-17
Well, it just happened again.

Seems to happen when my VMware hypervisor is really busy. I'm running VMware server 2. Has anyone else experienced this?

---

