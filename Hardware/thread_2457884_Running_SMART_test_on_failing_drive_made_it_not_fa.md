---
title: "Running SMART test on failing drive made it not failing anymore??"
date: 2021-02-11
forum: Hardware
---

### Post by &amp;KyT$0P# on 2021-02-11
I noticed in the gnome-disk-utility that an old HDD I'm not using much anymore was colored red.  Clicking it it said the disk was likely to fail soon.  [FONT=Courier New]smartctl -a[/FONT] output showed the overall health assessment of this disk was FAILED, seemingly because it had a really high rate of read errors.

This seemed a very sudden onset for such bad-looking number, so I decided to do a SMART test on this drive to get more information about the failure (and also for the experience of running a SMART test, which I've never done before) -
```
sudo smartctl -t short /dev/sdb
```

But when I re-ran [FONT=Courier New]sudo smartctl -a /dev/sdb[/FONT] after the test completed, the read error rate is now zero and the disk thinks it's totally fine?

What to make of this?
Can I trust this disk going forward? (I don't currently have any data on this disk.)

---

### Post by rsteinmetz70112 on 2021-02-11
You can never fully trust any disk. 

I've had drives that showed errors and then healed themselves. It may be something external to the drive like a bad cable. 
It depends on how lucky your feel. The safe thing to do is replace the drive, but it may never fail before you decide to replace it. 
If you keep using the drive you might want to institute automatic checks, like having smartd monitor the disk.

---

### Post by crip720 on 2021-02-11
Depends on type of data you put on it.  Data you must not lose, make sure you have good backups of it,  cat pictures from youtube, who cares.  If everything protected, use disk till you see smoke

---

### Post by TheFu on 2021-02-11
Run a long test.

Never trust any disk. They all fail.  22% of the time, SMART data doesn't know anything bad about a disk that fails.

Always have backups that happen as often as you don't want to lose data.  Versioned backups are best. There are many tools for making versioned backups. 80% of the time, an rsync mirror is fine, but there are times when that isn't sufficient.  How often should you make backups?  Some of the tools do it hourly and remove the extra backup sets as time passes.  That's how back-in-time works.  It is a great tool for backing up personal data, but not so great for system backups.

---

### Post by Yellow Pasque on 2021-02-12
Please give the entire output of smartctl. Maybe you had some bad sectors which the disk has now marked as bad and it stopped the errors for the moment. Even if that's the case, failed sectors are not a good sign for the health of the drive moving forward.

---

### Post by &amp;KyT$0P# on 2021-02-12
Thanks all for the advices.  Here is [FONT=Courier New]smartctl -a[/FONT] output after completing a long test -
```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-65-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     APPLE HDD HTS541010A9E682
Serial Number:    [COLOR="#FF0000"]xxxxxxxxxxxxxx[/COLOR]
LU WWN Device Id: [COLOR="#FF0000"]x xxxxxx xxxxxxxxx[/COLOR]
Firmware Version: JA0AB4E0
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    [COLOR="#FF0000"]xxxxxxxxxxxxxxxxxxxxxxxxxxxx[/COLOR]
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (   45) seconds.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 210) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   172   172   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   090   090   000    Old_age   Always       -       17304
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   035   035   000    Old_age   Always       -       28663
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   090   090   000    Old_age   Always       -       16339
160 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       34359738394
193 Load_Cycle_Count        0x0012   045   045   000    Old_age   Always       -       554389
194 Temperature_Celsius     0x0002   187   187   000    Old_age   Always       -       32 (Min/Max 11/42)
195 Hardware_ECC_Recovered  0x000a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       64

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     28662         -
# 2  Short offline       Completed without error       00%     28646         -

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

> **TheFu said:**
> 80% of the time, an rsync mirror is fine, but there are times when that isn't sufficient. 

I do backups with rsync + [FONT=Courier New]cp -avl[/FONT] to make hard links for versioning.  What times would this not be sufficient?

---

### Post by TheFu on 2021-02-12
> **halogen2 said:**
>  
I do backups with rsync + [FONT=Courier New]cp -avl[/FONT] to make hard links for versioning.  What times would this not be sufficient?

```
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       **_34359738394_**
```

Holy crap that's a number!  How s that even possible? Something is very wrong with the drive. No idea what it is.

The other question ...
Change the owner and/or permissions on a file included in your backups.  Do the older backup versions reflect the old or the new permissions and owner 
or
the old correct metadata?

See how that could be really bad?

---

### Post by &amp;KyT$0P# on 2021-02-14
Thanks TheFu.  I decommissioned the drive.

---

### Post by Yellow Pasque on 2021-02-14
> **halogen2 said:**
> Thanks TheFu.  I decommissioned the drive.

Maybe you should test it a little more with different system/cables before drawing a conclusion.

> Attribute ID: 192 (0xC0)
Hard drives, supporting this attribute

Samsung, Seagate, IBM (Hitachi), Fujitsu, Maxtor, Western Digital
Description

Power-off Retract Count S.M.A.R.T. parameter indicates the number of power off cycles. Fujitsu: Emergency Retract Cycle Count.
Recommendations

This parameter is considered informational by the most hardware vendors. The value is counted every time the heads are loaded off the media (i.e. every time the machine is powered down, put to sleep or is idle).

Although degradation of this parameter can be an indicator of drive aging and/or potential electromechanical problems, it does not directly indicate imminent drive failure. Regular backup is recommended. Pay closer attention to other parameters and overall drive health. -- [https://kb.acronis.com/content/9127](https://kb.acronis.com/content/9127)

---

### Post by &amp;KyT$0P# on 2021-02-15
I don't currently have another system to test with, and that KB entry supports TheFu's assessment: there's no way the disk could have been powered down 34,359,738,394 times during its lifetime.  Even if it's only the SMART reporting that's messed up, it seems I shouldn't be comfortable continuing to use this disk.

---

### Post by TheFu on 2021-02-16
> **halogen2 said:**
> I don't currently have another system to test with, and that KB entry supports TheFu's assessment: there's no way the disk could have been powered down 34,359,738,394 times during its lifetime.  Even if it's only the SMART reporting that's messed up, it seems I shouldn't be comfortable continuing to use this disk.

I wouldn't trust it - even if I only had cat videos on it.
Not sure I'd even put it into a system to be sold to a random person on the street.  I'd buy a cheap $30 SSD for that with no brand, no published endurance specs, perhaps even used.

---

### Post by PaulRSte on 2021-02-22
Re the very high number of unload errors, is this still increasing or has it stabilised? Like you said this is an impossible number. If still increasing then try disconnecting and reconnecting both ends of the cables. Try replacing the cables and then try connecting to a different power connector and a different connector on the mother board if there's one free. see if you can get ti to stabilise. As someone has already said, running an intensive test can cause bad blocks to be flagged as unusable and the problem to go away. This has been true ever since the early days of PCs. The MSDOS chkdsk utility was really good at this and the disc would work fine afterwards.

---

