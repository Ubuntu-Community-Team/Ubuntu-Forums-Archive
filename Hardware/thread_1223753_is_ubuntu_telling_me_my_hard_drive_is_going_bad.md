---
title: "is ubuntu telling me my hard drive is going bad?"
date: 2009-07-26
forum: Hardware
---

### Post by pythonscript on 2009-07-26
I read about using the smartmontools to monitor the health of my hard disk, and when I ran ```
sudo smartctl -a /dev/sda
``` I get this output:

```
 ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   099   098   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   098   098   020    Pre-fail  Always       -       2075
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       189117424
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3587
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   099   099   020    Pre-fail  Always       -       1669
184 Unknown_Attribute       0x0033   100   253   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x003a   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   096   000    Old_age   Always       -       65669
189 High_Fly_Writes         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   046   019   040    Old_age   Always   In_the_past 54 (3 150 81 14)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       517
192 Power-Off_Retract_Count 0x003a   100   100   000    Old_age   Always       -       782
193 Load_Cycle_Count        0x0012   070   070   000    Old_age   Always       -       61143
194 Temperature_Celsius     0x003a   054   081   000    Old_age   Always       -       54 (0 14 0 0)
195 Hardware_ECC_Recovered  0x003e   066   060   000    Old_age   Always       -       159995135
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
```According to the link, which was referring to hp pavilion laptops, same type as the computer I'm using, the Load Cycles Count should be around 200 for a new drive, and slowly decrease as the health of the drive goes bad. Am I reading these results wrong? My load cycles count is around 70! and this computer almost exactly 1 year old. Is my hard drive already "getting old" and going to die on me soon, or am I not reading the test properly? Thanks! If anyone can tell me any more general information from these results that I should know, that'd be great too. 

EDIT:  Here's the link I'm talking about, too:
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#disk](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#disk)

---

### Post by 67GTA on 2009-07-26
Smart values can be hard to read. VALUE is supposed to be the current value(different models vary on how this is calculated). WORST is the lowest seen by the disk so far. THRESH is the value that when reached in a pre-fail attribute will trigger a "failed SMART status". WHEN_FAILED is self explanatory. You only have one fail sometime in the past with 
Airflow_Temperature_Cel. The value during the test was 54C. Most of the time you want to read the RAW_VALUE column. It usually represents the actual reading at the time of the test. The most important value to watch IMHO is the Reallocated_Sector_Ct. It counts how many sectors the 
 disk was unable to read and had to replace. Don't freak out, yours looks fine:D

---

### Post by 67GTA on 2009-07-26
I have no idea what happened to the indentation on the above post:confused:

---

### Post by 67GTA on 2009-07-26
You can install gsmartcontrol. It is a GUI frontend for smartmontools. It has tooltips that will explain what most things are when you hover over them.  [http://download.opensuse.org/repositories/home:/alex_sh/xUbuntu_9.04/i386/gsmartcontrol_0.8.4+nmu1_i386.deb](http://download.opensuse.org/repositories/home:/alex_sh/xUbuntu_9.04/i386/gsmartcontrol_0.8.4+nmu1_i386.deb)

---

### Post by pythonscript on 2009-07-31
I appreciate the help, and gsmartcontrol is a nice little utility. Thanks!

---

