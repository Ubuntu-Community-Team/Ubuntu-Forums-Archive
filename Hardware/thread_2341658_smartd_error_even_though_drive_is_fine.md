---
title: "smartd error even though drive is fine?"
date: 2016-10-30
forum: Hardware
---

### Post by SundaY82 on 2016-10-30
I created a raid1 volume containing two disks.
The raid is up and running but one of the disks keep showing up in syslog and I get an email once a day about it.

This line pops up once every 30min:
smartd[2088]: Device: /dev/sdb [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.

So I checked the disk with smartctl, see below.
As you can see there are 0 reallocated sectors. 
I ran both a short and a long test on the drive that passed.

What to do?

```
smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST4000DM000-1F2168
Serial Number:    XXXXXXXXX
LU WWN Device Id: 5 000c50 05014215b
Firmware Version: CC51
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Oct 30 14:04:16 2016 CET
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
data collection:                (  602) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x1085) SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   112   099   006    Pre-fail  Always       -       45357920
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       60
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   066   060   030    Pre-fail  Always       -       3801404
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       478
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       12
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   095   095   000    Old_age   Always       -       5
190 Airflow_Temperature_Cel 0x0022   061   050   045    Old_age   Always       -       39 (Min/Max 26/40)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       179
194 Temperature_Celsius     0x0022   039   050   000    Old_age   Always       -       39 (0 21 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       26912265077020
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       26398742239
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       25070858407

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       439         -
# 2  Short offline       Completed without error       00%       430         -

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

### Post by TheFu on 2016-10-30
Check the other disk.

Also, get your daily, versioned, backups to be perfect.  RAID solves 2 issues.  Versioned backups solve at least 1,000 issues, including failed RAID.

---

### Post by SundaY82 on 2016-10-30
Ok thanks for your reply but isn't really a solution/answer to my problem.
I know a raid doesn't make backups unnecessary.

The smartd output explicitly state that there is a problem with /dev/sdb and not some of the other disks in the server.
And they are all fine by the way.

---

### Post by TheFu on 2016-10-30
SMART data isn't always helpful. There aren't any industry standards for what any of the parameters mean. Once read that the USGovt required SMART, but didn't put any standards inplace, so we get whatever the vendor wants to provide.  They do change the meaning of some of the parameters, between different disk models.

```
smartd[2088]: Device: /dev/sdb [SAT], Failed SMART usage Attribute: 5 Reallocated_Sector_Ct.
```
Reread this a few times. Initially, it seems to say that there is a failure reallocating a sector.  Reading is again and again leads me to see the smartd part ... which says the SMART subsystem was having trouble with the attribute - doesn't say if that is reading or writing it, just that there is an issue.  Not really helpful.  Could mean that updating the relocated sector count isn't working.  Could mean that relocating sectors isn't work, so data corruption is happening.  I dunno.

I'd remove that disk from the array and if I didn't trash it immediately, it would be relegated to sneaker-net, unimportant, 5th-backup duties.  But drilling 5 wholes into disks is so much fun too!

---

### Post by SundaY82 on 2016-10-30
Ok, yeah looks like I have to get a new drive and replace it. Getting these warnings every day will drive me insane otherwise.
Its not Seagates "NAS" series either but the desktop series so would be better of getting another drive anyway for the long term.

---

### Post by TheFu on 2016-10-30
> **SundaY82 said:**
> Ok, yeah looks like I have to get a new drive and replace it. Getting these warnings every day will drive me insane otherwise.
Its not Seagates "NAS" series either but the desktop series so would be better of getting another drive anyway for the long term.

I've had bad luck with any non-enterprise drives from seagate since about 2007.  Finally had the last drive fail a month ago - lasted 2 yrs (only 1 yr warranty).  The other Seagate I got at the same time (I always get pairs), failed after 13 months.  Oddly, I have some 320G Seagates from 2005-ish still spinning, happily, doing their jobs.  I think something happened with Seagate with the 750G and larger disks that just isn't good.  I **NEVER** plan to buy another seagate.  If you look at the stats from 64K drives that Backblaze puts out every few quarters, you'll see why to avoid Seagates.  People seem to have forgotten that Seagate (corporate) lied for almost a year about issues with their drives in 2007 - denying all the claims of design flaws for a very long time. Eventually, enough people were vocal enough they admitted the issues.  Took me over 5 yrs before I bought another seagate. That one failed after 13 months.  Then, in a weak moment, I bought 3 more in 2014 ...  Been buying WD, Hitachi and Toshibas since 2007-ish ... none of those have failed before a "reasonable" life time of use. They have all exceeded my expectations, except the seagates.  "Fool me once ... "  Also, my experience isn't worth considering. It isn't a statistical sample and nobody should make decisions based on a sample size that is so very tiny.

OTOH .... [https://www.backblaze.com/blog/hard-drive-failure-rates-q2-2016/](https://www.backblaze.com/blog/hard-drive-failure-rates-q2-2016/) ... says don't buy 4TB or smaller Seagates and avoid 3TB drives from every vendor.  I'm over simplifying, but that's my takeaway.  I'll just avoid Seagates completely - easier that way.

---

