---
title: "65537 Bad Sectors"
date: 2012-09-02
forum: Hardware
---

### Post by DeanM1134 on 2012-09-02
While recently trying to add a second hard drive to my computer, (a 500 GB SATA that unfortunately doesn't work at all) I booted off my LiveUSB and noticed that on my main 1TB Drive I have 65,537 bad sectors and disk utility is giving me a warning about it. My computer's still under warranty so I could get a new drive, but I want to know how concerned I should be first?

Also if anybody could help me with the problem with the 500GB that'd be great. there should be nothing wrong with it as it's just been sitting in it's packaging for ~6 or so months after a year or two of usage. When connect by it's self or alongside the main 1TB, the computer just hangs on the POST delay after being turned on and makes no attempt to boot anything. If I connect the drive after booting into Windows 7/Ubuntu it just isn't detected.

---

### Post by ahallubuntu on 2012-09-02
You could post the GSmartControl (S.M.A.R.T.) report for both drives here (or smartctl, the text version).  "Bad sectors" could mean a lot of things, though that of course is an extremely high number if real.

You can install GSmartControl/smartmontools in a live CD session.

---

### Post by DeanM1134 on 2012-09-02
This is the output for the 1TB main drive:
```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDS721010CLA632
Serial Number:    JP2940J83XASRV
LU WWN Device Id: 5 000cca 396f72950
Firmware Version: JP4OA41A
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Sep  2 17:46:10 2012 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 9396) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 157) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   096   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0027   136   100   054    Pre-fail  Always       -       93
  3 Spin_Up_Time            0x0023   185   100   024    Pre-fail  Always       -       205 (Average 205)
  4 Start_Stop_Count        0x0022   100   100   000    Old_age   Always       -       595
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       1 (0, 1)
  7 Seek_Error_Rate         0x002f   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   140   100   020    Pre-fail  Offline      -       30
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       1752
 10 Spin_Retry_Count        0x0033   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       595
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0032   099   099   000    Old_age   Always       -       131071
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   099   091   000    Old_age   Always       -       38274001
189 High_Fly_Writes         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   058   000    Old_age   Always       -       37 (Min/Max 37/39)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       595
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       595
194 Temperature_Celsius     0x0002   162   146   000    Old_age   Always       -       37 (Min/Max 18/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 0
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1752         -
# 2  Extended offline    Aborted by host               70%      1751         -
# 3  Extended offline    Interrupted (host reset)      90%         1         -

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

### Post by DeanM1134 on 2012-09-02
The second 500GB drive that I was trying to connect doesn't show up at all. BIOS doesn't even detect it so I'm declaring it dead.
After reading over it a bit myself, it sounds like it's in terrible shape. I don't understand the Old-Age tags either, it's only about 6 months old.

---

### Post by DeanM1134 on 2012-09-02
Bumping because now I'm really worried

---

### Post by ahallubuntu on 2012-09-02
Relax.  S.M.A.R.T. attributes have types: "pre-failure," "old age," etc.  That only describes the type of attribute it is, not whether it has failed or not.  A brand new drive would have exactly the same descriptors.

Where did you get the 65537 number?  Your S.M.A.R.T. output shows only two worrisome attributes: the Reallocated Sector Count (1) and   Reallocated Event Count (1).  That is not catastrophic at all - it means one sector on your drive failed (the "Reallocated event") but the drive firmware acted to deactivate and replace it with a spare sector.  Every modern drive has some spare sectors, so that if a few sectors fail, the drive can continue to function with spares.  It's not ideal to use spare sectors, because they are probably located in a different part of the drive than the adjacent sectors to the failed one, but it doesn't mean the end of the world.

The more common bad attribute is the "Pending Sector Count" - that is, the number of bad sectors that the drive firmware hasn't yet been able to deal with - and your count is 0.  That's good.

Having a few reallocated (spare) sectors in use on an older drive isn't unusual.  I use a few older servers that are not doing anything important (media servers) that have a few reallocated sectors.  The more worrisome issue is if the number of reallocated sectors INCREASES over time.  That indicates the drive surface is gradually failing.

This drive of yours isn't that old - you probably could get it replaced under warranty.  But if you do that, be prepared to get all data off of it before sending it back under RMA.  Ideally, they'd send you a new drive, you could clone the old one to it, wipe the drive (zero out your data), then send the old one back.  Sometimes they will let you do that if you are willing to leave a deposit for the 2nd drive while you have two.

Or, you could just go with the old drive and watch the reallocated sector count and not worry about it unless the number starts to go up.  It could last many years without the number increasing.

---

### Post by ahallubuntu on 2012-09-02
FYI, you can also run S.M.A.R.T. tests with SmartMonTools.  There are only a few tests; I'd run the Extended Test.  (Will probably take 2-3 hours.)  It's a non-destructive test, run almost entirely by the drive's firmware, while your computer waits for the test to complete.  Still, it should go without saying that you ought to have everything on this 1TB drive backed up anyway.  Drives can start to fail without warning and it's not uncommon for people to lose everything on a failed drive.

GSmartControl has a nicer interface than smartctl for running these tests - it's a graphic interface to smartctl, actually, and pretty nice.  If you use that and look at the Attributes, you should see the two reallocation attributes I pointed out above highlighted in red.  If you see others (that I missed) highlighted in red besides those two, let me know.

---

### Post by DeanM1134 on 2012-09-02
I got the 65537 from Disk Utility. I opened up the Hard Disk's SMART Data for the heck of it and it says:
Bad Sectors: 65537 Bad Sectors
Overall Assessment: Disk has a few bad sectors with a green circle next to it
     The second part is what confused me, acting like 65537 was a good number

I can post a picture of it if necessary

---

### Post by ahallubuntu on 2012-09-02
From personal experience, I trust GSmartControl (SmartMonTools) and not Ubuntu's disk utility.  It's always possible that tool is reading the wrong S.M.A.R.T. field.  You'll have to  make your own judgement.

You could still run the S.M.A.R.T. extended test I recommended.

---

### Post by DeanM1134 on 2012-09-02
Will do, thanks a lot.

---

### Post by ahallubuntu on 2012-09-02
I don't know why this didn't occur to me the first time I saw the number of bad sectors - but 65537 isn't a random number.  In HexDecimal (used internally by most of these programs), 65536 decimal is 10000.  Add one (the real number of reallocated sectors) and you get 10001 (that's not a binary number  it's ten thousand-and-one base 16).  In other words, the Ubuntu Disk Utility must be misreading the S.M.A.R.T. value and adding an extra byte or two as the most significant bytes.  Maybe your particular disk only gives two bytes (16 bits) but the Disk Utility expects four bytes or something.

Probably a bug that should be filed against Disk Utility if not already.

---

