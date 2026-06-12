---
title: "What's up with my hard drives?"
date: 2012-09-23
forum: Hardware
---

### Post by pssturges on 2012-09-23
Below is my current smart data from 3 hdd's in my mythbuntu system running as a home server. The system does run 24/7 and gets a fair bit of use. The drives are between 2 and 3 years old, which I would consider to be somewhere in the middle of their life expectancy. I have had other drives in this system that have exhibited these kinds of error and eventually failed.

So,

1) Is this level of errors within expected range for drives this age?

2) Are any of them in imminent danger of failure?

3) Is there something up to be causing this ongoing issue?

Thanks
Phil
```
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       2154
  3 Spin_Up_Time            0x0027   187   139   021    Pre-fail  Always       -       1641
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       106
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       12689
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       84
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   097   087   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       10
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       6
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       2

 
 
 
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       135111878
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       185
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       157113280
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       16202
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       186
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   057   050   045    Old_age   Always       -       43 (Min/Max 41/46)
194 Temperature_Celsius     0x0022   043   050   000    Old_age   Always       -       43 (0 18 0 0)
195 Hardware_ECC_Recovered  0x001a   039   028   000    Old_age   Always       -       135111878
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       91465623552240
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4004419904
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2213752186

 
 
 
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   015    Pre-fail  Always       -       4288
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       461
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       27077
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       344
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       6958744
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       786432
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   056   036   000    Old_age   Always       -       44
194 Temperature_Celsius     0x0022   103   043   000    Old_age   Always       -       45
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       6958744
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Total_Pending_Sectors   0x0012   253   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   253   253   000    Old_age   Always       -       0
```

---

### Post by lukeiamyourfather on 2012-09-24
Anything over a predetermined threshold will be marked as "Pre-fail" which is like it sounds. Those are indications the drive is not healthy and will likely fail. The drives may go on to live for another 20 years or they might die without any red flags at all from SMART. They are just another troubleshooting tool.

If it were my server and I had anything important on it I'd be sure it was backed up elsewhere and safe (hopefully you do this before SMART tells you a disk is failing).

I would consider three years your money's worth and get some new drives if you don't want any interruption. If a few days of downtime and loss of anything that isn't backed up is fine then run them until they die and then get some new ones (or send them in for warranty replacement if applicable).

---

### Post by pssturges on 2012-09-24
> **lukeiamyourfather said:**
> Anything over a predetermined threshold will be marked as "Pre-fail" which is like it sounds. Those are indications the drive is not healthy and will likely fail. The drives may go on to live for another 20 years or they might die without any red flags at all from SMART. They are just another troubleshooting tool.

If it were my server and I had anything important on it I'd be sure it was backed up elsewhere and safe (hopefully you do this before SMART tells you a disk is failing).

I would consider three years your money's worth and get some new drives if you don't want any interruption. If a few days of downtime and loss of anything that isn't backed up is fine then run them until they die and then get some new ones (or send them in for warranty replacement if applicable).

Time to bolster my backup regime I think. I agree that 3years plus is probably about par for a HDD, but 2 of them are barely 2 years old. If one or even 2 were showing signs of being on the way out would be fair enough, but all 3?

Cheers

---

### Post by lukeiamyourfather on 2012-09-24
> **pssturges said:**
> Time to bolster my backup regime I think. I agree that 3years plus is probably about par for a HDD, but 2 of them are barely 2 years old. If one or even 2 were showing signs of being on the way out would be fair enough, but all 3?

Cheers

Some models fare better than others or it could be something in the environment (heat, vibration, moisture).

---

