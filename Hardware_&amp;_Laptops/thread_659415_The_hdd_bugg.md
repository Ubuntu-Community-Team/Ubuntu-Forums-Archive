---
title: "The hdd bugg?"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Lulle on 2008-01-05
Hi!
I got a Desktop computer with 2 sata hdd's.

And when I'm going to check if I got the hdd bugg I typ this in the terminal:
```

sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb

```

I don't get up information from line 191,192,193.
So how do I know if I got the bugg?

I just got this from the sata 1 disk who is like 4 mounths old:
```

  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   253   189   021    Pre-fail  Always       -       2300
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       177
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3293
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       173
190 Temperature_Celsius     0x0022   060   047   045    Old_age   Always       -       40
194 Temperature_Celsius     0x0022   110   097   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

```


And I got this from the sata2 disk who is like 3weeks old:
```

  1 Raw_Read_Error_Rate     0x000f   253   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   015    Pre-fail  Always       -       2560
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       120
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       492
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       107
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       16729
187 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   070   056   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   148   106   000    Old_age   Always       -       30
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       16729
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   253   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   100   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0032   253   253   000    Old_age   Always       -       0

```

I have my computer on 24/7/365.
Sata disk 1 I got OS and apps on.
And sata disk 2 I download and upload stuff to all the time 24/7/365.

So what do you think of my logg?
Shod I use the fix?
And if I shod use the fix, which fix shod I use?

---

### Post by nick_h on 2008-01-06
Different drive manufacturers implement smart in differnt ways.  I'm not sure if you can know if your drive is spinning down too aften without the load cycle count.

The second drive seems to have a rather high value for the start/stop count consdiering it is on 24/7.  (approx. every 4 hours)

---

