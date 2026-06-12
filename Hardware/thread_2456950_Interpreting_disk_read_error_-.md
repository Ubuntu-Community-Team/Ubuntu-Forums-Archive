---
title: "Interpreting disk read error -"
date: 2021-01-22
forum: Hardware
---

### Post by michael351 on 2021-01-22
I have a Western Digital 4TB drive which is reporting read failure:

/dev/sdb single data partition (sdb1)

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%       826         8390658
# 2  Short offline       Completed: read failure       90%       826         8390658

```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       8
  3 Spin_Up_Time            0x0027   156   138   021    Pre-fail  Always       -       11175
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       492
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       827
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       286
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       93
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       404
194 Temperature_Celsius     0x0022   125   097   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```


How can I find which file this LBA refers? And is there a way to 'fix' this and then I can monitor in case the disk is going bad.

---

### Post by TheFu on 2021-01-22
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       3
```
is the only thing that looks bad to me.

If you want to try and restore those sectors, there is some cylinder, partition, header math needed.  I've seen the math outlines online, but never got it working for me because different vendors use different terms for block and sector sizes in their SMART reports - even between different models.  After all that, those sectors can still be 100% gone.

For my data, that means the disks are removed as primary storage and relegated to sneaker-net use only.  They aren't safe for backups ... unless you are fine losing data in your backups.

That number of powered on hours is tiny, BTW.
Just checked the times for a system here: Power_On_Hours for the disks are: 42478, 83063, 5251, 21476, 42311. All have 0 (zero) Reallocated_Sector_Ct and no pending sectors.  Pending sectors should be relocated when accessed, but a failing disk sometimes fails to do that.  SMART data isn't a guarantee of a good disk.  Remember reading that SMART data only provides hints at dying storage 78% of the time.  The other 22% - nothing.

---

