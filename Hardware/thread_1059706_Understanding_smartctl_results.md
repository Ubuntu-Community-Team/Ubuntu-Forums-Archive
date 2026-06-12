---
title: "Understanding smartctl results"
date: 2009-02-04
forum: Hardware
---

### Post by dargaud on 2009-02-04
Hello all,
I have a drive that produces a violent click every once in a while. But I have 3 drives in the box... In order to figure out which one is having those seizures, I ran smartctl but I can't make sense of the results. Can anyone give me a hand in interpreting them, thanks ?
```

$ sudo smartctl -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                               

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST31000340AS             
Serial Number:    9QJ0JKD6                 
Firmware Version: SD15                     
User Capacity:    1,000,204,886,016 bytes  
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8                                              
ATA Standard is:  ATA-8-ACS revision 4                           
Local Time is:    Wed Feb  4 08:46:54 2009 CET                   
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
data collection:                 ( 634) seconds.                                
Offline data collection                                                         
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 224) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103b) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       148264600
  3 Spin_Up_Time            0x0003   096   084   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1118
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   037   036   030    Pre-fail  Always       -       10810444186323
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4534
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       2
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       43
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   057   045    Old_age   Always       -       34 (Lifetime Min/Max 33/35)
194 Temperature_Celsius     0x0022   034   043   000    Old_age   Always       -       34 (0 16 0 0)
195 Hardware_ECC_Recovered  0x001a   037   030   000    Old_age   Always       -       148264600
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        87         -
# 2  Short offline       Completed without error       00%        84         -

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

```

$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                               

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST31000340AS             
Serial Number:    9QJ0KJ4Q                 
Firmware Version: SD15                     
User Capacity:    1,000,204,886,016 bytes  
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8                                              
ATA Standard is:  ATA-8-ACS revision 4                           
Local Time is:    Wed Feb  4 08:47:59 2009 CET                   
SMART support is: Available - device has SMART capability.       
SMART support is: Enabled                                        

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.    
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever  
                                        been run.                               
Total time to complete Offline                                                  
data collection:                 ( 642) seconds.                                
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 237) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103b) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       68229181
  3 Spin_Up_Time            0x0003   096   086   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       249
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   069   055   030    Pre-fail  Always       -       17213928688
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4572
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       1
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       47
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       4295032833
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   040   032   045    Old_age   Always   FAILING_NOW 60 (123 109 61 60)
194 Temperature_Celsius     0x0022   060   068   000    Old_age   Always       -       60 (0 40 0 0)
195 Hardware_ECC_Recovered  0x001a   041   033   000    Old_age   Always       -       68229181
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       121         -
# 2  Short offline       Completed without error       00%       117         -

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

```

$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/                               

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K400 series
Device Model:     HDS724040KLAT80              
Serial Number:    KRFA01RAG1RN5A               
Firmware Version: KFAOA32A                     
User Capacity:    400,088,457,216 bytes        
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7                                              
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1               
Local Time is:    Wed Feb  4 08:48:23 2009 CET                   
SMART support is: Available - device has SMART capability.       
SMART support is: Enabled                                        

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x04) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Disabled.            
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (9120) seconds.
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
recommended polling time:        ( 152) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   158   158   050    Pre-fail  Offline      -       212
  3 Spin_Up_Time            0x0007   176   176   034    Pre-fail  Always       -       409 (Average 385)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       245
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   136   136   020    Pre-fail  Offline      -       31
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       1591
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       235
192 Power-Off_Retract_Count 0x0032   100   100   050    Old_age   Always       -       302
193 Load_Cycle_Count        0x0012   100   100   050    Old_age   Always       -       302
194 Temperature_Celsius     0x0002   177   177   000    Old_age   Always       -       31 (Lifetime Min/Max 6/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       2

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
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

### Post by Endolith on 2009-04-10
I just discovered [GSmartControl]("http://gsmartcontrol.berlios.de/home/index.php/en/Home"), which puts a GUI on smartctl.  When you hover over things like "Reported_Uncorrect", it gives a much more helpful description in a tooltip about what the value means.

[Wikipedia has a lot of similar descriptions]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology#Known_ATA_S.M.A.R.T._attributes").

---

