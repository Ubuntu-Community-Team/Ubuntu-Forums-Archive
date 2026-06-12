---
title: "checking the status of the HDD"
date: 2013-09-09
forum: Hardware
---

### Post by micahpage on 2013-09-09
Recently my HDD starting making loud noises. I blow the internals out quite often to clean it from dust, and the noise is surely coming from the HDD. Its not clicking noises, but sounds like writing/reading, but just more loud than normal. Loud enough where if people are in the room, they ask what that noise is. 

The HDD is the internal default that came with the computer. It's about 2 years old. The Desktop however is always on. I have it hooked up to my TV via HDMI, but i use the TV data from my 3TB external HDD, not the internal for reading data constantly. 

*I have had an external Seagate before and it died quite early*, so i am not fond of Seagates anymore. My external is Western Digital, and i have never had a problem with those. It's weird that Seagate are more expensive but seem to last far less than WD. So i am trying to find out whether i need to cough up the money to buy a new HDD. I am not too concerned about saving data, as i would just re-install Ubuntu on a new HDD if this one fails and i didn't have a backup. Plus most important data is saved at numerous places. So it could die tonight and i would be like whatever, for the exception of me having to buy a new one. But i was trying to avoid having to buy a new one if i didnt have to. 

I am not sure what smartctl is or does, or if its the best method, but i came across:
I am not sure what these results even mean?

```
micahpage@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.8.0-19-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP72AWX
LU WWN Device Id: 5 000c50 02ef374f1
Firmware Version: CC44
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Sep  9 14:26:19 2013 EDT
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
data collection:         (  609) seconds.
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
recommended polling time:      ( 197) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103b)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       155502843
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       352
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   080   060   030    Pre-fail  Always       -       106745027
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       17151
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       352
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       52
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   068   057   045    Old_age   Always       -       32 (Min/Max 20/36)
194 Temperature_Celsius     0x0022   032   043   000    Old_age   Always       -       32 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   035   024   000    Old_age   Always       -       155502843
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       239822383892032
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2624327024
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1667912705

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
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by bernard2 on 2013-09-10
I've had a lot of Seagate drives and have had very little trouble with them ... but I guess that's just the luck of the draw.

Another - friendlier - way of getting info about a disk status is to use "Disk Utility" which you should be able to find on your system, it has a GUI.

As for what all the numbers mean - well, some of them are worryingly high but, then again, some of them are stupidly (implausibly) high and I'm never entirely confident about trusting the numbers I see in these reports. For example, your disk appears to have been running for longer than the known age of the universe ...

At the end of the day, if the disk is making graunching noises then it is about to die, no question. I'd trust my ear if I were you!

---

