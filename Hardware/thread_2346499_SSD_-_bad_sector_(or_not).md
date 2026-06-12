---
title: "SSD - bad sector (or not)?"
date: 2016-12-15
forum: Hardware
---

### Post by jaarvidsen on 2016-12-15
i have a 2 month old Corsair Force LE SSD 960 gb

yesterday gnome-disks started reporting one bad sector,  see [http://i.imgur.com/gezSepq.png](http://i.imgur.com/gezSepq.png) (ignore the temps, its just lm-sensors or something not working for this particular ssd model - its deffo not 100C)

after some research i decided to run badblocks as follows:
sudo badblocks -v /dev/sda
Checking blocks 0 to 937692503
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)


so what now? one reports an error, the other none. what should i do?

---

### Post by slickymaster on 2016-12-15
*Thread moved to **Hardware**.*

---

### Post by kpatz on 2016-12-15
Install smartmontools with ```
sudo apt-get install smartmontools
``` then in a terminal run ```
sudo smartctl -a /dev/sda
``` and paste the results here.

---

### Post by jaarvidsen on 2016-12-15
here are the results:
--------------
```
sudo smartctl -a /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.8.0-30-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Device Model:     Corsair Force LE SSD
Serial Number:    162980210001055500E5
Firmware Version: SAFC12.2
User Capacity:    960.197.124.096 bytes [960 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Dec 15 19:55:11 2016 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   30) seconds.
Offline data collection
capabilities:              (0x79) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (   2) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0013   100   100   050    Pre-fail  Always       -       1
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       715
 12 Power_Cycle_Count       0x0012   100   100   000    Old_age   Always       -       172
162 Unknown_Attribute       0x0003   099   099   000    Pre-fail  Always       -       4294967933
170 Unknown_Attribute       0x0002   100   100   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       1
174 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       30
181 Program_Fail_Cnt_Total  0x0012   100   100   000    Old_age   Always       -       1
187 Reported_Uncorrect      0x0012   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0012   100   100   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0023   070   070   030    Pre-fail  Always       -       30 (Min/Max 30/30)
196 Reallocated_Event_Count 0x0002   100   100   010    Old_age   Always       -       1
218 Unknown_Attribute       0x000b   100   100   050    Pre-fail  Always       -       0
231 Temperature_Celsius     0x0013   100   100   000    Pre-fail  Always       -       100
241 Total_LBAs_Written      0x0012   100   100   000    Old_age   Always       -       698
242 Total_LBAs_Read         0x0012   100   100   000    Old_age   Always       -       1796

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       709         -
# 2  Short offline       Completed without error       00%       708         -
# 3  Short offline       Completed without error       00%        54         -

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

---

### Post by kpatz on 2016-12-15
Looks like the drive reallocated one sector, so the count in gnome-disks is accurate.  The bad block scan found no more, since the bad one was reallocated from spare and is no longer mapped in active storage.

As long as it stays at 1, you should be ok.  If you start seeing more, it's a sign the drive is faulty/failing.

---

### Post by jaarvidsen on 2016-12-15
thanks !
what would happen if i zero'ed the disk, using dban or something and reinstalled?

edit, btw i just remembered that this started happening yesterday just after i had the corsair ssd unplugged for a bit cos i needed the sata cable for another drive as i was cloning my windows mechanical hdd onto another ssd using clonezilla (which worked great btw)

---

### Post by kpatz on 2016-12-15
There's no need.  The bad sector was reallocated by the drive so it's no longer "there" from the OS's perspective.  Zeroing the disk is just adding wear and tear to the flash cells.  Unless you're having issues with your install I'd just leave it, and run smartctl once in a while to make sure the drive isn't picking up new bad sectors.

Oh, and do backups!

---

### Post by jaarvidsen on 2016-12-15
> **kpatz said:**
> There's no need.  The bad sector was reallocated by the drive so it's no longer "there" from the OS's perspective.  Zeroing the disk is just adding wear and tear to the flash cells.  Unless you're having issues with your install I'd just leave it, and **run smartctl once in a while** to make sure the drive isn't picking up new bad sectors.

Oh, and do backups!

so checking gnome-disks is not enough?
i do backup almost daily onto a 2tb usb3 hdd

thanks for your help!
about to migrate into a node 202 so ssd problems came very inconveniently as ive got some hw to buy and spending a fortune on another 1tb ssd (anything less just wont do) would be a problem

---

### Post by kpatz on 2016-12-15
There should be a warranty on the drive if it fails.  You said it's only 2 months old, right?

I don't know how gnome-disks "detects" bad sectors.  If it's reading the SMART data from the drive, it will reflect the number of sectors the drive reports as bad.  smartctl reports from the drive's SMART data.  If you see gnome-disk report more sectors as bad in the future, run smartctl and see if the numbers match up.  And then backup and replace the drive since at that point it's dying.

---

