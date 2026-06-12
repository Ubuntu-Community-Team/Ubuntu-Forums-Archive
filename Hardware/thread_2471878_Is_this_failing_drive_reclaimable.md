---
title: "Is this failing drive reclaimable?"
date: 2022-02-11
forum: Hardware
---

### Post by renmccourtey on 2022-02-11
Hi, a few days ago my home server went to kernel panic, something went wrong with its system drive. I swapped the drive, restored the server and now I'm trying to figure out what happened to the old one. It actually *is* quite old, so I guess it will be a hw failure, still I'd like to try to learn something about recovery technics (and find why SMART didn't warn me). Those are steps I took so far:

I can see the drive as /dev/sdb now, and I can detect lvm there, so I renamed ubuntu-vg to ubuntu-vg-old and activated it. 
```
root@calcium:~# lvs
 LV        VG            Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
 ubuntu-lv ubuntu-vg     -wi-ao---- <29.06g
 backups   ubuntu-vg-old -wi-a-----   1.29t
 ubuntu-lv ubuntu-vg-old -wi-a----- 200.00g

```
Unfortunately, mounting it doesn't work and after long timeout the command fails making drive inaccessible:
```
root@calcium:~# mount /dev/ubuntu-vg-old/ubuntu-lv /mnt -o ro,user
mount: /mnt: can't read superblock on /dev/mapper/ubuntu--vg--old-ubuntu--lv.
root@calcium:~# pvscan
      Error reading device /dev/sdb at 0 length 512.
      Error reading device /dev/sdb at 0 length 4096.
      Error reading device /dev/sdb1 at 0 length 4096.
      Error reading device /dev/sdb2 at 0 length 4096.
      Error reading device /dev/sdb3 at 0 length 4096.
      PV /dev/sda3   VG ubuntu-vg       lvm2 [58.12 GiB / 29.06 GiB free]
      Total: 1 [58.12 GiB] / in use: 1 [58.12 GiB] / in no VG: 0 [0   ]

```
After reboot (I didn't find another way to make it accessible again) the drive is back. I tried to fix it:
```
root@calcium:~# fsck /dev/mapper/ubuntu--vg--old-ubuntu--lv
fsck from util-linux 2.36.1
e2fsck 1.46.3 (27-Jul-2021)
/dev/mapper/ubuntu--vg--old-ubuntu--lv: recovering journal
fsck.ext4: Input/output error while trying to re-open /dev/mapper/ubuntu--vg--old-ubuntu--lv
    
/dev/mapper/ubuntu--vg--old-ubuntu--lv: ********** WARNING: Filesystem still has errors **********

```
But this behaves exactly same as mount, long timeout and the drive is dropped from the system. I ran SMART offline surface test overnight:
 ```
smartctl -t offline /dev/sdb
```
It didn't find any issues nor changed any offline SMART attribute. badblocks read test also runs well, with no errors:
```
root@calcium:~# badblocks -b 4096 -c 1024 -s -o bb.out /dev/sdb
Checking for bad blocks (read-only test): done

```
So I tried nondestructive read-write test with badblocks:
```
badblocks -b 4096 -c 1024 -s -n -v /dev/sdb
```
and the drive drops from the system again after about half an hour of run.
Later I went on and tried to reformat drive:
```
mkfs.ext4 -b 4096 -c -c -m 0 -L Backups /dev/sdb1
```
There were millions of errors because again, disk went AWOL.
I already replaced SATA cable and connected the drive to a different port. There is clearly an issue only when **writing** to particular sector(s). For the rest of the surface it is usable so far. I'd like to know, if I can somehow make the drive running, even if to see more bad blocks appearing. I obviously would use it for scratch data only if successfully resurrected.

These are current SMART data, it really drives me mad to see how the drive have near-death experience and SMART is all so happy and shiny. There are bad blocks apparently, but no relocations(?) and what's most important, no reason for the drive to get "disconnected" from the system when hitting bad block. BTW, regarding well known Samsung FW error mentioned in smartctl info header, I flashed correct fw to the drive years ago.
```

root@calcium:~# smartctl -H /dev/sdb
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.13.0-28-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


root@calcium:~# smartctl -a /dev/sdb
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.13.0-28-generic] (local build)Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F4 EG (AF)
Device Model:     SAMSUNG HD204UI
Serial Number:    S2H7J1BB106801
LU WWN Device Id: 5 0024e9 0048b6675
Firmware Version: 1AQ10001
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Fri Feb 11 20:33:17 2022 CET


==> WARNING: Using smartmontools or hdparm with this
drive may result in data loss due to a firmware bug.
****** THIS DRIVE MAY OR MAY NOT BE AFFECTED! ******
Buggy and fixed firmware report same version number!
See the following web pages for details:
http://knowledge.seagate.com/articles/en_US/FAQ/223571en
https://www.smartmontools.org/wiki/SamsungF4EGBadBlocks


SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x80) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (20280) seconds.
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
recommended polling time:        ( 338) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       415
  2 Throughput_Performance  0x0026   055   051   000    Old_age   Always       -       18840
  3 Spin_Up_Time            0x0023   078   066   025    Pre-fail  Always       -       6859
  4 Start_Stop_Count        0x0032   094   094   000    Old_age   Always       -       6279
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       31708
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       2
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2291
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       19262840
191 G-Sense_Error_Rate      0x0022   099   099   000    Old_age   Always       -       11132
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   044   000    Old_age   Always       -       36 (Min/Max 14/56)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   083   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   084   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       235
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       2
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       6325


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     31708         -
# 2  Short offline       Interrupted (host reset)      90%     31699         -
# 3  Short offline       Completed without error       00%     31671         -
# 4  Short offline       Completed without error       00%     31656         -
# 5  Short offline       Completed without error       00%     31632         -
# 6  Short offline       Completed: read failure       10%     31608         2541336840
# 7  Extended offline    Completed without error       00%     31587         -
# 8  Short offline       Completed without error       00%     31560         -
# 9  Short offline       Completed without error       00%     31536         -
#10  Short offline       Completed without error       00%     31512         -
#11  Short offline       Completed without error       00%     31488         -
#12  Short offline       Completed without error       00%     31464         -
#13  Short offline       Completed without error       00%     31440         -
#14  Extended offline    Completed without error       00%     31419         -
#15  Short offline       Completed without error       00%     31392         -
#16  Short offline       Completed without error       00%     31368         -
#17  Short offline       Completed without error       00%     31344         -
#18  Short offline       Completed without error       00%     31320         -
#19  Short offline       Completed without error       00%     31296         -
#20  Short offline       Completed without error       00%     31272         -
#21  Extended offline    Completed without error       00%     31251         -


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by TheFu on 2022-02-11
We have different ideas about SMART data saying nothing is wrong.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       [COLOR="#FF0000"]415[/COLOR]
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       31708
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       2
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2291
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       [COLOR="#FF0000"]19262840[/COLOR]
191 G-Sense_Error_Rate      0x0022   099   099   000    Old_age   Always       -       [COLOR="#FF0000"]11132[/COLOR]
194 Temperature_Celsius     0x0002   064   044   000    Old_age   Always       -       36 (Min/Max 14/56)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   083   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   084   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       [COLOR="#FF0000"]235[/COLOR]
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       2
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       6325
```

Have you looked up what those mean? 
> This parameter is considered informational by the most hardware vendors. Although degradation of this parameter can be an indicator of drive aging and/or **potential electromechanical problems**, it does not directly indicate imminent drive failure. Regular backup is recommended. Pay closer attention to other parameters and overall drive health.

One of those is about the cache memory on the board failing.

According to Backblaze's quarterly reports, 28% of the time, HDDs fail without any warning.  So, the question comes back to how important is your data?

---

### Post by renmccourtey on 2022-02-11
Thx TheFu. Clearly, I'm bad in reading SMART bcs I focused on completely different attributes, like:
```
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   083   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   084   000    Old_age   Offline      -       0
```

While those do show something in the 'worst' area, raw is 0, that was my wrong assumption everything is ok (apparently I just forgot there are other components beside the platters).
Of course, if the memory module of the cache (or electronics in general) is malfunctioning, the drive wont be usable even for scratch data so I guess I can bin, dismantle or hammer the poor old thing. Thanks for pointing these attributes out for me.

---

