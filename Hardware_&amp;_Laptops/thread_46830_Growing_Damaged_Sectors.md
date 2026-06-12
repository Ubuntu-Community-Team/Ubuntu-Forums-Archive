---
title: "Growing Damaged Sectors"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by larry on 2005-07-06
Dear All,
Some time ago I posted a thread in which similar to this one. Roughly every 30-40 mounts, Ubuntu check the hard drive for errors.
This is the output of df -h to let you have an idea of the partitioning of my disk:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              38G  3.1G   33G   9% /
tmpfs                 284M     0  284M   0% /dev/shm
/dev                   38G  3.1G   33G   9% /.dev
none                  5.0M  2.8M  2.3M  55% /dev

Ubuntu checks /hda1 and every time it does it finds some damaged sectors (it started with about 1.2%, but now it detects 2% of non-contiguous damaged sectors).
Some people in the forum told me that it is nothing to worry about, but other friends of mine who use Linux keep on saying it is likely to be a hardware problem due to the hard disk which is about to crash.
Anybody comes forward with a hint/suggestion?
Cheers
Larry

---

### Post by nocturn on 2005-07-06
You can try the smart utilities (in universe) to see if there are errors.

---

### Post by larry on 2005-07-06
Thanks for your advice. Could you be a bit more specific about the previse utility to use?
I looked in the repositories for "smart utilities" but I ended up with smart card utilities (I allowed universe and multiverse).
Cheers
Larry

---

### Post by nocturn on 2005-07-06
You will need smartmontools.  These utils allow you to query IDE drives that support SMART (self monitoring and something).

---

### Post by larry on 2005-07-06
Thanks again. I installed the packages, but they do not seem (to me) to work smoothly. For instance, I tried to perform a long test using:

larry@ubuntu:~ $ sudo smartctl -t long /dev/hda1
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 17 minutes for test to complete.
Test will complete after Wed Jul  6 17:08:00 2005

Use smartctl -X to abort test.

Immediately afterwards the prompt was as if the command had been completed. but nothing happened after the 17 minutes...I did not see any log in the directory where I was.

I also tried to print out the results from the previous test using the -a option.
I attach the very long output (sorry for its length).
The main point for me (seen that quite many errors are found) is simply to find out whether there is anything I can do to straighten them up or I have to buy some new hardware.
Cheers
Larry




larry@ubuntu:~ $ sudo  smartctl -a -t long /dev/hda1
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     Maxtor 6E040L0
Serial Number:    E11DWHFE
Firmware Version: NAR61590
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Wed Jul  6 18:09:09 2005 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 247) Self-test routine in progress...
                                        70% of test remaining.
Total time to complete Offline
data collection:                 (1021) seconds.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  17) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   222   221   063    Pre-fail  Always       -       11265
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       1587
  5 Reallocated_Sector_Ct   0x0033   252   252   063    Pre-fail  Always       -       7
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   246   246   187    Pre-fail  Always       -       38526
  9 Power_On_Minutes        0x0032   243   243   000    Old_age   Always       -       301h+29m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   249   249   000    Old_age   Always       -       1608
192 Power-Off_Retract_Count 0x0032   252   252   000    Old_age   Always       -       1568
193 Load_Cycle_Count        0x0032   252   252   000    Old_age   Always       -       5199
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       51
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       11305
196 Reallocated_Event_Count 0x0008   251   251   000    Old_age   Offline      -       2
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       1
198 Offline_Uncorrectable   0x0008   253   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       14
202 TA_Increase_Count       0x000a   253   232   000    Old_age   Always       -       1
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       24
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   184   184   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 207 inconsistent with error log pointer 5

ATA Error Count: 207 (device log contains only the most recent five errors)
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

