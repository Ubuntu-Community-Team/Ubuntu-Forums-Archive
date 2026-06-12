---
title: "SmartCtl Results....OK, or time for a new one??"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by JungMin on 2007-07-29
I am running Feisty......My system is a server for the house, so it is always on.  I woke up this morning to a blank screen.  Tried to reboot but it said something like "No disk found".  Rebooted again and it said "Hard drive failure".   I was freaking out a bit.....So I took the hard drive out and stuck it in the freezer for 1/2 hour incase it was too hot.  Put it back in the computer and all is fine.  Backed up all 450GB to a new drive i just bought.

Havent had any errors since that blank screen, or any errors any other time.  I ran SMARTCTL on the drive and this is what i get:

```
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3500630A
Serial Number:    5QG1HBXY
Firmware Version: 3.AAF
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Jul 29 14:29:33 2007 KST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 163) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       71259358
  3 Spin_Up_Time            0x0003   096   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       42
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       65343164
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2242
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       44
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Unknown_Attribute       0x0022   061   048   045    Old_age   Always       -       689897511
194 Temperature_Celsius     0x0022   039   052   000    Old_age   Always       -       39 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   060   057   000    Old_age   Always       -       217539244
197 Current_Pending_Sector  0x0012   001   001   000    Old_age   Always       -       4294967295
198 Offline_Uncorrectable   0x0010   001   001   000    Old_age   Offline      -       4294967295
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 16 (device log contains only the most recent five errors)
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

Error 16 occurred at disk power-on lifetime: 2227 hours (92 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d7 c1 01 e0  Error: UNC 128 sectors at LBA = 0x0001c1d7 = 115159

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 d7 c1 01 e0 00      00:00:52.326  READ DMA EXT
  25 00 88 cf c1 01 e0 00      00:00:50.441  READ DMA EXT
  25 00 90 c7 c1 01 e0 00      00:00:48.555  READ DMA EXT
  25 00 98 bf c1 01 e0 00      00:00:46.670  READ DMA EXT
  25 00 a0 b7 c1 01 e0 00      00:00:44.784  READ DMA EXT

Error 15 occurred at disk power-on lifetime: 2227 hours (92 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d7 c1 01 e0  Error: UNC at LBA = 0x0001c1d7 = 115159

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 88 cf c1 01 e0 00      00:00:52.326  READ DMA EXT
  25 00 90 c7 c1 01 e0 00      00:00:50.441  READ DMA EXT
  25 00 98 bf c1 01 e0 00      00:00:48.555  READ DMA EXT
  25 00 a0 b7 c1 01 e0 00      00:00:46.670  READ DMA EXT
  25 00 a8 af c1 01 e0 00      00:00:44.784  READ DMA EXT

Error 14 occurred at disk power-on lifetime: 2227 hours (92 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d7 c1 01 e0  Error: UNC at LBA = 0x0001c1d7 = 115159

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 90 c7 c1 01 e0 00      00:00:52.326  READ DMA EXT
  25 00 98 bf c1 01 e0 00      00:00:50.441  READ DMA EXT
  25 00 a0 b7 c1 01 e0 00      00:00:48.555  READ DMA EXT
  25 00 a8 af c1 01 e0 00      00:00:46.670  READ DMA EXT
  25 00 b0 a7 c1 01 e0 00      00:00:44.784  READ DMA EXT

Error 13 occurred at disk power-on lifetime: 2227 hours (92 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d7 c1 01 e0  Error: UNC at LBA = 0x0001c1d7 = 115159

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 bf c1 01 e0 00      00:00:52.326  READ DMA EXT
  25 00 a0 b7 c1 01 e0 00      00:00:50.441  READ DMA EXT
  25 00 a8 af c1 01 e0 00      00:00:48.555  READ DMA EXT
  25 00 b0 a7 c1 01 e0 00      00:00:46.670  READ DMA EXT
  25 00 b8 9f c1 01 e0 00      00:00:44.784  READ DMA EXT

Error 12 occurred at disk power-on lifetime: 2227 hours (92 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 d7 c1 01 e0  Error: UNC at LBA = 0x0001c1d7 = 115159

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 a0 b7 c1 01 e0 00      00:00:52.326  READ DMA EXT
  25 00 a8 af c1 01 e0 00      00:00:50.441  READ DMA EXT
  25 00 b0 a7 c1 01 e0 00      00:00:48.555  READ DMA EXT
  25 00 b8 9f c1 01 e0 00      00:00:46.670  READ DMA EXT
  25 00 c0 97 c1 01 e0 00      00:00:44.784  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      2242         -
# 2  Extended offline    Aborted by host               90%      2240         -

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

There are a few errors there, i ran a few different tests and those errors are the ones that just happened.  So then i ran the extended test...took 2.5 hours.  It says at the bottom there that it "Completed without error".

SO, is my drived toasted??  or was it something not to worry about??  A lot of the stuff there doesnt mean too much to me.....Some stuff says "Old Age' or "Pre-Fail".  I ran the test on the brand new drive and it says "old-age' and 'pre-fail' on it too???

Anyways....anyone familiar with smartctl results??  What do ya think??

---

### Post by JungMin on 2007-07-29
It seems to be ok now......But not sure if the test results mean imminent failure.

---

