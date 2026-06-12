---
title: "Filesystem Corruption apparantly cause by Chrom(e/ium)"
date: 2013-05-10
forum: Hardware
---

### Post by rekh127 on 2013-05-10
This weekend I upgraded to 13.04. I started getting file system corruption, which in turn caused the file system to be mounted read only. It was happening everytime I boot up, and required fixing with fsck. I tried all sorts of things trying to fix it. Reinstalling disabling NCQ, etc. Nothing worked, but there was a few times it didn't seem to pop up as quikly, and I started trying to figure out what's wrong with it. Long story short it seems to be caused by Chrom(e/ium). Badblocks and my drives smartdata show now problems, memory test was clean. I don't get it in my windows partition either, which seems to confirm that it's not a hardware failure. Within a few minutes of using chrome or chromium (both stable versions) the file system goes readonly, doesn't seem to happen with any other program. Does anyone have any ideas on a more specific cause or a way to get more data to be useful for a bug report?

P.S. I hope this is the right forum, if not could a mod move it for me?

---

### Post by matt_symes on 2013-05-10
Hi

Please post your smart data here and also any relevent sections of /var/log/syslog and ~/.xsession-errors.

Kind regards.

---

### Post by rekh127 on 2013-05-13
Thank you for your swift reply, sorry mine is delayed. 

Smart Data:
> ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       74138292
  3 Spin_Up_Time            0x0002   099   098   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   096   096   000    Pre-fail  Always       -       4179
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       84951358
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5062
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   098   098   020    Pre-fail  Always       -       3027
183 Runtime_Bad_Block       0x0032   100   253   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       4
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   048   044   045    Old_age   Always   In_the_past 52 (0 3 55 23 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       460
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       70
193 Load_Cycle_Count        0x0032   057   057   000    Old_age   Always       -       87743
194 Temperature_Celsius     0x0022   052   056   000    Old_age   Always       -       52 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   052   052   000    Old_age   Always       -       74138292
196 Reallocated_Event_Count 0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

I didn't see anything really relevant in the logs, but I could just not know what I'm looking for.

---

### Post by tgalati4 on 2013-05-13
I presume that this doesn't happen with firefox?  Chrome writes lots of small cache files as a way of separating (jailing) tabs.  You can clear the cache in settings and see if that changes the behavior.  I would switch to firefox or opera in the meantime.

There is usually more SMART data.  Open a terminal:

```
sudo smartctl -a /dev/sda
```

---

### Post by rekh127 on 2013-05-13
No it doesn't happen in firefox. I'll try chromium with the cache cleared later tonight and let you know what happens.

I thought that was the only relevant portion. I'll post the rest

> === START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.6
Device Model:     ST9320325AS
Serial Number:    6VDA240H
LU WWN Device Id: 5 000c50 032d31b25
Firmware Version: 0005HPM1
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon May 13 14:03:53 2013 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
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
recommended polling time:      (  97) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006    Pre-fail  Always       -       85508472
  3 Spin_Up_Time            0x0002   099   098   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   096   096   000    Pre-fail  Always       -       4179
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       84976410
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5063
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   098   098   020    Pre-fail  Always       -       3027
183 Runtime_Bad_Block       0x0032   100   253   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       4
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   048   044   045    Old_age   Always   In_the_past 52 (0 3 55 23 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       460
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       70
193 Load_Cycle_Count        0x0032   057   057   000    Old_age   Always       -       87743
194 Temperature_Celsius     0x0022   052   056   000    Old_age   Always       -       52 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   053   052   000    Old_age   Always       -       85508472
196 Reallocated_Event_Count 0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5062         -
# 2  Extended offline    Aborted by host               90%      4993         -
# 3  Short offline       Completed without error       00%      4993         -
# 4  Short offline       Aborted by host               80%      2053         -
# 5  Short offline       Completed without error       00%       291         -
# 6  Short offline       Completed without error       00%        11         -
# 7  Short offline       Completed without error       00%        11         -
# 8  Short offline       Completed without error       00%        10         -
# 9  Short offline       Completed without error       00%         9         -
#10  Short offline       Completed without error       00%         9         -
#11  Short offline       Completed without error       00%         8         -
#12  Short offline       Completed without error       00%         7         -
#13  Short offline       Completed without error       00%         7         -
#14  Short offline       Completed without error       00%         6         -
#15  Short offline       Completed without error       00%         5         -
#16  Short offline       Completed without error       00%         5         -
#17  Short offline       Completed without error       00%         4         -
#18  Short offline       Completed without error       00%         4         -
#19  Short offline       Completed without error       00%         3         -
#20  Short offline       Completed without error       00%         2         -
#21  Short offline       Completed without error       00%         2         -

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

### Post by tgalati4 on 2013-05-13
Your SMART parameters look OK.  The last short test was performed at 5,062 hours.  No errors have been logged.  So now we look at Chrome.  What version of chrome?  Did you perform any chrome updates recently?  It could be a faulty install of chrome.  Try removing it completely and reinstall.  Are you running 32-bit or 64-bit?

---

### Post by rekh127 on 2013-05-13
Clearing the cache seems to have fixed it, I'd like to see if we can'tfigure out what might have caused it though. 

I'm on 64 bit. The problem was occuring with installs of Chrome stable and the Chromium version in the raring repositories, the installs were fresh but the profiles had been carried over from the same version of chrome on my 12.04 install which was running fine.

---

