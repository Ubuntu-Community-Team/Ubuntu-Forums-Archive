---
title: "possible failure of my hard drive disk"
date: 2014-11-29
forum: Hardware
---

### Post by -@23%^yu* on 2014-11-29
I am not sure wether my HDD has failed or not. Just ran the command ```
 sudo smartctl --all /dev/sda


```got the results. can any one help me reading the data and explan me what the problem is?```
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST500DM002-1BC142
Serial Number:    Z2AKQTK4
LU WWN Device Id: 5 000c50 03fbc7197
Firmware Version: JC4B
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat Nov 29 12:08:36 2014 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  82) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006    Pre-fail  Always       -       95910010
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   088   088   020    Old_age   Always       -       12354
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   085   060   030    Pre-fail  Always       -       347708686
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8046
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   093   093   020    Old_age   Always       -       7669
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   067   067   000    Old_age   Always       -       33
188 Command_Timeout         0x0032   100   095   000    Old_age   Always       -       2 2 3181
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   051   045    Old_age   Always       -       32 (Min/Max 32/32)
194 Temperature_Celsius     0x0022   032   049   000    Old_age   Always       -       32 (0 19 0 0 0)
195 Hardware_ECC_Recovered  0x001a   037   024   000    Old_age   Always       -       95910010
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       23098h+88m+47.822s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3988711571
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1173346811

SMART Error Log Version: 1
ATA Error Count: 33 (device log contains only the most recent five errors)
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

Error 33 occurred at disk power-on lifetime: 5083 hours (211 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 6d 5f 06  Error: UNC at LBA = 0x065f6d77 = 106917239

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 58 6d 5f e6 00      01:58:12.859  READ DMA EXT
  25 00 00 58 6c 5f e6 00      01:58:12.780  READ DMA EXT
  35 00 10 b8 48 87 e4 00      01:58:12.732  WRITE DMA EXT
  35 00 10 10 41 87 e4 00      01:58:12.732  WRITE DMA EXT
  35 00 08 00 41 87 e4 00      01:58:12.732  WRITE DMA EXT

Error 32 occurred at disk power-on lifetime: 5083 hours (211 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 6d 5f 06  Error: UNC at LBA = 0x065f6d77 = 106917239

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 60 6d 5f e6 00      01:58:10.008  READ DMA EXT
  35 00 20 40 95 5c e4 00      01:58:10.006  WRITE DMA EXT
  25 00 20 40 6d 5f e6 00      01:58:10.006  READ DMA EXT
  35 00 20 20 95 5c e4 00      01:58:10.006  WRITE DMA EXT
  25 00 20 20 6d 5f e6 00      01:58:10.006  READ DMA EXT

Error 31 occurred at disk power-on lifetime: 5083 hours (211 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 6d 5f 06  Error: UNC at LBA = 0x065f6d77 = 106917239

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 58 6d 5f e6 00      01:58:04.375  READ DMA EXT
  25 00 00 58 6c 5f e6 00      01:58:04.364  READ DMA EXT
  35 00 08 48 a5 42 e0 00      01:58:04.140  WRITE DMA EXT
  35 00 09 50 a5 42 e0 00      01:58:04.139  WRITE DMA EXT
  35 00 03 10 c4 03 e0 00      01:58:04.135  WRITE DMA EXT

Error 30 occurred at disk power-on lifetime: 5083 hours (211 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 6d 5f 06  Error: UNC at LBA = 0x065f6d77 = 106917239

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 58 6d 5f e6 00      01:57:31.772  READ DMA EXT
  25 00 00 58 6c 5f e6 00      01:57:31.727  READ DMA EXT
  35 00 08 00 ef 3a e0 00      01:57:31.694  WRITE DMA EXT
  35 00 20 d0 ee 3a e0 00      01:57:31.694  WRITE DMA EXT
  ea 00 00 ff ff ff af 00      01:57:31.479  FLUSH CACHE EXT

Error 29 occurred at disk power-on lifetime: 5083 hours (211 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 77 6d 5f 06  Error: UNC at LBA = 0x065f6d77 = 106917239

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 60 6d 5f e6 00      01:57:28.755  READ DMA EXT
  35 00 20 a0 e3 5b e4 00      01:57:28.753  WRITE DMA EXT
  25 00 20 40 6d 5f e6 00      01:57:28.753  READ DMA EXT
  35 00 20 80 e3 5b e4 00      01:57:28.753  WRITE DMA EXT
  25 00 20 20 6d 5f e6 00      01:57:28.753  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      00%      8046         -
# 2  Extended offline    Interrupted (host reset)      00%      8046         -
# 3  Short offline       Completed without error       00%      4537         -
# 4  Extended offline    Aborted by host               90%      4537         -
# 5  Short offline       Completed without error       00%      4536         -
# 6  Short offline       Completed without error       00%      4536         -

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


``` If there is more data required please let me know

---

### Post by weatherman2 on 2014-11-29
Run the extended S.M.A.R.T. test with smartctl.  (GSmartControl is a much easier interface to smartctl, if you want to use the Gui instead of a terminal.)  Should take only about 90 minutes to run the extended test.  If it passes, maybe the hard drive isn't failing.  Your drive did report a lot of errors, but I have seen occasional errors like that that don't present a problem if they don't continue.  Still, you should ALWAYS setup regular backups for any hard drive, and I'd do them more often on a drive that is suspect like yours.

---

### Post by Mark Phelps on 2014-11-29
Don't mean to be an alarmist, but of all the hard drives and PCs I have, only two drives have failed me in recent history.  Both failed this year, both failed suddenly without any warnings at all -- and BOTH were Seagate Barracuda drives.

So, if I were you and I suspected a Seagate drive of failing, I would do whatever I could to back up the content I couldn't affort to lose to an external drive, or to a large USB stick.

---

### Post by tgalati4 on 2014-11-30
Is this a laptop or desktop?  You are getting a lot of correctable DMA (direct memory access) errors, which usually means a cable or power issue.  Make sure your machine is clean and the cables are properly seated.  Try changing cables if there is evidence of pinching or damage.  Check your power supply voltages, especially 12VDC while running.  Use a voltmeter or the BIOS health monitoring.

Uncorrectable errors (UNC's) are bad and usually indicate a failing disk surface or head problem--back up fast.

Back up regardless.

---

### Post by -@23%^yu* on 2015-03-30
Thanks. I took Backup of all the date and finally the drive's dead.

---

### Post by -@23%^yu* on 2015-03-30
It's a desktop. The dive failed.

---

