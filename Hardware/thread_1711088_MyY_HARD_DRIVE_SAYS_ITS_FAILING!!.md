---
title: "MyY HARD DRIVE SAYS ITS FAILING!!"
date: 2011-03-20
forum: Hardware
---

### Post by mttrackmaster38 on 2011-03-20
I just got a notification from  disk utility saying my hdd is about to fail. I scanned it with smartctl and I got this:

marquis@tarantulaman ~ $ sudo smartctl -HA /dev/sda1
[sudo] password for marquis: 
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   186   185   021    Pre-fail  Always       -       1691
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2364
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   028   028   051    Pre-fail  Always   FAILING_NOW 1377
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       8116
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2138
187 Reported_Uncorrect      0x0032   100   091   000    Old_age   Always       -       9
188 Command_Timeout         0x0032   098   098   000    Old_age   Always       -       8590065666
190 Airflow_Temperature_Cel 0x0022   056   036   040    Old_age   Always   In_the_past 44
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       206
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       12592
194 Temperature_Celsius     0x0022   103   083   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

It says my seek error rate is failing. I dont know what that means. Do I have to replace my hard drive?

---

### Post by ebasa on 2011-03-20
BACK UP EVERYTHING NOW! Just in case, sometimes you do get false readings though.

---

### Post by Yellow Pasque on 2011-03-20
Back up all data, but don't be surprised if the drive fails while doing so. I hope you have a recent backup..

If you are able to back up successfully, you might want to look into possible drive firmware updates in case there's a problem with it.

---

### Post by mttrackmaster38 on 2011-05-23
Thanks for your help but it looks like it was just a mistake because my computer no longer tells me my hdd is failing. It runs perfectly.

---

