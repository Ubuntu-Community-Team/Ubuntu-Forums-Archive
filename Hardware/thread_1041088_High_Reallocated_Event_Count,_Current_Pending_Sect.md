---
title: "High Reallocated_Event_Count, Current_Pending_Sector and Offline_Uncorrectable values"
date: 2009-01-16
forum: Hardware
---

### Post by tux_mark_5 on 2009-01-16
Hello,

I've recently bought a dell XPS M1730 laptop, which has two 200 GB HM201JJ hard drives. The problem is the values of smartctl:

These are OLDER (about 16 days old of the new laptop) smartctl values of the first drive:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       8
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2937
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       10104
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Half_Minutes   0x0032   099   099   000    Old_age   Always       -       9h+02m
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       36
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   115   088   000    Old_age   Always       -       41 (Lifetime Min/Max 20/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1291
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       45
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       86
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0
254 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       33554432

```

And these are of the second:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       7
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2875
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       8446
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Half_Minutes   0x0032   099   099   000    Old_age   Always       -       9h+02m
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
191 G-Sense_Error_Rate      0x0032   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       17
194 Temperature_Celsius     0x0022   118   091   000    Old_age   Always       -       40 (Lifetime Min/Max 21/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       981
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       17
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       71
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0
254 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       33554432

```

These are CURRENT values of the first drive:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       14       
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2937     
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       10655    
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0        
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1258     
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       62       
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2        
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       23       
194 Temperature_Celsius     0x0022   124   088   000    Old_age   Always       -       38 (Lifetime Min/Max 16/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       11597                      
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       131                        
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       248                        
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0                          
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0                          
254 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       33554432

```

These are CURRENT values of the second drive:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       10       
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       3000     
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       8836     
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0        
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1249     
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       58       
191 G-Sense_Error_Rate      0x0032   252   252   000    Old_age   Always       -       0        
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       22       
194 Temperature_Celsius     0x0022   124   091   000    Old_age   Always       -       38 (Lifetime Min/Max 16/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       10419                      
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       90                         
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       135                        
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0                          
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0                          
254 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       33554432

```

I am using kubuntu 8.10 with latest updates installed.
Kernel is: 2.6.27-9-server (the same thing happens with generic kernel too; I'm using server because of the PAE)

Also I have laptop mode enabled in /etc/default/acpi-support

Also both hdd's sometimes make very weird noise (I've recorded it with my mp3 player, so sorry for the poor quality).
It happens ONLY when pc is starting up (exactly when GRUB closes and linux starts to boot) OR when the laptop is shutting down.
The weird thing about this is that BOTH hard drives are always making the noise at the same time.

I haven't noticed this weird behavior with WinXP SP3.

Any help/comments/suggestions/ideas would be really appreciated.
Thank you very much.

Audrius

---

