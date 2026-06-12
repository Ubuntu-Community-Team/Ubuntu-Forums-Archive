---
title: "Help with Gsmartcontrol/smartctl logs to detect problems of my hd"
date: 2017-06-14
forum: Hardware
---

### Post by hohihohihahaha on 2017-06-14
H&#304;,

I've searched for the errors but couldn't find anything useful and i'm a total beginner(used only octave etc for my work,i'm not capable of testing and figure out my pc's issues with commands by myself-so not much of a linux user-).That's why i'm asking for help;
does this log mean my hd needs a format(hd should be around 2.5 year old) or SATA controller can't communicate with hd(ATA error) ?
Btw i had to switch between windows-ubuntu several times,is that the reason of the problem now i'm facing?
In addition,i'm using ubuntu16.04 now and it's really slow(wasn't like this previous time),and 'Welcome to Emergency Mode!' was popping up after boot(time to time) and i just used ctrl-d to pass it.Besides whenever i transfer a file/folder to my flash drive,i'm facing input/output errors for some of the files lately.
I hope you help me with these problems or at least show me the source of my problem.

Thanks a lot in advance!

```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 117)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  105) seconds.
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
recommended polling time:      ( 119) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x1085)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   088   079   006    Pre-fail  Always       -       93285830
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3949
  5 Reallocated_Sector_Ct   0x0033   093   093   010    Pre-fail  Always       -       8464
  7 Seek_Error_Rate         0x000f   083   060   030    Pre-fail  Always       -       224261376
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       10835
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3929
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       13970
188 Command_Timeout         0x0032   100   096   000    Old_age   Always       -       2 9 26
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   060   045    Old_age   Always       -       30 (Min/Max 21/31)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       163
193 Load_Cycle_Count        0x0032   093   093   000    Old_age   Always       -       14161
194 Temperature_Celsius     0x0022   030   040   000    Old_age   Always       -       30 (0 13 0 0 0)
197 Current_Pending_Sector  0x0012   064   059   000    Old_age   Always       -       6056
198 Offline_Uncorrectable   0x0010   064   059   000    Old_age   Offline      -       6056
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       10930h+00m+55.684s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       32680313467
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2069075968094

SMART Error Log Version: 1
ATA Error Count: 13965 (device log contains only the most recent five errors)
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

Error 13965 occurred at disk power-on lifetime: 10835 hours (451 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 53 00 80 03 e9 00  Error: UNC at LBA = 0x00e90380 = 15270784

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 80 03 e9 e0 00      06:21:54.384  READ DMA
  e5 00 00 00 00 00 00 00      06:21:54.170  CHECK POWER MODE
  35 00 10 ff ff ff ef 00      06:21:54.169  WRITE DMA EXT
  35 00 08 ff ff ff ef 00      06:21:54.169  WRITE DMA EXT
  35 00 10 ff ff ff ef 00      06:21:54.169  WRITE DMA EXT

Error 13964 occurred at disk power-on lifetime: 10835 hours (451 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 53 00 80 03 e9 00  Error: UNC at LBA = 0x00e90380 = 15270784

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 80 03 e9 e0 00      06:21:50.001  READ DMA
  35 00 10 ff ff ff ef 00      06:21:50.001  WRITE DMA EXT
  35 00 10 ff ff ff ef 00      06:21:50.000  WRITE DMA EXT
  35 00 10 ff ff ff ef 00      06:21:50.000  WRITE DMA EXT
  35 00 10 ff ff ff ef 00      06:21:50.000  WRITE DMA EXT

Error 13963 occurred at disk power-on lifetime: 10835 hours (451 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 53 00 80 03 e9 00  Error: UNC at LBA = 0x00e90380 = 15270784

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 80 03 e9 e0 00      05:58:55.976  READ DMA
  35 00 10 ff ff ff ef 00      05:58:55.975  WRITE DMA EXT
  35 00 08 ff ff ff ef 00      05:58:55.974  WRITE DMA EXT
  35 00 08 ff ff ff ef 00      05:58:55.974  WRITE DMA EXT
  35 00 30 ff ff ff ef 00      05:58:55.974  WRITE DMA EXT

Error 13962 occurred at disk power-on lifetime: 10835 hours (451 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 53 00 80 03 e9 00  Error: UNC at LBA = 0x00e90380 = 15270784

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 80 03 e9 e0 00      05:58:51.892  READ DMA
  ea 00 00 00 00 00 a0 00      05:58:51.872  FLUSH CACHE EXT
  35 00 08 ff ff ff ef 00      05:58:51.872  WRITE DMA EXT
  ea 00 00 00 00 00 a0 00      05:58:51.098  FLUSH CACHE EXT
  35 00 28 ff ff ff ef 00      05:58:51.098  WRITE DMA EXT

Error 13961 occurred at disk power-on lifetime: 10835 hours (451 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 53 00 80 03 e9 00  Error: UNC at LBA = 0x00e90380 = 15270784

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 80 03 e9 e0 00      05:58:41.732  READ DMA
  35 00 08 ff ff ff ef 00      05:58:41.730  WRITE DMA EXT
  35 00 10 ff ff ff ef 00      05:58:41.729  WRITE DMA EXT
  35 00 08 ff ff ff ef 00      05:58:41.729  WRITE DMA EXT
  ef 10 02 00 00 00 a0 00      05:58:41.729  SET FEATURES [Enable SATA feature]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       50%     10835         15270784
# 2  Short offline       Completed: read failure       90%     10835         15270784
# 3  Extended offline    Completed: read failure       90%     10833         19836632
# 4  Short offline       Completed: read failure       90%     10830         15259728
# 5  Short offline       Completed: read failure       90%     10829         15259728
# 6  Extended offline    Completed: read failure       90%     10829         15259728

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

### Post by deadflowr on 2017-06-14
You need a new disk, plain and simple.
The reallocated sector count is huge,
As are the the current pending sector count and offline uncorrectable count.
All three of these are big indicators of a hard drive that could be at the end of it's life very soon.

While there is a very very slight chance it's more software related and that a complete wipe (we're talking low level wiping, which is more complex than a simple reformatting) may fix the issue.
The more likely outcome will be that the same problems and concerns will still be there as there are right now.

---

