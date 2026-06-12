---
title: "How to check a hdd for bad sectors."
date: 2016-10-07
forum: Hardware
---

### Post by Blix775 on 2016-10-07
So one of my hard drives started causing all types of problems when I installed Ubuntu on it. I now have it as a secondary storage drive and so far it is working fine. I suspect it only has some sectors of it damaged and that the rest is fine. Is there any application I can use to check the sectors of the hdd? Or perhaps any commands I can use from Bash to check it out? Thanks in advanced.

---

### Post by frostschutz on 2016-10-07
install smartmontools, sudo smartctl -a /dev/yourdisk, run a long selftest (will take hours depending on size/speed of disk) sudo smartctl -t long /dev/yourdisk

If you can't make sense of the smartctl -a output feel free to post it here. The most important ones usually are Reallocated / Pending / Uncorrectable sectors, their raw value should be 0.

If there are errors the disk is no longer trustworthy - you should only use it for data you may afford to lose.

Also if there seem to be problems and the system is still running, you can check 'dmesg' for any error messages.

---

### Post by TheFu on 2016-10-07
I'd start with **fsck**, then move to **badblocks**.  Good backups are important at a time like that.

I've found smartctl to be less-than-useful unless you watch the numbers and compare weekly.  It can be useful if the data-rate-of-change is compared. Since there aren't any standards for what each output means across vendors or even within the same vendor's disks, only the changing data is useful to gleam anything.

For me, data is much more important than hardware, so once any storage device causes 1 tiny bit of worry or issues, I'll replace it and relegate that old disk to 4th level backups or sneaker net, temporary, use.

---

### Post by frostschutz on 2016-10-07
fsck = file system crunch killer. whatever fsck does you can't undo (unless you use an overlay like you do in raid recovery). if the storage medium is bad it will just make things worse. fsck is for filesystem errors on a logical level, it can't deal with hardware failure.

as for badblocks, if you let it write, it might increase damages even in the so-called non-destructive mode. in the read-only mode it serves no purpose.

if you suspect there are bad blocks you can use ddrescue to make a copy. does the same read test as badblocks while doing something useful with the data it managed to read (as in - create a copy).

smartctl is useful as it can tell you at a glance that the disk is bad provided the disk already knows about it. You don't need a data rate of change - a single reallocated sector is sufficient to know that the disk has serious issues and should be replaced asap.

everyone should have smartmontools run at least monthly checks on their disk. otherwise you will discover too late that your disk went bad.

---

