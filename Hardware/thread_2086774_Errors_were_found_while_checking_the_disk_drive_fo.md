---
title: "Errors were found while checking the disk drive for /"
date: 2012-11-21
forum: Hardware
---

### Post by yma981 on 2012-11-21
Hello 

I am experiencing some weird behavior, sometimes unexpectedly and randomly my Hard Disk becomes Read-Only, I can't write anything on the disk. 

When booting i am getting the following message:

"Errors were found while checking the disk drive for /

Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for Manual recovery."

And after that the boot sequence tells me that tmp/ isn't accessible

Sometimes when i restart the Laptop it acts normally with read and write capabilities...

Any idea what is happening? Is my HDD dying or what? is there a specific log i can check for errors?? Any idea?

10x

---

### Post by ahallubuntu on 2012-11-21
~

---

### Post by skart88 on 2013-05-28
Hi I had today the same errors, I follows what  you have said to fix it, and finally I run smartctl -a dev/sda.
I quote the terminal result>>
 
> [FONT=courier new]smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-44-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS547564A9E384
Serial Number:    J2180053EYLZ5D
LU WWN Device Id: 5 000cca 63ee9a4fe
Firmware Version: JEDOA50A
User Capacity:    640,135,028,736 bytes [640 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Tue May 28 11:24:12 2013 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   45) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 178) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0025   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0023   172   100   033    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       464
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       570
 10 Spin_Retry_Count        0x0033   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       462
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       42950656000
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   053   045    Old_age   Always       -       36 (Min/Max 35/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       102
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       786444
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       6611
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x002a   100   100   000    Old_age   Always       -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]




SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/FONT]

Is it good? How do you think it?

---

