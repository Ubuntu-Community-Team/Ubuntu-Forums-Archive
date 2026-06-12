---
title: "SMART Control Pre-Fail &amp; Read Failure - Bad Disk?"
date: 2018-11-15
forum: Hardware
---

### Post by mdonders on 2018-11-15
I have been seeing some performance issues on my home-server and saw some recommendations that even after I run a **sudo touch /forcefsck** on reboot.

This is the output from my **smartctl** commands. Not sure if this disk is going bad or if the issue is related to something else on the server?

```

$ sudo smartctl -A /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-39-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   079   079   006    Pre-fail  Always       -       231061819
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       734
  5 Reallocated_Sector_Ct   0x0033   043   043   036    Pre-fail  Always       -       2364
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       734662636
  9 Power_On_Hours          0x0032   073   073   000    Old_age   Always       -       23942
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       355
183 Runtime_Bad_Block       0x0032   099   099   000    Old_age   Always       -       1
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       11413
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       47245361167
189 High_Fly_Writes         0x003a   098   098   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   071   043   045    Old_age   Always   In_the_past 29 (0 96 29 27 0)
194 Temperature_Celsius     0x0022   029   057   000    Old_age   Always       -       29 (0 18 0 0 0)
195 Hardware_ECC_Recovered  0x001a   034   024   000    Old_age   Always       -       231061819
197 Current_Pending_Sector  0x0012   093   093   000    Old_age   Always       -       322
198 Offline_Uncorrectable   0x0010   093   093   000    Old_age   Offline      -       322
199 UDMA_CRC_Error_Count    0x003e   200   197   000    Old_age   Always       -       1807
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       24840 (66 156 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1260749126
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       909000527

```
```

$ sudo smartctl -l selftest /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-39-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     23941         220990286
# 2  Extended offline    Completed without error       00%      8133         -
# 3  Extended offline    Aborted by host               90%      8129         -
# 4  Short offline       Completed without error       00%      8128         -
# 5  Short offline       Aborted by host               60%      8128         -
```

---

### Post by mastablasta on 2018-11-15
looks like you have a bit of overheating: [COLOR=#000000][FONT=&amp]190 Airflow_Temperature_Cel 0x0022   071   **043**   045    Old_age   Always   In_the_past 29 (0 96 29 27 0)

also even if SMART is OK the disk may still be failing. there are some parameters that are not tested by smart. i used to have a clicking sound and it failed to boot sometimes, yet smart was ok. after i replaced the disk it all works flawless.[/FONT][/COLOR]

---

### Post by Autodave on 2018-11-15
Definitely an overheating issue.  Is this a laptop or desktop?  Spinning or SSD?

---

### Post by deadflowr on 2018-11-15
Your reallocated sector count is too high, a typical sign of imminent failure.
Couple that output with both current pending sector count, which deals with the remapping of those bad sectors and the online uncorrectable count, 
neither of which should ever be above zero.

(A handful of reallocated sectors is fine, but the current pending sector count means there are sectors on the disks that cannot be properly remapped,
which usually means you've hit the threshold of usable spare sectors or other serious issues)

And I also agree about the overheating problems as well,
IMO,
I'd suggest you drop the disk asap.

---

### Post by QIII on 2018-11-15
While I'm sure we all hate to spend your hard-earned money for you, we recognize that the risk of data loss may far outweigh the cost of a new device.  Your cost is not taken lightly.

I have to +1 the idea of replacement.  Soon ... yesterday if possible.

---

### Post by mdonders on 2018-11-15
This is a relatively old 1TB disk in a desktop. Is there something wrong with the airflow in the case or its just something wrong with the disk?

Running sensors gives this output.
```

$ sensors
asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +31.5°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +85.0°C)

```

---

### Post by rbmorse on 2018-11-15
The temp business could be spurious.  Or not. 

However, pay attention to deadflowr's post.

---

