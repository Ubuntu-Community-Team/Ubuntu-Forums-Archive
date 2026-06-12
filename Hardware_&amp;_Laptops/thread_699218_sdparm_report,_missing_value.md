---
title: "sdparm report, missing value"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by ilLorenz on 2008-02-17
Hi everybody, I've been checking the last few days for the infamous bug that shortens hard-disk lifetime in ubuntu as well in another distros... i ran the command smartctl -a /dev/sda and here is the output

Device Model:     FUJITSU MHY2120BH
Serial Number:    K430T7B2AVVS
Firmware Version: 0085000B
User Capacity:    120,034,123,776 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x42
Local Time is:    Sun Feb 17 11:40:56 2008 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       4253
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       7510
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       46550
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       492
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       110
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       111
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 9/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       44119
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       120792014782466
198 Offline_Uncorrectable   0x0032   100   100   000    Old_age   Always       -       29749125775363
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       3519849
200 Multi_Zone_Error_Rate   0x0032   100   100   000    Old_age   Always       -       9827904

Here is my problem: I've been told to look for value 193 or Load_Cycle_Counts, but i can't find it! I'm really confused  :confused: ,.. Hope somebody can explain if I should be worried about a possible crash... 

Thanks in advance!

---

