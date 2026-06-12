---
title: "SmartCtl Information"
date: 2011-03-16
forum: Hardware
---

### Post by buckyb on 2011-03-16
Okay so I ran SmartCtl, and I've scoured different forums to learn more about the information presented by SmartCtl. But I'm still confused about some of the numbers. Some numbers same insanely high.

```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   092   092   062    Pre-fail  Always       -       2621440
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   240   240   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   096   096   000    Old_age   Always       -       6740
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   075   075   000    Old_age   Always       -       10980
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       5644
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       149
193 Load_Cycle_Count        0x0012   077   077   000    Old_age   Always       -       233594
194 Temperature_Celsius     0x0002   096   096   000    Old_age   Always       -       57 (Min/Max 9/61)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       124
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       11
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

```

Power Cycle Count is 5644.  I rarely reboot, I usually keep my laptop on standby. This number seems way too high, does anyone know why? I'm sure I don't restart my computer or turn it off every 2 hours. That cant be true. (10,980 power on hours/5644 Power Cycles)

Also, Reallocated Event Count is 124, due to I/O errors according to the Fedora Wiki. Does that mean that my HardDisk is getting sick? Is it time to buy a new disk?

The good news is my Load Cycle Count is still low: 233594 and my Reallocated Sector Count is 0.

[https://fedoraproject.org/wiki/Smartctl](https://fedoraproject.org/wiki/Smartctl)
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

What do you guys think?

---

### Post by dabl on 2011-03-16
Let's shoot straight to the bottom line:  [https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux](https://ata.wiki.kernel.org/index.php/Known_issues#Drives_which_perform_frequent_head_unloads_under_Linux)

---

