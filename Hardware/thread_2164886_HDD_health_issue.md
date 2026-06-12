---
title: "HDD health issue"
date: 2013-08-02
forum: Hardware
---

### Post by kav120 on 2013-08-02
Hello people,

I have a one year old dell laptop and when I perform a startup check (dell's stuff), it gives and hdd error, so i decided to get information about my hdd health from OS. I ran ```
sudo smartctl -a /dev/sda | less
``` command and it game me 

```
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-26-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6
Device Model:     ST9500325AS
Serial Number:    5VES9WBZ
LU WWN Device Id: 5 000c50 049699619
Firmware Version: D005DEM1
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Aug  2 10:11:08 2013 GST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x73) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.

SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 134) minutes.
Conveyance self-test routine
recommended polling time:        (   3) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   091   006    Pre-fail  Always       -       155744204
  3 Spin_Up_Time            0x0003   099   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2073
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       71436241
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2782
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1952
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       - 
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   043   045    Old_age   Always   In_the_past 39 (0 15 39 38 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       110
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       122
193 Load_Cycle_Count        0x0032   091   091   000    Old_age   Always       -       19330
194 Temperature_Celsius     0x0022   039   057   000    Old_age   Always       -       39 (0 13 0 0 0)
195 Hardware_ECC_Recovered  0x001a   052   046   000    Old_age   Always       -       155744204
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       3
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -      1
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       135364484270756
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3830158476
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       40434943
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1099 (device log contains only the most recent five errors)
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

Error 1099 occurred at disk power-on lifetime: 2310 hours (96 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:27:54.820  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:54.818  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:54.817  READ FPDMA QUEUED
  60 00 30 e0 c5 66 4d 00      00:27:54.767  READ FPDMA QUEUED
  60 00 40 a0 c5 66 4d 00      00:27:54.762  READ FPDMA QUEUED

Error 1098 occurred at disk power-on lifetime: 2310 hours (96 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:27:51.953  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:51.953  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:51.953  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:51.951  READ FPDMA QUEUED
  ea 00 00 00 00 00 00 00      00:27:51.918  FLUSH CACHE EXT

Error 1097 occurred at disk power-on lifetime: 2310 hours (96 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:27:40.639  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:40.639  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:40.638  READ FPDMA QUEUED
  60 00 58 b0 31 79 4e 00      00:27:40.626  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:27:40.625  READ FPDMA QUEUED

Error 1096 occurred at disk power-on lifetime: 2310 hours (96 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:27:35.968  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:35.968  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:35.967  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:27:35.967  READ FPDMA QUEUED
  60 00 20 40 66 7c 4d 00      00:27:35.966  READ FPDMA QUEUED

Error 1095 occurred at disk power-on lifetime: 2310 hours (96 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:24:10.538  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:24:10.538  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:24:10.538  READ FPDMA QUEUED
  61 00 20 ff ff ff 4f 00      00:24:10.537  WRITE FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:24:10.523  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      2499         773820463
# 2  Short offline       Completed: read failure       90%      2499         773820463
# 3  Short offline       Completed: read failure       90%      2487         773820463
# 4  Extended offline    Completed: read failure       90%      2481         773820463
# 5  Short offline       Completed: read failure       90%      2481         773820463
# 6  Short offline       Completed: read failure       90%      1592         773820463
# 7  Short offline       Completed: read failure       90%      1229         753218749
# 8  Short offline       Completed: read failure       90%      1229         753218749
# 9  Short offline       Completed: read failure       90%      1226         753218749
#10  Short offline       Completed: read failure       90%      1226         753218749
#11  Short offline       Completed without error       00%      1154         -
#12  Short offline       Completed without error       00%      1121         -
#13  Short offline       Completed without error       00%       796         -
#14  Short offline       Completed without error       00%       773         -
#15  Short offline       Completed without error       00%       271         -
#16  Short offline       Completed without error       00%       187         -
#17  Short offline       Completed without error       00%        53         -
#18  Short offline       Completed without error       00%         1         -

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

Something like this. Can you comment on these errors. Is my hdd about to die? Should I backup my data?

Thanks in advance

---

### Post by w1ll1am on 2013-08-02
I am not sure what all of that information means I am sure someone will have more information but you shouldn't get any errors so something is wrong. An of course you should back up your data always backup just in case!

---

### Post by tgalati4 on 2013-08-02
Your disk has a few issues:

# 1  Short offline       Completed: read failure       90%      2499         773820463
# 2  Short offline       Completed: read failure       90%      2499         773820463
# 3  Short offline       Completed: read failure       90%      2487         773820463
# 4  Extended offline    Completed: read failure       90%      2481         773820463
# 5  Short offline       Completed: read failure       90%      2481         773820463
# 6  Short offline       Completed: read failure       90%      1592         773820463
# 7  Short offline       Completed: read failure       90%      1229         753218749
# 8  Short offline       Completed: read failure       90%      1229         753218749
# 9  Short offline       Completed: read failure       90%      1226         753218749
#10  Short offline       Completed: read failure       90%      1226         753218749

At 1226 hours you got a read error at 10% of the disk.  At 1592 and 2481 hours you got another read error at 10% of the disk, but at a different Logical Block Address (LBA).  As long as these errors don't increase in time, you can still use the disk, but be more aggressive in your backup strategy.  It's not clear from your output if the disk surface has defects or if the drive mechanism has worn spots that is causing these errors.

After performing a backup of your personal data, run *badblocks* and see how many blocks are unreadable.

---

### Post by bwallum on 2013-08-02
It looks as though the drive overheated at some point. This is very common with laptops, people will take them to bed, lay in a douve or such like and generally block up the ventilation. Look for an intermittent fault in your cpu and possible ram dimms too. It seems to be very well used for a year old. All things considered I would get a SSD which would greatly improve performance and run a lot cooler. If you are fortunate enough to have a dual drive bay then you could use the SSD for your Home drive (protects your data) whilst you continue to use your HDD for the system drive.

---

### Post by kav120 on 2013-08-03
I don't think it overheated but I had an issue with power supply adapter (it worked but didn't charge, so I had to get a new one). It seemed like adapter had internal problems. Could it cause these problems? BTW, I have tested with memtester and it seems RAM is OK

---

