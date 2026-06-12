---
title: "Hard drive making thrashing noise"
date: 2009-09-08
forum: Hardware
---

### Post by Lucky75 on 2009-09-08
Hi all,

My drive suddenly started making the thrashing noise, where it sounds like I'm overworking my drive heads. However, nothing was eating up CPU usage, and I wasn't really doing a lot of read/writes to my drive.

Is that a bad sign? Freeing up some space seemed to make it happen less often, but it was going for a good 5 minutes straight. I had 9 gigs left, freed up to about 35 now. Seems to have helped a bit?

If it's about to die, how would I make an image of *most* of the drive (excluding home folder and other useless folders) so I can restore if need be? How would I restore it once I swap the drive out?

And how can I tell for sure which drive it is?

EDIT: ACtually,  *gnome-video-thru* seems to be spiking. What is that?

---

### Post by IcarusR on 2009-09-08
Free up more space. Move your 'home' to a seperate drive with more space.
To list all drive in system. You should be able to work out which one it is by size.
```
sudo fdisk -l
```

Hirens Boot CD has several imaging utilities on it download from here
[http://www.hirensbootcd.net/]("http://www.hirensbootcd.net/")

Foun this thread which should help you
[http://ubuntuforums.org/showthread.php?t=287522]("http://ubuntuforums.org/showthread.php?t=287522")

---

### Post by rob-ward on 2009-09-08
You may want to have a look at the status of the drive if it were making a thrashing noise, you can use the smart tools to do this.

Firstly install smartmontools
```
sudo apt-get install smartmontools 
```then run
```
sudo smartctl -a /dev/sda
```that should give you a printout showing you info about your hdd, post it here if you need help understanding it.

However if your hdd is making funny sounds I would consider replacing it, you can just mirror all of the drive onto a new disk using dd to create a complete backup.

---

### Post by GoldenSun on 2009-09-08
I would replace asap as it might be a sign of it going out soon.  You can use a program called rsynch to copy all folders/files onto another hd.

---

### Post by rob-ward on 2009-09-08
Does rsynch work to copy the entire OS, i've always used dd, if it does I might try that next time. 

But ye I agree that the HDD should be replaces ASAP, but do post the results from smartctl

---

### Post by Lucky75 on 2009-09-08
Thanks guys! I've started making backups, but I'm getting some IO errors. The noise is intermittent now.

```

sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAKS-00TMA0
Serial Number:    WD-WCAPW1825421
Firmware Version: 12.01C01
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Sep  8 18:23:06 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (12600) seconds.
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
recommended polling time: 	 ( 157) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   207   168   021    Pre-fail  Always       -       4641
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       81
  5 Reallocated_Sector_Ct   0x0033   184   184   140    Pre-fail  Always       -       124
  7 Seek_Error_Rate         0x000e   199   173   051    Old_age   Always       -       140
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18700
 10 Spin_Retry_Count        0x0012   100   253   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       76
192 Power-Off_Retract_Count 0x0032   190   190   000    Old_age   Always       -       7810
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       7826
194 Temperature_Celsius     0x0022   112   089   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   152   152   000    Old_age   Always       -       48
197 Current_Pending_Sector  0x0012   195   193   000    Old_age   Always       -       467
198 Offline_Uncorrectable   0x0010   200   193   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       6
200 Multi_Zone_Error_Rate   0x0008   080   080   051    Old_age   Offline      -       8041

SMART Error Log Version: 1
ATA Error Count: 1607 (device log contains only the most recent five errors)
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

Error 1607 occurred at disk power-on lifetime: 18686 hours (778 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 27 8f d9 e3  Error: UNC at LBA = 0x03d98f27 = 64589607

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 8f d9 03 00      04:33:58.262  READ DMA
  27 00 00 00 00 00 00 00      04:33:58.262  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      04:33:58.253  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      04:33:58.246  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      04:33:58.246  READ NATIVE MAX ADDRESS EXT

Error 1606 occurred at disk power-on lifetime: 18686 hours (778 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 27 8f d9 e3  Error: UNC at LBA = 0x03d98f27 = 64589607

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 8f d9 03 00      04:33:54.670  READ DMA
  27 00 00 00 00 00 00 00      04:33:54.670  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      04:33:54.661  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      04:33:54.654  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      04:33:54.654  READ NATIVE MAX ADDRESS EXT

Error 1605 occurred at disk power-on lifetime: 18686 hours (778 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 27 8f d9 e3  Error: UNC at LBA = 0x03d98f27 = 64589607

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 8f d9 03 00      04:33:51.133  READ DMA
  27 00 00 00 00 00 00 00      04:33:51.133  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      04:33:51.124  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      04:33:51.117  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      04:33:51.117  READ NATIVE MAX ADDRESS EXT

Error 1604 occurred at disk power-on lifetime: 18686 hours (778 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 27 8f d9 e3  Error: UNC at LBA = 0x03d98f27 = 64589607

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 8f d9 03 00      04:33:47.149  READ DMA
  27 00 00 00 00 00 00 00      04:33:47.149  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      04:33:47.140  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      04:33:47.133  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      04:33:47.133  READ NATIVE MAX ADDRESS EXT

Error 1603 occurred at disk power-on lifetime: 18686 hours (778 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 28 8f d9 e3  Error: UNC at LBA = 0x03d98f28 = 64589608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 8f d9 03 00      04:33:43.329  READ DMA
  27 00 00 00 00 00 00 00      04:33:43.329  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      04:33:43.320  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 00      04:33:43.313  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      04:33:43.313  READ NATIVE MAX ADDRESS EXT

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


```

```

sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500320AS
Serial Number:    9QM1Z430
Firmware Version: SD15
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Sep  8 18:24:25 2009 EDT
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
data collection: 		 ( 634) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 117) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   105   099   006    Pre-fail  Always       -       10100595
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       16
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       70863586
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       12090
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       25
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   051   051   000    Old_age   Always       -       49
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       15
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   050   045    Old_age   Always       -       36 (Lifetime Min/Max 35/45)
194 Temperature_Celsius     0x0022   036   050   000    Old_age   Always       -       36 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   045   030   000    Old_age   Always       -       10100595
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       319
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       319
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 49 (device log contains only the most recent five errors)
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

Error 49 occurred at disk power-on lifetime: 11322 hours (471 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00  27d+09:39:15.595  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:15.594  READ FPDMA QUEUED
  60 00 10 ff ff ff 4f 00  27d+09:39:15.594  READ FPDMA QUEUED
  60 00 68 ff ff ff 4f 00  27d+09:39:15.593  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  27d+09:39:15.592  READ NATIVE MAX ADDRESS EXT

Error 48 occurred at disk power-on lifetime: 11322 hours (471 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 68 ff ff ff 4f 00  27d+09:39:11.801  READ FPDMA QUEUED
  60 00 10 ff ff ff 4f 00  27d+09:39:11.800  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:11.800  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:11.798  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  27d+09:39:11.798  READ NATIVE MAX ADDRESS EXT

Error 47 occurred at disk power-on lifetime: 11322 hours (471 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 10 ff ff ff 4f 00  27d+09:39:08.003  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:08.002  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:08.002  READ FPDMA QUEUED
  60 00 10 ff ff ff 4f 00  27d+09:39:08.001  READ FPDMA QUEUED
  60 00 40 ff ff ff 4f 00  27d+09:39:08.001  READ FPDMA QUEUED

Error 46 occurred at disk power-on lifetime: 11322 hours (471 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00  27d+09:39:04.174  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00  27d+09:39:04.174  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00  27d+09:39:04.173  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  27d+09:39:04.172  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02  27d+09:39:04.165  IDENTIFY DEVICE

Error 45 occurred at disk power-on lifetime: 11322 hours (471 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00  27d+09:39:00.407  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  27d+09:39:00.407  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02  27d+09:39:00.400  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02  27d+09:39:00.391  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  27d+09:39:00.391  READ NATIVE MAX ADDRESS EXT

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

```

```

sudo smartctl -a /dev/sdc
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD6400AAKS-22A7B0
Serial Number:    WD-WMASY4545884
Firmware Version: 01.03B01
User Capacity:    640,135,028,736 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Sep  8 18:27:29 2009 EDT
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
data collection: 		 (11580) seconds.
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
recommended polling time: 	 ( 136) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   162   162   021    Pre-fail  Always       -       4883
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       26
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1216
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       24
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       26
194 Temperature_Celsius     0x0022   111   100   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

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


```
No idea what this means :)

---

### Post by rob-ward on 2009-09-09
K, this site [http://en.wikipedia.org/wiki/S.M.A.R.T.#Known_ATA_S.M.A.R.T._attributes](http://en.wikipedia.org/wiki/S.M.A.R.T.#Known_ATA_S.M.A.R.T._attributes) can explain what these mean if you are intrested. Te primary ones to look at are read error rate which literally tells you how many time the drive has gone to read a piece of data and had an error in doing so, The number of reallocated sectors, the higher the number the more sectors of data the HDD has moved because it is damaged(often meaning the hdd surfae is dammaged) and the number of offline sectors.

Looking at sda you can see that the read error rate is zero which is good, overall sda isn't in a bad shape however it has aged a fair bit but it has being online for over two years so it is getting old.

SDB
This is the drive I would be most worried about(not sure is this the drive making the noises) This drive has a high error rate, a giant seek error and a high Hardware ECC Recovery rate. Like I said if I were to pick a drive which might be failing from the stats here I would say this one.

SDC
This drive is in very good shape, looks like you havn't had it very long(compared with the others) I don't think this drive is the issue.

Do you know which drive is making the sound, if not next time it is doing it you way want to have a look in the case see if you can locate which one. I'm guessing it will be the seagate, you can often tell by placing you hand on the hdd as you can normally feel the clunk.

Hope that helps

---

### Post by Lucky75 on 2009-09-09
> df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1              381G   335G    35G  91% /
/dev/sda1              501G   182G   320G  37% /media/sdb1
/dev/sdb3              106G    20G    86G  19% /media/sdc3
/dev/sdc1              641G   244G   398G  38% /media/disk


Does that mean that it's my main OS (mounted on "/") that's causing the problem?

Because I can't tell if it's that one or the one at /media/sdb1 which is mounted on sda.

the /dev/sda should be newer than the /dev/sdb, but of course, it's running the OS, so it would have more read/writes, while the other is primarily used for storing data.

Thanks for the help!

---

### Post by rob-ward on 2009-09-09
Yes it is likely dev/sdb which has you OS on that is the problem. I would suggest replacing this drive or at least copying the data that you want onto one of your other drives.

---

### Post by GoldenSun on 2009-09-09
I would personally get a new hd.  Copy all media and just the home folder to save all configs.  Then start with a fresh install of ubuntu.  A hd transplant could break things, and links to folders could be messed up.

---

### Post by Lucky75 on 2009-09-09
Yeah, the weird thing is that it was the other Hard drive (/dev/sda) that was actually having issues when I was copying data, so I don't know if it's /dev/sdb that's causing problems?

/dev/sda was having IO read issues.

---

### Post by rob-ward on 2009-09-09
A way of testing may be to wrtie a large amount of data and copy it backwards and forwards between partitions see if either breaks with IO errors, maybe you have more than one bad hdd.

---

### Post by Wee_Guy on 2009-09-13
I've had 2 Seagate Baracudas (7200.10) fail on me. Notably, both of them failed instantly, with no problems beforehand, and both of them were in external enclosures which ran _very_ hot, so it was likely the heat that killed them, but I have [read things]("http://datacent.com/datarecovery/hdd/seagate/Barracuda+7200.11") about the 7200s having other problems.

---

### Post by rob-ward on 2009-09-13
The seagate drives are generally horrible, the number of them that I have seen fail is unbelievable, I would recommend that people stick with the WD drives, namely the WD black edition drives as these are very reliable and fast.

---

