---
title: "Dying harddrive?"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by Jimmy_r on 2006-09-29
Edgy started acting wierd a few days ago, at boot it would complain about bad filesystem structures and too large blocks and would not boot.
Well, i thought it was edgys fault so i installed dapper yesterday.
Today when i tried to open a gnome-terminal it complained about not able to execute binary.
Nothing wanted to work so i switched to another terminal and did a ctrl-alt-delete. I got the message: /sbin/shutdown:/sbin/shutdown: cannot execute binary file.
I did a hard reboot and was greeted with the grub message about bad filesystem structure.
I booted from a desktop cd and downloaded smartmontools. Here is the output:

```

ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda -d ata
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3160827AS
Serial Number:    4MT16VQD
Firmware Version: 3.42
User Capacity:    160&#65533;041&#65533;885&#65533;696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Fri Sep 29 09:22:44 2006 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed                                        without error or no self-test has ever
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
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  94) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   056   048   006    Pre-fail  Always       -       219020555
  3 Spin_Up_Time            0x0003   097   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       374
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   061   059   030    Pre-fail  Always       -       85926615308
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1258
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       692
194 Temperature_Celsius     0x0022   033   045   000    Old_age   Always       -       33 (Lifetime Min/Max 0/18)
195 Hardware_ECC_Recovered  0x001a   056   048   000    Old_age   Always       -       219020555
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   136   000    Old_age   Always       -       187
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1280 (device log contains only the most recent five errors)
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

Error 1280 occurred at disk power-on lifetime: 1258 hours (52 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 0f 39 00 00 e0  Error: ICRC, ABRT 15 sectors at LBA = 0x00000039 = 57

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 40 08 00 00 e0 00      00:02:09.623  READ DMA EXT
  25 00 08 00 00 00 e0 00      00:02:09.620  READ DMA EXT
  25 00 08 20 9d a1 e0 00      00:02:09.614  READ DMA EXT
  25 00 08 a0 9e a1 e0 00      00:02:09.574  READ DMA EXT
  25 00 08 b0 9d a1 e0 00      00:02:09.570  READ DMA EXT

Error 1279 occurred at disk power-on lifetime: 1258 hours (52 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 2e cf cb 82 e0  Error: ICRC, ABRT 46 sectors at LBA = 0x0082cbcf = 8571855

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 3f be cb 82 e0 00      00:00:37.604  READ DMA EXT
  25 00 3f 7f cb 82 e0 00      00:00:37.604  READ DMA EXT
  25 00 3f 40 cb 82 e0 00      00:00:37.603  READ DMA EXT
  25 00 3f 01 cb 82 e0 00      00:00:37.602  READ DMA EXT
  25 00 3f c2 ca 82 e0 00      00:00:37.601  READ DMA EXT

Error 1278 occurred at disk power-on lifetime: 1258 hours (52 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 1e 15 de 82 e0  Error: ICRC, ABRT 30 sectors at LBA = 0x0082de15 = 8576533

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 3f f4 dd 82 e0 00      00:00:28.067  READ DMA EXT
  25 00 3f b5 dd 82 e0 00      00:00:28.066  READ DMA EXT
  25 00 3f 76 dd 82 e0 00      00:00:28.066  READ DMA EXT
  25 00 3f 37 dd 82 e0 00      00:00:28.065  READ DMA EXT
  25 00 3f f8 dc 82 e0 00      00:00:28.065  READ DMA EXT

Error 1277 occurred at disk power-on lifetime: 1258 hours (52 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 53 c6 82 e0  Error: ICRC, ABRT at LBA = 0x0082c653 = 8570451

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 3f 15 c6 82 e0 00      00:00:25.969  READ DMA EXT
  25 00 3f d6 c5 82 e0 00      00:00:25.969  READ DMA EXT
  25 00 3f 97 c5 82 e0 00      00:00:25.968  READ DMA EXT
  25 00 3f 58 c5 82 e0 00      00:00:25.976  READ DMA EXT
  25 00 3f 19 c5 82 e0 00      00:00:25.975  READ DMA EXT

Error 1276 occurred at disk power-on lifetime: 1258 hours (52 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 a6 c1 82 e0  Error: ICRC, ABRT at LBA = 0x0082c1a6 = 8569254

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 3f 68 c1 82 e0 00      00:00:15.077  READ DMA EXT
  25 00 3f 29 c1 82 e0 00      00:00:15.077  READ DMA EXT
  25 00 3f ea c0 82 e0 00      00:00:15.076  READ DMA EXT
  25 00 3f ab c0 82 e0 00      00:00:15.076  READ DMA EXT
  25 00 3f 6c c0 82 e0 00      00:00:15.075  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       424         -

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

Does it look like the harddrive is dying? Is there some other command to find out? 
The hdd is fairly new so i find it odd that it would die.
Or could it be edgys fault? A virus?
If nothing is wrong with the harddrive i think i will try a zero-fill and install windows, to test if the error appear there as well.

---

