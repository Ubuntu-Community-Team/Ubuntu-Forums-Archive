---
title: "How can I Check/Fix Hard Drives??"
date: 2010-05-31
forum: Hardware
---

### Post by alek66 on 2010-05-31
Hello everyone!!!

I am putting togheter a NAS, I will use FreeNas, I am Using some Ata Disks. The disks are like 7 8 years old, so I want to do a low level check. They must have some errors, or something, is there a way to do a low level check? Even If they have some bad clusters, is there a way to fix them, or leave them out?

I dont how to explain very well... I just want to do a "full service" to this old disks.

(I dont have sensitive data or anything like that, I want to use some pieces I have in my house laying around. i Just want to learn and have a sofisticated file server :) )

Feel free to coment and recomend me some ideas on how to service my disks.

May 31 Edit:
I found some info on my disks, perhaps its usefull:
ATA disk:
---------
ATA channel 0:
   Master:  ad0 <QUANTUM FIREBALLP LM30/A35.0700> ATA/ATAPI revision 5
   Slave:   ad1 <ST380011A/3.04> ATA/ATAPI revision 6
ATA channel 1:
   Master:      no device present
   Slave:       no device present

S.M.A.R.T. [/dev/ad0]:
----------------------
smartctl 5.39.1 2010-01-28 r3054 [FreeBSD 7.3-RELEASE-p1 i386] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Quantum Fireball Plus LM series
Device Model:     QUANTUM FIREBALLP LM30
Serial Number:    186052930382
Firmware Version: A35.0700
User Capacity:    30,020,272,128 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 1
Local Time is:    Mon May 31 10:00:00 2010 ART
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever
					been run.
Total time to complete Offline
data collection: 		 (  46) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  24) minutes.

SMART Attributes Data Structure revision number: 11
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 1 Raw_Read_Error_Rate     0x0029   100   253   020    Pre-fail  Offline      -       0
 3 Spin_Up_Time            0x0027   060   055   020    Pre-fail  Always       -       5106
 4 Start_Stop_Count        0x0032   092   092   008    Old_age   Always       -       5688
 5 Reallocated_Sector_Ct   0x0033   100   100   020    Pre-fail  Always       -       0
 7 Seek_Error_Rate         0x000b   100   093   023    Pre-fail  Always       -       0
 9 Power_On_Hours          0x0012   035   035   001    Old_age   Always       -       42884
10 Spin_Retry_Count        0x0026   100   100   020    Old_age   Always       -       0
11 Calibration_Retry_Count 0x0013   100   100   020    Pre-fail  Always       -       0
12 Power_Cycle_Count       0x0032   097   097   008    Old_age   Always       -       2251
13 Read_Soft_Error_Rate    0x000b   100   093   023    Pre-fail  Always       -       0
199 UDMA_CRC_Error_Count    0x001a   186   186   000    Old_age   Always       -       14
196 Reallocated_Event_Count 0x0010   100   253   020    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0032   100   100   020    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 2795 (device log contains only the most recent five errors)
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

Error 2795 occurred at disk power-on lifetime: 19500 hours (812 days + 12 hours)
 When the command that caused the error occurred, the device was in an unknown state.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 40 d1 01 50 4f 60 e0  Error: UNC at LBA = 0x00604f50 = 6311760

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 40 d8 01 50 4f 60 e0 00      00:06:50.853  READ VERIFY SECTOR(S)
 40 d8 01 4f 4f 60 e0 00      00:06:50.852  READ VERIFY SECTOR(S)
 40 d8 02 51 4f 60 e0 00      00:06:50.841  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:50.834  READ DMA
 40 d8 02 4f 4f 60 e0 00      00:06:45.528  READ VERIFY SECTOR(S)

Error 2794 occurred at disk power-on lifetime: 19500 hours (812 days + 12 hours)
 When the command that caused the error occurred, the device was in an unknown state.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 40 d1 01 50 4f 60 e0  Error: UNC at LBA = 0x00604f50 = 6311760

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 40 d8 02 4f 4f 60 e0 00      00:06:45.528  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:45.527  READ DMA
 40 d8 04 53 4f 60 e0 00      00:06:45.516  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:45.509  READ DMA
 40 d8 04 4f 4f 60 e0 00      00:06:40.253  READ VERIFY SECTOR(S)

Error 2793 occurred at disk power-on lifetime: 19500 hours (812 days + 12 hours)
 When the command that caused the error occurred, the device was in an unknown state.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 40 d1 03 50 4f 60 e0  Error: UNC at LBA = 0x00604f50 = 6311760

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 40 d8 04 4f 4f 60 e0 00      00:06:40.253  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:40.253  READ DMA
 40 d8 08 57 4f 60 e0 00      00:06:40.241  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:40.234  READ DMA
 40 d8 08 4f 4f 60 e0 00      00:06:36.266  READ VERIFY SECTOR(S)

