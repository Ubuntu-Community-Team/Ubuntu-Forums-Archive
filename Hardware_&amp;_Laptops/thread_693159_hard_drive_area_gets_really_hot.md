---
title: "hard drive area gets really hot"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by speel on 2008-02-10
after opening a few apps and leaving the laptop on for a good 15-20 mins the hard drive area of my laptop gets really hot..i used to run mandriva and didn't get this.. 
any solution perhaps?

---

### Post by mzembe on 2008-02-10
Check your temps with hdparm (mostly for Hitachi drives?).
```
root@m70-numbar1:/# hdparm -H /dev/sda

/dev/sda:
 drive temperature (celsius) is:  36
 drive temperature in range:  yes

```

---

### Post by speel on 2008-02-10
/dev/sda:
 HDIO_DRIVE_CMD(hitachisensecondition) failed: Input/output error


btw its a hp pavilion dv6000 series

---

### Post by mzembe on 2008-02-10
Earlier I installed smartmontools with apt and got some additional information, It showed mean lifetime temperature and other statistics (like reallocated sectors, etc.) with a
```
root@m70-numbar1:/home/brian# smartctl -d ata -a /dev/sda
```

---

### Post by speel on 2008-02-10
here is the output

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1600BEVS-60RST0
Serial Number:    WD-WXE807A29055
Firmware Version: 04.01G04
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 10 21:20:02 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (6780) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  87) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   188   187   021    Pre-fail  Always       -       1583
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1001
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1121
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       723
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       4295032833
190 Temperature_Celsius     0x0022   050   032   040    Old_age   Always   In_the_past 50
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       211
193 Load_Cycle_Count        0x0032   191   191   000    Old_age   Always       -       28885
194 Temperature_Celsius     0x0022   097   079   000    Old_age   Always       -       50
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 4
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 4 occurred at disk power-on lifetime: 477 hours (19 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 ff cf b8 40  Error: UNC 8 sectors at LBA = 0x00b8cfff = 12111871

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff cf b8 02 00      00:22:05.867  READ DMA EXT
  35 00 60 a7 98 21 0a 00      00:22:05.866  WRITE DMA EXT
  35 00 00 a7 97 21 0a 00      00:22:05.865  WRITE DMA EXT
  35 00 08 3f 00 5e 00 00      00:22:05.865  WRITE DMA EXT
  35 00 08 ef f0 2f 0a 00      00:22:05.865  WRITE DMA EXT

Error 3 occurred at disk power-on lifetime: 477 hours (19 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 11 94 35 40  Error: UNC 8 sectors at LBA = 0x00359411 = 3511313

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 11 94 35 0a 00      00:21:12.407  READ DMA EXT
  35 00 00 87 0a 01 0a 00      00:21:12.405  WRITE DMA EXT
  35 00 00 87 09 01 0a 00      00:21:10.580  WRITE DMA EXT
  35 00 00 87 08 01 0a 00      00:21:10.579  WRITE DMA EXT
  35 00 00 87 07 01 0a 00      00:21:09.057  WRITE DMA EXT

Error 2 occurred at disk power-on lifetime: 125 hours (5 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 d7 81 c7 e0  Error: UNC 8 sectors at LBA = 0x00c781d7 = 13074903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 d7 81 c7 11 00      02:39:08.338  READ DMA EXT
  ca 00 08 d7 1d 03 00 00      02:39:07.586  WRITE DMA
  ca 00 38 9f 1d 03 00 00      02:39:07.585  WRITE DMA
  35 00 28 a7 5b ca 11 00      02:39:07.585  WRITE DMA EXT
  35 00 10 cf 49 c7 11 00      02:39:07.585  WRITE DMA EXT

Error 1 occurred at disk power-on lifetime: 53 hours (2 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1f f8 2c 40  Error: UNC at LBA = 0x002cf81f = 2947103

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 1f f8 2c 02 00      05:03:58.411  READ DMA EXT
  35 00 08 a7 03 00 00 00      05:03:58.411  WRITE DMA EXT
  35 00 08 4f 03 00 00 00      05:03:58.411  WRITE DMA EXT
  35 00 00 07 f7 2c 02 00      05:03:58.409  WRITE DMA EXT
  35 00 00 07 f6 2c 02 00      05:03:58.408  WRITE DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1074         -
# 2  Short offline       Completed without error       00%      1073         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

anthony@anthony-laptop:~$

---

### Post by Yellow Pasque on 2008-02-11
I'm not sure what your temp is there. Try this.
```
sudo apt-get install hddtemp lm-sensors sensors-applet
```
Now you should be able to right-click on the bar at the top of you screen and select 'Add to Panel'. Under the Systems & Hardware section should be a Hardware Sensors Monitor App. Add that. Now right click on it and select Preferences. Under the Sensors tab should be a pulldown list  with the HD(s) listed. Select the appropriate one and now you can monitor the temp of your HD. Most are rated to at least 55C, so don't panic unless it's exceeding that.

---

### Post by speel on 2008-02-11
> **Temüjin said:**
> I'm not sure what your temp is there. Try this.
```
sudo apt-get install hddtemp lm-sensors sensors-applet
```
Now you should be able to right-click on the bar at the top of you screen and select 'Add to Panel'. Under the Systems & Hardware section should be a Hardware Sensors Monitor App. Add that. Now right click on it and select Preferences. Under the Sensors tab should be a pulldown list  with the HD(s) listed. Select the appropriate one and now you can monitor the temp of your HD. Most are rated to at least 55C, so don't panic unless it's exceeding that.

ah thanks, yea its at 49c so i guess i'm safe :)

---

### Post by mzembe on 2008-02-13
I fixed a laptop once, well - twice, the power jack had been repaired previously and when I resoldered it - just figured it was weak from the original repair. It didn't last and I had to look at it a second time. The board was fried, I had to sand and remove the corner of the board it was so cooked. I was shocked that it actually came back on, the board had a lot of heat damage there, and overall, the whole thing stayed hot. The fans worked, the heat fins were all clear... 
While I was working on the board I had the battery charging separately just in case the power connector area was beyond hope but just maybe it would POST from the remote battery connectors. It worked anyways though, and when I went to install the battery that had been sitting removed from the charger for an hour or so - it was still unusually hot. A couple of the cells had internally shorted (likely, they had been that way for months). I dissected the battery into cell pairs and within 30 minutes all of the pairs were cooled except one - slightly later they were dead relative to the remaining charge in the others and within hours they cooled with no significant charge left... 
These two shorted cells caused the laptop to constantly be in a state of charge, they created a ton of heat just continually discharging which was why the whole thing stayed so hot... Normally, you just figure the power cord has been tripped over too many times..
Sometimes, things that generate heat, like the drive or cpu, etc., are understood/designed to operate at outrageous temperatures relative to reasonable environmental temperatures so they can perform a rapid exchange but when you have something unrelated like the malfunctioning battery exaggerating normal room temperature they have to be a lot hotter for the design to adapt - like a cascading effect? Maybe. Anyways, you might want to see if running it without a battery makes a difference.

---

