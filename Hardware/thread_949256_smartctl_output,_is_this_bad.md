---
title: "smartctl output, is this bad?"
date: 2008-10-16
forum: Hardware
---

### Post by inigomontoya on 2008-10-16
```
smartctl version 5.38 [powerpc-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   057   042   006    Pre-fail  Always       -       129631731
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       813
  5 Reallocated_Sector_Ct   0x0033   082   082   036    Pre-fail  Always       -       729
  7 Seek_Error_Rate         0x000f   083   060   030    Pre-fail  Always       -       223163432
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6253
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       818
194 Temperature_Celsius     0x0022   047   053   000    Old_age   Always       -       47 (0 12 0 0)
195 Hardware_ECC_Recovered  0x001a   052   048   000    Old_age   Always       -       45372372
197 Current_Pending_Sector  0x0012   098   098   000    Old_age   Always       -       42
198 Offline_Uncorrectable   0x0010   098   098   000    Old_age   Offline      -       42
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   098   251   000    Old_age   Always       -       2
```

---

### Post by jpkotta on 2008-10-16
Yeah, that's bad.  There are way too many errors.  Back up your data and get a new drive.  Also, it seems to be running kind of hot.  My drives are at 32C.  47C is not dangerously hot, but maybe double check your cooling.

---

### Post by inigomontoya on 2008-10-20
Thanks, this drive will be on it's way back to Seagate tomorrow as it is under warrantee.  I can't put anything on it for more than 3 days without the file system becoming corrupt.

---