Error 207 occurred at disk power-on lifetime: 3345 hours (139 days + 9 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0b 3f 11 54 e4  Error: UNC 11 sectors at LBA = 0x0454113f = 72618303

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 10 3f 11 54 e4 08      00:35:51.200  READ DMA
  c8 00 18 37 11 54 e4 08      00:35:49.888  READ DMA
  c8 00 20 2f 11 54 e4 08      00:35:48.560  READ DMA
  c8 00 28 27 11 54 e4 08      00:35:47.248  READ DMA
  c8 00 30 1f 11 54 e4 08      00:35:45.936  READ DMA

Error 206 occurred at disk power-on lifetime: 3345 hours (139 days + 9 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0b 37 11 54 e4  Error: UNC 11 sectors at LBA = 0x04541137 = 72618295

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 18 37 11 54 e4 08      00:35:49.888  READ DMA
  c8 00 20 2f 11 54 e4 08      00:35:48.560  READ DMA
  c8 00 28 27 11 54 e4 08      00:35:47.248  READ DMA
  c8 00 30 1f 11 54 e4 08      00:35:45.936  READ DMA
  c8 00 38 17 11 54 e4 08      00:35:44.608  READ DMA

Error 205 occurred at disk power-on lifetime: 3345 hours (139 days + 9 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0b 2f 11 54 e4  Error: UNC 11 sectors at LBA = 0x0454112f = 72618287

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 2f 11 54 e4 08      00:35:48.560  READ DMA
  c8 00 28 27 11 54 e4 08      00:35:47.248  READ DMA
  c8 00 30 1f 11 54 e4 08      00:35:45.936  READ DMA
  c8 00 38 17 11 54 e4 08      00:35:44.608  READ DMA
  c8 00 40 0f 11 54 e4 08      00:35:43.296  READ DMA

Error 204 occurred at disk power-on lifetime: 3345 hours (139 days + 9 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0b 27 11 54 e4  Error: UNC 11 sectors at LBA = 0x04541127 = 72618279

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 28 27 11 54 e4 08      00:35:47.248  READ DMA
  c8 00 30 1f 11 54 e4 08      00:35:45.936  READ DMA
  c8 00 38 17 11 54 e4 08      00:35:44.608  READ DMA
  c8 00 40 0f 11 54 e4 08      00:35:43.296  READ DMA
  c8 00 48 07 11 54 e4 08      00:35:41.984  READ DMA

Error 203 occurred at disk power-on lifetime: 3345 hours (139 days + 9 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0b 1f 11 54 e4  Error: UNC 11 sectors at LBA = 0x0454111f = 72618271

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 30 1f 11 54 e4 08      00:35:45.936  READ DMA
  c8 00 38 17 11 54 e4 08      00:35:44.608  READ DMA
  c8 00 40 0f 11 54 e4 08      00:35:43.296  READ DMA
  c8 00 48 07 11 54 e4 08      00:35:41.984  READ DMA
  c8 00 50 ff 10 54 e4 08      00:35:40.656  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%      3353         13864
# 2  Extended offline    Completed: read failure       40%      3353         13863
# 3  Extended offline    Completed: read failure       40%      3353         13863
# 4  Extended offline    Completed: read failure       40%      3352         -

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

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 17 minutes for test to complete.
Test will complete after Wed Jul  6 18:26:10 2005

Use smartctl -X to abort test.

---

### Post by nocturn on 2005-07-07
What is the output of:
smartctl -l selftest /dev/hda

Note, for this type off operation, always use the whole device (hda) instead of partitions.

---

### Post by larry on 2005-07-07
Hi,
I tried your suggestion. The test ends quickly with what again looks like an error message:

larry@ubuntu:~ $ sudo smartctl -l selftest /dev/hda
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       30%      3354         35913784
# 2  Extended offline    Completed: read failure       40%      3353         13864
# 3  Extended offline    Completed: read failure       40%      3353         13863
# 4  Extended offline    Completed: read failure       40%      3353         13863
# 5  Extended offline    Completed: read failure       40%      3352         -

Do you know what it means? I am not very experienced with linux yet...
Cheers
Larry

---

### Post by nocturn on 2005-07-07
It is definately bad.

Can you try to download and run the PowerMax utilities from Maxtor?  
They maybe can reallocate data to non affected sectors and give a better indication of what is worng.

Is this drive still under warranty?

---

### Post by Jussi Kukkonen on 2005-07-07
I looked at your first error log and while I don't know what the errors are about, they don't look that bad -- all are from the same time. Maybe the electricity went down or something...

*smartcl -l selftest* only prints the selftest logs that the drive itself keeps, that's why it's fast. The log says it has started 5 offline tests (all within two hours), but it seems they have not finished...

You might want to find out what files those bad sectors affect:
[http://smartmontools.sourceforge.net/BadBlockHowTo.txt](http://smartmontools.sourceforge.net/BadBlockHowTo.txt)

---

### Post by larry on 2005-07-07
Thanks to both of you. I still have a few questions:
1) I am going through the procedure in [http://smartmontools.sourceforge.net/BadBlockHowTo.txt](http://smartmontools.sourceforge.net/BadBlockHowTo.txt)

larry@ubuntu:~ $ sudo smartctl -l selftest /dev/hda
Password:
smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       30%      3354         35913784
# 2  Extended offline    Completed: read failure       40%      3353         13864
# 3  Extended offline    Completed: read failure       40%      3353         13863
# 4  Extended offline    Completed: read failure       40%      3353         13863
# 5  Extended offline    Completed: read failure       40%      3352         -


Now how do I exactly estimate the value of LBA to input in the formula reported in the site?
2) Again I do not find exactly the name of the packages required to deal with the Maxtor. No piece of my PC is under warranty yet...it is too old!
Best Regards

Larry

---

### Post by nocturn on 2005-07-07
On [www.maxtor.com](www.maxtor.com), worldwide support, software downloads.
Select ATA drives, and hte PowerMax Iso image.

This you have to burn to CD and boot with it, it can diagnose your drive.

---

