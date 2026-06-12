---
title: "how to interpit the smartctl results?"
date: 2008-11-14
forum: General Help
---

### Post by duanedesign on 2008-11-14
I just recently installed the smartmontools package contains two utility programs (smartctl and smartd) to control and monitor storage systems using the Self-Monitoring, Analysis and Reporting Technology System (SMART) built into most modern ATA and SCSI harddisks. In many cases, these utilities will provide advanced warning of disk degradation and failure.

However after running the test I have no idea what the results mean. In several columns the result is "old-age" but the computer is only a couple of weeks old. Also some lines say "Pre-Fail". Does anyone have, or know where to get definitions for these descriptors.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG    VALUE WORST THRESH TYPE    UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   050    Pre-fail Always       -       0
  2 Throughput_Performance  0x0007   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   100   100   002    Pre-fail  Always       -       1588
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       71
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       274
 10 Spin_Retry_Count        0x0013   101   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       70
184 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       2
189 High_Fly_Writes         0x003a   100   100   001    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   071   049   045    Old_age   Always       -       29 (Lifetime Min/Max 21/29)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       3
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       6062
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       29 (Lifetime Min/Max 21/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       46
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       230
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       346
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

---

### Post by CP1256 on 2008-11-14
You should look at 'Raw value'.

Spin up time is the time your hdd needs to spin up (in milliseconds).
Spin retry count is how much times it failed to spin up the hdd, the lower the better.
Load hours is the how much hours your hard drive has been working under load (writing something for example).

That's all I can remember now, more information can is on [http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology#Known_ATA_S.M.A.R.T._attributes](http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology#Known_ATA_S.M.A.R.T._attributes)

---

