---
title: "Data slowly corrupting on software raid5"
date: 2017-11-08
forum: Hardware
---

### Post by Dethecus on 2017-11-08
I'm hoping someone can point to what may be causing my data to slowly corrupt itself (jpegs slowly get garbled, movies get artifacts and eventually get so bad they stop working past certain points)

I have a raid 5 array using MDADM, it consists of 7x 750GB SATA drives, with 1x 250GB drive for the OS, all running ext4
I have had drives fail in the past and I have replaced them, no big deal
I suspect that one of the drives is on the way out but hasn't completely failed yet, it's hard to find the smoking gun!

relevant outputs:

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[8] sdc1[1] sdf1[3] sde1[6] sdd1[0] sda1[7] sdb1[5]
      4394643456 blocks super 1.2 level 5, 512k chunk, algorithm 2 [7/7] [UUUUUUU]

unused devices: <none>


$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Mar  1 01:50:19 2014
     Raid Level : raid5
     Array Size : 4394643456 (4191.06 GiB 4500.11 GB)
  Used Dev Size : 732440576 (698.51 GiB 750.02 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Wed Nov  8 21:18:33 2017
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : avatar:0  (local to host avatar)
           UUID : 8e7c7abb:3f90d43e:32c7616f:51811cdd
         Events : 29011

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       8       8      113        2      active sync   /dev/sdh1
       3       8       81        3      active sync   /dev/sdf1
       7       8        1        4      active sync   /dev/sda1
       5       8       17        5      active sync   /dev/sdb1
       6       8       65        6      active sync   /dev/sde1


$ cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3d56f2a1-c952-41f4-bab2-7b717a99e168 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3722735c-5d06-44cb-aeb8-d6ffa0d34d98 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0        /mnt/raid       ext4    defaults        1 2



All SMART tests (Extended offline tests) complete without error
Extended output gives stats on error rates that look possibly concerning
I understand the outputs start at 100 (or 200 in some cases) and go down to 0 as they get worse, I'm just not sure if some of the error rates that aren't perfect (in red) could be causing the issue
Any help or advice would be greatly appreciated!

```
SDA
	   
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
[COLOR="#FF0000"]**  1 Raw_Read_Error_Rate     0x000f   104   072   006    Pre-fail  Always       -       233345589**[/COLOR]
  3 Spin_Up_Time            0x0003   093   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       106
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       19
[COLOR="#FF0000"]**  7 Seek_Error_Rate         0x000f   074   060   030    Pre-fail  Always       -       155428213679**[/COLOR]
  9 Power_On_Hours          0x0032   046   046   000    Old_age   Always       -       48137
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       106
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   051   045   045    Old_age   Always   In_the_past 49 (Min/Max 21/52)
194 Temperature_Celsius     0x0022   049   055   000    Old_age   Always       -       49 (0 14 0 0)
[COLOR="#FF0000"]**195 Hardware_ECC_Recovered  0x001a   058   048   000    Old_age   Always       -       173255646**[/COLOR]
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0


SDB

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   112   099   006    Pre-fail  Always       -       48659139
  3 Spin_Up_Time            0x0023   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       80
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
[COLOR="#FF0000"]**  7 Seek_Error_Rate         0x002f   074   060   030    Pre-fail  Always       -       28447800**[/COLOR]
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21284
 10 Spin_Retry_Count        0x0033   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       80
180 Unused_Rsvd_Blk_Cnt_Tot 0x002b   100   100   000    Pre-fail  Always       -       152301
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   056   049   045    Old_age   Always       -       44 (Min/Max 17/49)
194 Temperature_Celsius     0x0022   044   051   000    Old_age   Always       -       44 (0 12 0 0)
[COLOR="#FF0000"]**195 Hardware_ECC_Recovered  0x003a   043   019   000    Old_age   Always       -       48659139**[/COLOR]
196 Reallocated_Event_Count 0x0032   100   100   036    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0


SDC

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   075   075   011    Pre-fail  Always       -       8210
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       209
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       9776
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       63965
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       209
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   055   051   000    Old_age   Always       -       45 (Min/Max 12/47)
194 Temperature_Celsius     0x0022   054   052   000    Old_age   Always       -       46 (0 103 52 12)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       28813237
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0


SDD

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   075   075   011    Pre-fail  Always       -       8430
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       214
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   099   099   015    Pre-fail  Offline      -       15301
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       63965
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       12
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       214
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   057   000    Old_age   Always       -       41 (Min/Max 12/42)
194 Temperature_Celsius     0x0022   058   057   000    Old_age   Always       -       42 (Min/Max 12/47)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       19881315
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0


SDE

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   118   099   006    Pre-fail  Always       -       175782740
  3 Spin_Up_Time            0x0023   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       114
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
[COLOR="#FF0000"]**  7 Seek_Error_Rate         0x002f   074   060   030    Pre-fail  Always       -       28140768**[/COLOR]
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21402
 10 Spin_Retry_Count        0x0033   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       114
180 Unused_Rsvd_Blk_Cnt_Tot 0x002b   100   100   000    Pre-fail  Always       -       554887758
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   056   050   045    Old_age   Always       -       44 (Min/Max 18/47)
194 Temperature_Celsius     0x0022   044   050   000    Old_age   Always       -       44 (0 13 0 0)
[COLOR="#FF0000"]**195 Hardware_ECC_Recovered  0x003a   037   018   000    Old_age   Always       -       175782740**[/COLOR]
196 Reallocated_Event_Count 0x0032   100   100   036    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0


SDF

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   075   075   011    Pre-fail  Always       -       8250
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       214
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   099   099   015    Pre-fail  Offline      -       15240
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       63930
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       105
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       214
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   062   000    Old_age   Always       -       37 (Min/Max 11/38)
194 Temperature_Celsius     0x0022   062   062   000    Old_age   Always       -       38 (Min/Max 11/43)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       18316398
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0


SDG (System drive)

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0007   253   253   025    Pre-fail  Always       -       4352
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       258
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       66045
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       215
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       134120402
184 End-to-End_Error        0x0033   253   253   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   253   253   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   106   097   000    Old_age   Always       -       44 (Min/Max 5/47)
194 Temperature_Celsius     0x0022   106   094   000    Old_age   Always       -       44 (Min/Max 5/48)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       134120402
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   253   253   000    Old_age   Always       -       0


SDH

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   075   075   011    Pre-fail  Always       -       8230
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       214
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       9859
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       63965
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       214
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   052   000    Old_age   Always       -       46 (Min/Max 12/47)
194 Temperature_Celsius     0x0022   054   052   000    Old_age   Always       -       46 (0 60 52 12)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       14068324
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
```

---

### Post by TheFu on 2017-11-09
Use ZFS if you care about data corruption. It is the only file system which validates what gets written to disks.
RAID with large disks has always been an issue.  Using RAID with over 2TB disks is not recommended by storage vendors.
I scrub my mdadm arrays weekly to see if there are issues. Stopped using RAID5 when I switched to 2T+ disks, but I was coming from 320G disks, so the jump in available storage was huge already.

In a home environment, I only use RAID for VMs.  Media doesn't get RAID, since backups are 1000x more important than RAID anyways.

Please use *code tags* when posting **any** command/file output.  Easier to read.

---

### Post by Tadaen_Sylvermane on 2017-11-09
Snapraid is a good solution for rarely changing data like media and pictures. Does corruption checking as well, although it isn't real time scrubbing. Can use different size drives. Also you are not locked into a raid setup. The snapraid rides on top of the existing partition structures, if you want to stop using it you just stop. No loss. And if you lose more drives than parity you only lose those drives, not the whole array.

---

