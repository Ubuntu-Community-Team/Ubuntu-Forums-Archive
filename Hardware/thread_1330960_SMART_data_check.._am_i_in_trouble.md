---
title: "SMART data check.. am i in trouble?"
date: 2009-11-18
forum: Hardware
---

### Post by SurferGTO on 2009-11-18
After recieving the disc utility warning that my hard disc may be about to fail and has multiple errors, then reading that it may or may not be a bug with the new 9.10 upgrade, i decided to check the SMART data with an additional utility to see whats up. can anyone make sense of it for me since i dont really know what any of it means lol 

> === START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM250JI
Serial Number:    S15YJF0PC08251
Firmware Version: HS100-10
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Wed Nov 18 20:45:52 2009 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32)	The self-test routine was interrupted
					by the host with a hard or soft reset.
Total time to complete Offline 
data collection: 		 ( 103) seconds.
Offline data collection
capabilities: 			 (0x51) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
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
recommended polling time: 	 ( 103) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       213
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2000
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       745
  5 Reallocated_Sector_Ct   0x0033   078   078   010    Pre-fail  Always       -       211
  7 Seek_Error_Rate         0x000f   252   252   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   252   252   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       8824
 10 Spin_Retry_Count        0x0033   252   252   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   088   088   000    Old_age   Always       -       12256
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       607
184 Unknown_Attribute       0x0033   252   252   070    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       67
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       95
190 Airflow_Temperature_Cel 0x0022   054   031   040    Old_age   Always   In_the_past 46 (Lifetime Min/Max 10/69)
191 G-Sense_Error_Rate      0x0032   091   091   000    Old_age   Always       -       98550
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       475
193 Load_Cycle_Count        0x0032   002   002   000    Old_age   Always       -       999999
194 Temperature_Celsius     0x0022   054   031   000    Old_age   Always       -       46 (Lifetime Min/Max 10/69)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       14665
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       206
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 2
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

Error 2 occurred at disk power-on lifetime: 8823 hours (367 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 20 17 25 27 ed  Error: UNC 32 sectors at LBA = 0x0d272517 = 220669207

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 17 25 27 ed 00      02:49:37.000  READ DMA
  c8 00 08 a7 24 27 ed 00      02:49:29.562  READ DMA
  ef 05 fe 00 00 00 40 00      02:49:29.500  SET FEATURES [Enable APM]
  c8 00 40 ff 8b 5e ed 00      02:49:29.500  READ DMA
  c8 00 20 87 24 27 ed 00      02:49:29.500  READ DMA

Error 1 occurred at disk power-on lifetime: 6879 hours (286 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b7 7e 7b e8  Error: WP at LBA = 0x087b7eb7 = 142311095

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 00 b7 7e 7b e8 00   1d+02:44:41.000  WRITE DMA
  ec 00 00 00 00 00 a0 00   1d+02:44:20.437  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:44:20.437  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00   1d+02:44:20.437  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 00   1d+02:44:13.000  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        62         -
# 2  Short offline       Completed without error       00%        61         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


am i screwed?

---

