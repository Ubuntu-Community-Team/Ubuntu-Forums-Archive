---
title: "Unsafe shutdown of HDD"
date: 2016-12-06
forum: Hardware
---

### Post by l3v2 on 2016-12-06
Hi everyone,

I sincerely hope someone can help me out here.
I've bought a 2,5" Toshiba hdd (SATA II,  MQ01ABD100) mainly for storage for my desktop pc. I've installed Xubuntu 16.10 on it (because Win10 started to p*** me off) and after a few weeks I've noticed that ubuntu does not properly prepare the drive for the shutdown sequence. It simply seems that it's not parking the heads and it appears that only the power is cut. You can hear the heads slamming into parking position while the platters are spinning down noisily. The weird thing is, this does not happen regularely, and it only affects the 2,5" drive. The drive is only a couple of weeks old and the retract count is rising. It reached 16 yesterday... 

I've got 3 drives in my pc. #1 Crucial M4 128GB, #2 3,5" WD blue EALX 1 TB, (by now more than 13k power on hours without problems, 50 retract counts), and #3 the Toshiba 2,5" MQ01ABD100
On the ssd I've kept win10 for gaming, the WD is purely for storage and the 2,5" was intended for Ubuntu mainly.

Somewhere I've read, that cutting power / the unsafe power-off of a hdd decreases its lifetime by a factor of about 10. Is that true?

The only workaround is rebooting into windows in order to shut down the pc from there. Under windows this problem does not happen at all. ever. Why is that?? I wanted to use ubuntu as productive system, but this is a major no-go for me.
I've searched for quite a while now, and the only information to similar problems dates back to 2008 / 2009, also related to ubuntu and the unsafe power-off of 2,5" usb hdds and laptop discs. I thought the issue has been resolved 8 years later...?

---

### Post by l3v2 on 2016-12-08
anyone?

is there a way to manually prepare the disk for shutdown, i.e. forcing the disk to park the heads before the power is cut?
in the german ubuntu forum i've already asked the same and nobody could really help me. a guy suggested modifying the hdparm.conf from

apm_battery = 127
to
apm_battery = 254

but he thought i was using a laptop, which i don't at the moment. also i'm actually afraid to mess with hdparm (i'm a noob...)
rebooting to windows, only for the purpose of shutting down my pc is more than annoying and no permanent solution.
please help :(

---

### Post by l3v2 on 2016-12-08
i've checked smartctl again. the load cycle count for the 2,5" drive is really high for its age. is that normal??

> 

[LIST]
[*]Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model: **    TOSHIBA MQ01ABD100**
Serial Number:    56D6PFKTT
LU WWN Device Id: 5 000039 702404aa9
Firmware Version: AX1P1A
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Dec  8 09:53:46 2016 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled 
[*]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1695
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       161
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       399
 10 Spin_Retry_Count        0x0033   103   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       93
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 **Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       16**
193 **Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1387**
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       30 (Min/Max 16/38)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       173
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       265
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0 
[/LIST]



compared to the 3,5" drive


> 
[LIST]
[*]Model Family:     Western Digital Blue
Device Model:     **WDC WD10EALX-009BA0**
Serial Number:    WD-WCATR6765519
LU WWN Device Id: 5 0014ee 2b06a9559
Firmware Version: 15.01H15
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Dec  8 09:52:52 2016 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled 
[*]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   177   173   021    Pre-fail  Always       -       4141
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2394
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 **Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13676**
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2352
192 **Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       50**
193 **Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2343**
194 Temperature_Celsius     0x0022   113   098   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0 
[/LIST]


---

### Post by l3v2 on 2016-12-11
*bump* triple checked it again. it's only the laptop hdd. the retract count went up again. interestingly, the load cycle count as well. i assume, i can counter the load cycle problem by more or less disabling acpi via hdparm for /dev/sdc, right? but what about the initial problem? anyone? please?

---

