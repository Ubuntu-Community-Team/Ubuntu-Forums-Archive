---
title: "HDD possibly dying"
date: 2012-09-27
forum: Hardware
---

### Post by KjetilK on 2012-09-27
Hi all!

I just noticed a problem with my Mythbuntu box. In the middle of a playback, it would just stop. It would not happen at the same place in the playback every time, and it happens on many different files. I looked in dmesg, and found a lot of errors related to sdc, which is a Western Digital Caviar Green 1.5 TB disk. I've posted a log of the most recent output of [dmesg here]("http://pastebin.com/Lb4FC57S").

So, I've started to investigate with smartmontools, and this is what I found from a long self-test:

```

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       60%     19015         1455150408

```

The attributes are as follows:
```

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1380
  3 Spin_Up_Time            0x0027   185   180   021    Pre-fail  Always       -       5750
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       74
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   074   074   000    Old_age   Always       -       19020
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       72
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       2361449
194 Temperature_Celsius     0x0022   113   103   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       7
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       7
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       7

```

Mmmmm, interesting... It just I have no clue what it means...

Since the error seemed to occur rather randomly and on many different files, I've been guessing that it is not a simple localized error, and that I should just buy a new one ASAP, but OTOH, if it can be rescued, that would save me some money too... So, can this situation be saved?


I have a backup of all the critical data on this disk, but it is a PITA if the disk fails anyway, so it would be nice to know if I should just buy another ASAP anyway.

---

### Post by 2F4U on 2012-09-27
Ok, here is how I understand those values. The important columns to look at are:
- VALUE: the current value of the attribute
- WORST: the worst value of the attribute up to now
- THRESH: what the manufacturer considers to be the value from which on the hdd is damaged

Most important attributes to look at:
-  Raw_Read_Error_Rate: points to read errors, either of the heads or due to surface damage
- Seek_Error_Rate: errors encountered during repositioning of the heads
- Reallocated_Sector_Ct: counts movement of bad sectors to other sectors
- Multi_Zone_Error_Rate: errors encountered during write operations

Since there have already been considerable (200) errors detected, it seems a good idea to me to replace the drive.

---

### Post by KjetilK on 2012-09-27
> **2F4U said:**
> 
Since there have already been considerable (200) errors detected, it seems a good idea to me to replace the drive.

OK, thanks for the advice, I've ordered a new disk now! 

Given that it has that many errors, possibly causing many files to be unreadable, what would be the best way to copy the data to the new drive?

Best,

Kjetil

---

### Post by Ares Drake on 2012-09-27
If you want to copy bit by bit, you could use ddrescue (package somehow is called gddrescue).
For a file-based copy I would suggest rsync.

Both are teminal based programs, and both are rather tolerant with errors. 

With ddrescue, be double sure to NOT mix up origin and destination though, there is no warning and if you do mix them up, you would overwrite the dying disk with empty zeros from the new disk.

Good luck getting all your data off the dying drive!

---

### Post by ahallubuntu on 2012-09-27
7 Pending Sectors is very bad news.  (It means 7 sectors are in a state where the drive tried to read data from them but cannot.)  It could mean the surface has started to fail, especially with the high error rate.

I would try zeroing out the entire drive once you have copied off anything you really need from the drive and see if those pending sectors clear.  If they do, and your error rates return to normal, the drive may be OK.  If the pending sectors remain, replace the drive.

---

### Post by KjetilK on 2012-10-25
Ah, I forgot to thank you for the advices! I have replaced the device now and upgraded the box. I ended up copying with scp actually, as it was easiest to do it across the network. I managed to do that without data loss, but it was a lot of scary messages along the way... Thank you also very much for advicing that the disk may not be dead, I've kept it so that I can try that out if I find a another system to try it in.

---

