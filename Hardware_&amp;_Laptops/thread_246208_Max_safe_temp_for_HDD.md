---
title: "Max safe temp for HDD?"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by srunni on 2006-08-28
Hi,

I just got a new 500 GB Hitachi Deskstar 7K500, so that I wouldn't have to partition my 250 GB HD for Windows/Linux. I'm running Linux on the new HDD, and I'm on it significantly more than I'm on Windows. After reading some reports of this HDD going to very high temperatures, I was wondering what the maximum safe temperature for a HDD is. This one has the problem of getting very hot because it has 5 platters instead of an increased density for each platter. I have 4 HDD slots in my computer, and I've put the 2 HDD's as far away from each other as possible. Also, my computer (a VAIO; yeah yeah yeah, I'll build my own computer next time :D) has a hole in the middle of the tower, giving the HDD's direct access to open air. The CPU etc. (which is at the opposite side of the tower) has a liquid cooling system to ensure quietness and a low temperature at the same time. Anyway, is this enough to keep the HDD cool enough? I want to make sure this drive lasts for a while ;)

---

### Post by funchords on 2006-08-28
30-50C under normal operations.

If a device goes to 60C-65C under stress, I generally watch it for issues but I don't necessarily pull the fire alarm.

If it's above 50 without stress or above 65 with stress, then I'll take it offline.

I've got a hot drive right now.  It idles at about 50. :-(

This is all "rule-of-thumb" to me. Sometimes equipment is designed and tested by the manufacturer to run in hotter ranges.  This info should be found in the specifications that came with the drive or on their website.

---

### Post by srunni on 2006-08-29
Well, absolutely nothing came with the drive lol, it was just in a plastic container. I guess I'll check Hitachi site. What would be the best way to determine the actual current temperature of my hard drive?

---

### Post by funchords on 2006-08-29
**sudo apt-get install smartmontools**

**sudo smartctl -a /dev/hda**
```
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 8 family
Device Model:     Maxtor 6E040L0
Serial Number:    E16BSWAE
Firmware Version: NAR61590
User Capacity:    41,110,142,976 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue Aug 29 12:04:19 2006 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (1021) seconds.
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
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  17) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   220   219   063    Pre-fail  Always       -       10962
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       179
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   251   245   187    Pre-fail  Always       -       59884
  9 Power_On_Minutes        0x0032   206   206   000    Old_age   Always       -       1005h+43m
 10 Spin_Retry_Count        0x002b   250   246   157    Pre-fail  Always       -       3
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   253   253   000    Old_age   Always       -       174
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       157
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       340
**194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       40**
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       18309
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       2
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       4
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   250   246   000    Old_age   Always       -       3
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   187   187   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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
```

robb@TOPOL016:~$

---

### Post by srunni on 2006-08-29
> 194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       40

Does that mean the temperature is 40 degrees?

EDIT: Using ```
sudo smartctl -a -d ata /dev/sdb3
```, I got ```
194 Temperature_Celsius     0x0002   114   114   000    Old_age   Always       -       48 (Lifetime Min/Max 24/53)
```

Seems that my HDD temperature is 48 degrees. Also, it seems that the HDD which was originally in my computer (a 250 GB) is at 39 degrees. Since I'm not even accessing it right now, I'm guessing it's gotten a lot hotter than that, so maybe I'm OK.

---

### Post by funchords on 2006-08-29
Yes, you've got it.

I wouldn't worry about 48C at all.  Sounds normal.  For comparison, what does 

**acpi -V **

say (if anything) about the temp inside your box?  Surprisingly, my drive runs cooler than my motherboard sensor.

---

### Post by srunni on 2006-08-29
Well, I just checked the Hitachi page, and the "Ambient Temperature" while in operation is 55 degrees. Does that mean it's safe for it to go up to 55 degrees?
EDIT: ```
acpi -V
``` results in ```
No support for device type: thermal
``` I'm guessing this means that my box doesn't support checking CPU temperature. But I'm guessing it's pretty low, because one of the advantages of this computer is the liquid cooling system it uses.

---

### Post by funchords on 2006-08-29
> **srunni said:**
> Well, I just checked the Hitachi page, and the "Ambient Temperature" while in operation is 55 degrees. Does that mean it's safe for it to go up to 55 degrees?No, it means its designed/tested to operate in an environment that reaches 55 degrees.

However, I think you could assume that if it's rated at 55C ambient, that it is safe to operate to similar internal temperatures.

---

### Post by srunni on 2006-08-29
Well, are there any ways to lower the temperature of a hard drive through purely software modification?

---

### Post by funchords on 2006-08-29
I think you're fine.  No need to do anything.

But just in case you someday need to ...

Reduce fragmentation by using an efficient filesystem.  If you formatted it with ext2/ext3, you've already done that.

Use power management to spin down idle drives, but this technique can backfire as it's often easier on the hardware to keep a platter spinning than  it is to keep spinning it up from a stopped state.  The advice here is to wait for several minutes of idle time before allowing a spin-down.

Use enough physical memory so that the system does not need to use a swap-file except in very unusual circumstances.  (Okay, that one is not exactly "purely software.")

---

### Post by srunni on 2006-08-29
The swap file thing isn't a problem: I have 1 GB RAM. I'll be sure to try out the power down thing. I didn't bother to look at that at all, since it's usually meant for laptops to make the battery last longer.

---