Error 2792 occurred at disk power-on lifetime: 19500 hours (812 days + 12 hours)
 When the command that caused the error occurred, the device was in an unknown state.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 40 d1 07 50 4f 60 e0  Error: UNC at LBA = 0x00604f50 = 6311760

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 40 d8 08 4f 4f 60 e0 00      00:06:36.266  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:36.260  READ DMA
 40 d8 10 4f 4f 60 e0 00      00:06:32.420  READ VERIFY SECTOR(S)
 40 d8 10 3f 4f 60 e0 00      00:06:32.420  READ VERIFY SECTOR(S)
 40 d8 20 5f 4f 60 e0 00      00:06:32.408  READ VERIFY SECTOR(S)

Error 2791 occurred at disk power-on lifetime: 19500 hours (812 days + 12 hours)
 When the command that caused the error occurred, the device was in an unknown state.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 40 d1 0f 50 4f 60 e0  Error: UNC at LBA = 0x00604f50 = 6311760

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 40 d8 10 4f 4f 60 e0 00      00:06:32.420  READ VERIFY SECTOR(S)
 40 d8 10 3f 4f 60 e0 00      00:06:32.420  READ VERIFY SECTOR(S)
 40 d8 20 5f 4f 60 e0 00      00:06:32.408  READ VERIFY SECTOR(S)
 c8 d8 01 00 00 00 e0 00      00:06:32.401  READ DMA
 40 d8 20 3f 4f 60 e0 00      00:06:28.471  READ VERIFY SECTOR(S)

SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging

S.M.A.R.T. [/dev/ad1]:
----------------------
smartctl 5.39.1 2010-01-28 r3054 [FreeBSD 7.3-RELEASE-p1 i386] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST380011A
Serial Number:    3JV09JN5
Firmware Version: 3.04
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Mon May 31 10:00:01 2010 ART
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
					No General Purpose Logging support.
Short self-test routine
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  58) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 1 Raw_Read_Error_Rate     0x000f   063   051   006    Pre-fail  Always       -       180283537
 3 Spin_Up_Time            0x0003   099   098   000    Pre-fail  Always       -       0
 4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       233
 5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
 7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       753968728
 9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       12603
10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       2030
194 Temperature_Celsius     0x0022   025   058   000    Old_age   Always       -       25
195 Hardware_ECC_Recovered  0x001a   063   050   000    Old_age   Always       -       180283537
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   001   000    Old_age   Always       -       560
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 38 (device log contains only the most recent five errors)
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

Error 38 occurred at disk power-on lifetime: 3307 hours (137 days + 19 hours)
 When the command that caused the error occurred, the device was active or idle.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 84 51 01 00 00 00 f0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.194  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.192  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:53.095  READ DMA

Error 37 occurred at disk power-on lifetime: 3307 hours (137 days + 19 hours)
 When the command that caused the error occurred, the device was active or idle.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 84 51 01 00 00 00 f0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.194  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.192  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:53.095  READ DMA

Error 36 occurred at disk power-on lifetime: 3307 hours (137 days + 19 hours)
 When the command that caused the error occurred, the device was active or idle.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 84 51 01 00 00 00 f0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.194  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.192  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:53.095  READ DMA

Error 35 occurred at disk power-on lifetime: 3307 hours (137 days + 19 hours)
 When the command that caused the error occurred, the device was active or idle.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 84 51 01 00 00 00 f0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.194  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.192  READ DMA
 ef 03 41 00 10 00 b0 00      00:00:53.095  SET FEATURES [Set transfer mode]

Error 34 occurred at disk power-on lifetime: 3307 hours (137 days + 19 hours)
 When the command that caused the error occurred, the device was active or idle.

 After command completion occurred, registers were:
 ER ST SC SN CL CH DH
 -- -- -- -- -- -- --
 84 51 01 00 00 00 f0  Error: ICRC, ABRT 1 sectors at LBA = 0x00000000 = 0

 Commands leading to the command that caused the error were:
 CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
 -- -- -- -- -- -- -- --  ----------------  --------------------
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.195  READ DMA
 c8 03 01 00 00 00 f0 00      00:00:56.194  READ DMA
 ef 03 41 00 10 00 b0 00      00:00:56.192  SET FEATURES [Set transfer mode]
 ef 03 0c 00 10 00 b0 00      00:00:53.095  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

---

### Post by IcarusR on 2010-05-31
Some hard drive manufacturers have hdd checking & low level formating software on their websites for download.

Hirens boot cd has a few hdd check programs on it. Available for download on the net, do a google search.

---

