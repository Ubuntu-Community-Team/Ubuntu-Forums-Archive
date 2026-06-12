---
title: "How to interpret smartmontools numbers?"
date: 2008-05-26
forum: Hardware
---

### Post by befana on 2008-05-26
This is my report from smartmontools:

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MHY2120BH
Serial Number:    K427T7A29T9R
Firmware Version: 0040020B
User Capacity:    120,034,123,776 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x27
Local Time is:    Tue May 27 00:55:13 2008 EEST
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
data collection: 		 ( 487) seconds.
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
recommended polling time: 	 (  69) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       171109
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       27328929
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       499
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3936
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       4
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1425
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       487
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       38
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       9276
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       42 (Lifetime Min/Max 6/51)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       924
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       414580736
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       8845
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       1529035226332
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -

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



What the columns FLAG, VALUE, WORST, THRESH, TYPE, UPDATED, WHEN_FAILED and RAW_VALUE show?
And the numbers in these columns mean?

---

