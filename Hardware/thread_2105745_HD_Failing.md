---
title: "HD Failing?"
date: 2013-01-16
forum: Hardware
---

### Post by ugriffin on 2013-01-16
I'm not sure, but I think my hard drive is failing. The funny part is that Ubuntu's Disk utility says it's fine, with 1705 reallocated sectors, while Smartctl says it's (may?) be failing. The pre-fail thing looks scary anyways. :P

Another potential sign is that Windows constantly requests a drive-repair reboot and CHKDSK hangs at 11%.

Could someone help me make sense of the information? I'm going to post my smartCTL results here. Thanks! :popcorn:

```

ugriffin@ubuntu:~$ smartctl -i /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sda failed: Permission denied
ugriffin@ubuntu:~$ sudo smartctl -i /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK3265GSX
Serial Number:    31CDD47QB
LU WWN Device Id: 5 000039 32ab83243
Firmware Version: GJ002F
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jan 16 22:44:50 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

ugriffin@ubuntu:~$ smartctl --test=long /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sda failed: Permission denied
ugriffin@ubuntu:~$ sudo smartctl --test=long /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 96 minutes for test to complete.
Test will complete after Thu Jan 17 00:21:29 2013

Use smartctl -X to abort test.
ugriffin@ubuntu:~$ smartctl --all /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sda failed: Permission denied
ugriffin@ubuntu:~$ sudo smartctl --all /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK3265GSX
Serial Number:    31CDD47QB
LU WWN Device Id: 5 000039 32ab83243
Firmware Version: GJ002F
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jan 16 22:46:13 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 249)	Self-test routine in progress...
					90% of test remaining.
Total time to complete Offline 
data collection: 		(  120) seconds.
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
recommended polling time: 	 (  96) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1193
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       628
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1705
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       809
 10 Spin_Retry_Count        0x0033   112   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       579
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       48
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       12
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       18992
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Min/Max 10/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       130
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       89
222 Loaded_Hours            0x0032   099   099   000    Old_age   Always       -       544
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       338
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               90%       809         -

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

ugriffin@ubuntu:~$ ^C
ugriffin@ubuntu:~$ 

```

EDIT: Added the smartCTL results after a 'long' Scan. Disk Utility still says the disk is fine. 
```

smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK3265GSX
Serial Number:    31CDD47QB
LU WWN Device Id: 5 000039 32ab83243
Firmware Version: GJ002F
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Jan 17 00:39:28 2013 EST
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
data collection: 		(  120) seconds.
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
recommended polling time: 	 (  96) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1193
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       628
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       1705
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       811
 10 Spin_Retry_Count        0x0033   112   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       579
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       48
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       12
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       18996
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       33 (Min/Max 10/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       130
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       89
222 Loaded_Hours            0x0032   099   099   000    Old_age   Always       -       546
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       330
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       810         -
# 2  Extended offline    Aborted by host               90%       809         -

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

