---
title: "SMART Currently unreadable sectors"
date: 2013-04-02
forum: Hardware
---

### Post by OxleyDave on 2013-04-02
I have the smartd daemon running on a 12.10 server with raid 6 array using mdadm and a few days ago I got an email about bad sectors on one of the disks:
```
Device: /dev/sdd [SAT], 8 Currently unreadable (pending) sectors
```
immediately followed by another email:
```
Device: /dev/sdd [SAT], 8 Offline uncorrectable sectors
```

I ordered a replacement disk which is yet to arrive. /dev/sdd has not yet been kicked out of the array. Anyway these emails have since continued and reported the same number of unreadable sectors. Last night I got another couple of emails:
```
Device: /dev/sdd [SAT], 65528 Currently unreadable (pending) sectors
```
and again immediately followed by:
```
Device: /dev/sdd [SAT], 65528 Offline uncorrectable sectors
```

However when I run 'smartctl -a /dev/sdd' it doesn't appear to show any issues other than the original extended tests failing. I don't really know how to read smartd output. But it appears the sectors are no longer reported as an issue but also haven't been reallocated as Reallocated_Sector_Ct is 0. But also the last few tests have completed succesfully, so I'm not sure why smartd generated last nights email. I'm going to replace the disk as soon as the replacement arrives but I am confused about the SMART output. Can anyone help me understand what's going on with this please?

Here's the output from 'smartctl -a /dev/sdd':
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   106   099   006    Pre-fail  Always       -       229065848
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       37
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       522315485
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6270
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       37
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   069   045    Old_age   Always       -       24 (Min/Max 22/31)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       20
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       47
194 Temperature_Celsius     0x0022   024   040   000    Old_age   Always       -       24 (0 11 0 0 0)
197 Current_Pending_Sector  0x0012   100   001   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   001   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       44547400800382
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       261256089719672
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       598035371796


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Self-test routine in progress 10%      6270         -
# 2  Short offline       Completed without error       00%      6259         -
# 3  Short offline       Completed without error       00%      6237         -
# 4  Short offline       Completed without error       00%      6213         -
# 5  Short offline       Completed without error       00%      6189         -
# 6  Extended offline    Completed without error       00%      6177         -
# 7  Short offline       Completed without error       00%      6165         -
# 8  Short offline       Completed without error       00%      6141         -
# 9  Short offline       Completed without error       00%      6117         -
#10  Short offline       Completed without error       00%      6093         -
#11  Short offline       Completed without error       00%      6069         -
#12  Short offline       Completed without error       00%      6045         -
#13  Short offline       Completed without error       00%      6021         -
#14  Extended offline    Completed: read failure       50%      6017         3821328312
#15  Extended offline    Completed: read failure       50%      6005         3821328312
#16  Short offline       Completed without error       00%      5997         -
#17  Short offline       Completed without error       00%      5973         -
#18  Short offline       Completed without error       00%      5949         -
#19  Short offline       Completed without error       00%      5925         -
#20  Short offline       Completed without error       00%      5901         -
#21  Short offline       Completed without error       00%      5877         -
2 of 2 failed self-tests are outdated by newer successful extended offline self-test # 6

```

/var/log/syslog shows this for the sdd disk:
```
Apr  2 22:43:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], 65528 Currently unreadable (pending) sectors
Apr  2 22:43:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], 65528 Offline uncorrectable sectors
Apr  2 22:43:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], SMART Usage Attribute: 197 Current_Pending_Sector changed from 100 to 1
Apr  2 22:43:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], SMART Usage Attribute: 198 Offline_Uncorrectable changed from 100 to 1
Apr  2 23:13:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], No more Currently unreadable (pending) sectors, warning condition reset after 1 email
Apr  2 23:13:19 baldrick smartd[5764]: Device: /dev/sdd [SAT], No more Offline uncorrectable sectors, warning condition reset after 1 email

```
Cheers,
Dave.

---

### Post by ahallubuntu on 2013-04-02
~

---

### Post by OxleyDave on 2013-04-02
> **ahallubuntu said:**
> Looks like a glitch or a false alarm.  Originally you had 8 pending sectors - then 65528 (which in hex is FFF8 unsigned or -8 signed decimal).  Looks too much like a glitch to have first 8 then -8 sectors showing up vs. real numbers.

Wow, good catch. I didn't notice that. 8 to -8 seems unlikely to be a coincidence to me and a glitch seems likely.

> **ahallubuntu said:**
> I'd make sure the extended test passes on sdd anyway.  It goes without saying you should be making regular backups anyway, even with a RAID.  A RAID protects you against only hard drive failure, not file system corruption or accidental erasure.

The previous extended tests failed at 50% and the current test has only 10% remaining, so it's looking good so far. The system backs up important files using Crashplan but I don't have the bandwidtch to back up the 4TB of media to the cloud. Never sure how best to back up such a huge amount of data.

> **ahallubuntu said:**
> FYI, pending sectors (when not false alarms) don't always become reallocated - that's how it's SUPPOSED to work but sometimes they get "stuck" and can never be re-allocated - and you are kind of out of luck.  Sometimes writing zeros to the disk will clear them, usually not.

Understood, and I did read that md handles bad sectors by building the data from the other disks and attempting to write it back to the bad sectors; removing the disk from the arrays if this fails. So, I ordered a disk to replace it in anticipation of this happening but I guess it hasn't needed to read or write to those sectors. Or maybe it has and that's what reset them. Either way, I guess I shouldn't rush to replace the disk and just keep an eye on it?

Is there anything else I should look at to check the disk? The Raw_Read_Error_Rate does look quite a bit higher than the other disks:
sudo smartctl -a /dev/sda |grep Raw_Read_Error_Rate
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       123604048
dave@baldrick:~$ sudo smartctl -a /dev/sdb |grep Raw_Read_Error_Rate
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       74104424
dave@baldrick:~$ sudo smartctl -a /dev/sdc |grep Raw_Read_Error_Rate
  1 Raw_Read_Error_Rate     0x000f   113   099   006    Pre-fail  Always       -       56165264
dave@baldrick:~$ sudo smartctl -a /dev/sdd |grep Raw_Read_Error_Rate
  1 Raw_Read_Error_Rate     0x000f   107   099   006    Pre-fail  Always       -       236668608

Cheers,
Dave.

---

### Post by ahallubuntu on 2013-04-02
~

---