### Post by TheFu on 2016-10-07
SMART data? 
[http://arstechnica.com/civis/viewtopic.php?t=1155702](http://arstechnica.com/civis/viewtopic.php?t=1155702)
[https://www.backblaze.com/blog/hard-drive-smart-stats/](https://www.backblaze.com/blog/hard-drive-smart-stats/) - seems I might need to rethink my use of SMART data.
 
A single relocated sector is NOT a huge issue. It can be years between relocations.  Any number less than 4 is probably ok according to the 40K disks running at backblaze. I have a disk with '7' as the number, it has had that value for about 4 yrs. 
The way that I'd swap disks varies depending on the criticality of the system.  A work system with an RPO of 15 minutes would have been swapped at the first sign of any issues as soon as a maintenance period could be scheduled (assuming non-hot-swap). At home, I wait for a failure. Have 60-120 days of backups, so massive data loss isn't a concern.

That backblaze article has this summary for SMART data in the comments:
```
SMART 5: Reallocated_Sector_Count       --> 1-4 keep an eye on it, more than 4 replace
SMART 188: Command_Timeout              -->  1-13 keep an eye on it, more than 13 replace
SMART 197: Current_Pending_Sector_Count --> 1 or more replace
SMART 198: Offline_Uncorrectable        --> 1 or more replace

```
If a cheap JMicron USB3-to-SATA converter inside a $99 4 disk array supported smartctl, then I'd be happy.  Alas, SMART data isn't always available.

---

### Post by frostschutz on 2016-10-07
> A single relocated sector is NOT a huge issue.

A relocated sector usually means the disk could no longer read it AND no longer write it. The  disk lost whatever data there was in that sector. Relocation only  happens when you try to write new data to it AND even that fails.

To me that seems like a serious indication that this piece of spinning rust has developed a mechanical failure. The problem is, you can hardly look inside and check, so you can only guess.

> It can be years between relocations.

It can also be days. There can be tons of dead sectors that just haven't been detected yet - without regular selftests, serious errors can go unnoticed for years.

Losing data is not acceptable to me. Keeping disks with dead sectors around is a gamble I'm not willing to make.

ymmv

---

### Post by colmax on 2016-10-07
To flag bad sectors you need to do a low-level format
This will entirely erase the disk/partition
Different filesystems will have different sector sizes (ntfs, vfat, ext4 etc)
Can take quite awhile cos the system writes/reads/deletes/rewrites/reads each sector
It will be worth it - maybe
Most disk utilities can do this
Just make sure you are prepared to lose all data on the partition/drive
Cheers

---

### Post by Blix775 on 2016-10-08
OK. Here is the output from Smartmontools:
> SMART Error Log Version: 1No Errors Logged


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




---

### Post by frostschutz on 2016-10-08
That output seems incomplete, which option did you use?

I expected it to look like this:

```

$ sudo smartctl -a /dev/sdg
smartctl 6.5 2016-05-07 r4318 [x86_64-linux-4.7.6] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA5897450
LU WWN Device Id: 5 0014ee 2b05daa2b
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Oct  9 00:43:13 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (39600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 381) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   204   168   021    Pre-fail  Always       -       4758
  4 Start_Stop_Count        0x0032   094   094   000    Old_age   Always       -       6710
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27814
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2648
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       136
193 Load_Cycle_Count        0x0032   195   195   000    Old_age   Always       -       15129
194 Temperature_Celsius     0x0022   124   103   000    Old_age   Always       -       26
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Selective offline   Completed without error       00%     27804         -
# 2  Selective offline   Completed without error       00%     27791         -
# 3  Selective offline   Completed without error       00%     27772         -
# 4  Selective offline   Completed without error       00%     27754         -
# 5  Selective offline   Completed without error       00%     27736         -
# 6  Selective offline   Completed without error       00%     27719         -
# 7  Selective offline   Completed without error       00%     27704         -
# 8  Selective offline   Completed without error       00%     27688         -
# 9  Selective offline   Completed without error       00%     27667         -
#10  Selective offline   Completed without error       00%     27652         -
#11  Selective offline   Completed without error       00%     27634         -
#12  Selective offline   Completed without error       00%     27616         -
#13  Selective offline   Completed without error       00%     27599         -
#14  Selective offline   Completed without error       00%     27583         -
#15  Selective offline   Completed without error       00%     27566         -
#16  Selective offline   Completed without error       00%     27549         -
#17  Selective offline   Completed without error       00%     27534         -
#18  Selective offline   Completed without error       00%     27521         -
#19  Selective offline   Completed without error       00%     27503         -
#20  Selective offline   Completed without error       00%     27488         -
#21  Selective offline   Completed without error       00%     27471         -

SMART Selective self-test log data structure revision number 1
 SPAN     MIN_LBA     MAX_LBA  CURRENT_TEST_STATUS
    1  1465135938  1627928819  Not_testing
    2           0           0  Not_testing
    3           0           0  Not_testing
    4           0           0  Not_testing
    5           0           0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by Blix775 on 2016-10-13
I used this on: [COLOR=#000000]sudo smartctl -a /dev/yourdisk

I'll run the long one and post it when it's done. [/COLOR]

---

### Post by frostschutz on 2016-10-13
You might need to scroll back up or make your terminal larger or redirect to a file using > output.txt or | wgetpaste or | pastebinit.

---

