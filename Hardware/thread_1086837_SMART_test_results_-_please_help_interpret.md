---
title: "SMART test results - please help interpret"
date: 2009-03-04
forum: Hardware
---

### Post by j123jam on 2009-03-04
Hi Folks. I have a Sony Vaio laptop that's less than a year and a half old.  I replaced the HDD once when it died (Fujitsu brand), but now I'm afraid I might be having more problems.  I primarily use Windows Vista (please spare me the jokes), but I was able to boot into Ubuntu LiveCD to run SMART tests.  The long test is running now, but will take over 2 hours more to finish.  I am posting the SMART results for the short test below and I'm hoping somebody can help me interpret them because I have no idea what they mean.  I really appreciate any help!

Some symptoms: Cannot boot into Vista, says registry corrupted.  Cannot boot into windows recovery partition to run the startup repair (it starts booting but hangs with black screen and white pointer which I can move around).  I can't even boot from Vista CD (it also hangs at black screen, HDD activity light solid).

Here's the SMART results:
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MHX2250BT
Serial Number:    K204T7826E6Y
Firmware Version: 0041000B
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Wed Mar  4 17:17:22 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (1382) seconds.
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
recommended polling time: 	 ( 159) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       36175
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       74514432
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1322
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8439613030467
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3495
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       2934
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       644
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       31672
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       34 (Lifetime Min/Max 16/49)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       15
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       410714179
197 Current_Pending_Sector  0x0012   095   095   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0010   097   097   000    Old_age   Offline      -       6
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       549847
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       2628548428173
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 410 (device log contains only the most recent five errors)
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

Error 410 occurred at disk power-on lifetime: 2934 hours (122 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 03 24 08 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 08 00 40 00      00:13:30.027  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:13:30.026  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:13:30.026  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:13:30.026  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:13:30.025  READ NATIVE MAX ADDRESS EXT

Error 409 occurred at disk power-on lifetime: 2934 hours (122 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 03 24 08 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 08 00 40 00      00:13:24.397  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:13:24.397  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:13:24.397  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:13:24.396  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:13:24.396  READ NATIVE MAX ADDRESS EXT

Error 408 occurred at disk power-on lifetime: 2934 hours (122 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 03 24 08 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 08 00 40 00      00:13:18.768  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:13:18.768  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:13:18.768  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:13:18.767  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:13:18.767  READ NATIVE MAX ADDRESS EXT

Error 407 occurred at disk power-on lifetime: 2934 hours (122 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 03 24 08 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 08 00 40 00      00:13:13.139  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:13:13.139  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:13:13.138  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:13:13.138  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:13:13.138  READ NATIVE MAX ADDRESS EXT

Error 406 occurred at disk power-on lifetime: 2934 hours (122 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 03 24 08 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 08 00 40 00      00:13:07.510  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:13:07.510  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:13:07.509  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:13:07.509  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:13:07.509  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      2934         2084
# 2  Short offline       Completed without error       00%         3         -

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

### Post by giacof on 2009-03-05
Hi. Parhaps you could start here: [http://www.linuxjournal.com/article/6983]("http://www.linuxjournal.com/article/6983")
Anyway, though I cannot claim I'm such an expert in hardware issues, I see some very bad figures in your report. Sounds weird, as two HDDs gone in less than one year and a half are far from normal lifetime. There might be some hw problem in your laptop, say in the controller. But, again, I cannot help you in identifying a hw issue.

---

