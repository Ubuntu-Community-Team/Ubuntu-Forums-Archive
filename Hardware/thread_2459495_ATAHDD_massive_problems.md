---
title: "ATA/HDD massive problems"
date: 2021-03-19
forum: Hardware
---

### Post by diridibindy on 2021-03-19
**[SIZE=4]journalctl -p err reports this[/SIZE]**
```

ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
ata6.00: irq_stat 0x00000040, connection status changed
ata6: SError: { PHYRdyChg CommWake DevExch }
ata6.00: failed command: READ DMA EXT
ata6.00: cmd 25/00:00:68:48:46/00:02:01:00:00/e0 tag 6 dma 262144 in
              res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
ata6.00: status: { DRDY }
blk_update_request: I/O error, dev sda, sector 21383272 op 0x0:(READ) flags 0x80700 phys_seg 19 prio class 0

```

This is a general idea of errors that I'm getting (and have been getting for more than a year now).

These are threads about my issues with the HDD

[https://www.reddit.com/r/linuxquestions/comments/hjc9ph/some_kind_of_atahdd_problem_unrelated_to_sata/](https://www.reddit.com/r/linuxquestions/comments/hjc9ph/some_kind_of_atahdd_problem_unrelated_to_sata/)
and
[https://ubuntuforums.org/showthread.php?t=2449285](https://ubuntuforums.org/showthread.php?t=2449285)

Nothing recommended in those threads helped, those recommendations being:

[LIST]
[*]Disabling NCQ (Didn't change anything regarding the errors) 
[*]Changing the SATA cable (Went through 3 different cables) 
[*]Checked the drive for faulty blocks (Nothing was found and the drive is in a good condition) 
[/LIST]

Myself I did the following things to try to fix the issue:
[LIST]
[*]Changed the motherboard (Once again, no changes to the drive crapping itself) 
[/LIST]

**[SIZE=3] Here is my smartctl -a output [/SIZE]**
```

smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-7642-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Blue
Device Model:     WDC WD10EZEX-08WN4A0
Serial Number:    WD-WCC6Y2AZCXCF
LU WWN Device Id: 5 0014ee 210ccd3e0
Firmware Version: 02.01A02
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Mar 19 22:29:21 2021 +03
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
data collection:         (11400) seconds.
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
recommended polling time:      ( 118) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   181   170   021    Pre-fail  Always       -       1908
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1136
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2184
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1086
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       169
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       994
194 Temperature_Celsius     0x0022   116   103   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   001   000    Old_age   Always       -       72380
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1507         -
# 2  Short offline       Interrupted (host reset)      90%      1507         -
# 3  Short offline       Completed without error       00%       837         -
# 4  Short offline       Completed without error       00%       836         -

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

[I] **[SIZE=2] Some (possibly) related problems with my system:[/SIZE]**
[/I][B][SIZE=2]*My other RAM stick (I have 2) doesn't get detected in the system (It is detected in UEFI, but not in the OS) after changes in UEFI, be it changing the RAM speed, voltage, sometimes even after adding another drive it doesn't get detected.*
[/SIZE][/B]
I really want to know if this is fixable or at least a concrete answer on what the problem actually is.
Some people suggested it's the PSU, but I want a way to confirm that before doing anything drastic.

After having enough of the issue I disabled the 1TB HDD and went with a brand new m.2 NVME 256G SSD, which did fix the problem… of me not being able to use the system, but after trying to get the damned HDD working for the past year I am really at a loss.
With the new SSD there are no more problems, with HDD mounted the kernel spews errors once again.

My system is:
GPU: 1660 Ti
CPU: Ryzen 5 2600
RAM: 16G
SSD: ADATA SX8200PNP

If any other data is required I will gladly post it, but please consider going through the linked threads for additional info first.

---

### Post by Autodave on 2021-03-19
You evidently have a bad HD.  It could possibly be overheating or just plain failing.  It could be drawing just a little too much power and shutting down.  If you could check the voltages, that might give you a hint.

---

### Post by diridibindy on 2021-03-19
Alright, I suppose that may be the case, though all the possible HDD tests come back with a positive result (They say it is fine).

How should I handle it, assuming the drive is bad?

Also why would you rule out a bad PSU?

Sorry if these questions are too much.

---

### Post by TheFu on 2021-03-19
I have a Ryzen 2600. It was picky about RAM even after installing new BIOS every 6 months.  In the end, my 3200 Mhz RAM would only run stable at 2800Mhz.  I have an Asus B550 Motherboard.

I's run a smartctl long test, not just short tests on the drive. Give the tests a chance to see more problems.

The error is most commonly caused by a bad cable, cable interference (running power too close to data cables), bad SATA controller.  Perhaps the SATA controller has known issues with Linux?  I have a Marvell SATA controller that claims to support SATA-3, but only provides SATA-2 connectivity.  So, try different power inputs, different SATA ports, different cables and a different SATA controller. Besides that, there isn't much you can do besides run ZFS to ensure that data supposed to be on the disk actually gets there. ZFS is the only file system which validates data.

You can/should look up what this:
```
199 UDMA_CRC_Error_Count    0x0032   200   001   000    Old_age   Always       -       72380
```
means for the exact model of disk. [https://kb.acronis.com/content/9135](https://kb.acronis.com/content/9135) says to watch other parameters and to have backups.  That's always good advice for any storage used.

---

### Post by diridibindy on 2021-03-20
The thing is I tried 3 different SATA cables, 6 sata ports on one motherboard and 6 on the other, I even tried running the drive on Windows, it didn't  tell me much, just BSODd.

I'll try to search for CRC errors and if nothing is found will try using ZFS, I assume these issues won't  do anything to a ZFS filesystem?

Nothing was found, apparently WD is very bad at documentation, they couldn't even find what S.M.A.R.T means on their disks in their own internal documentation. Guess I'm left with ZFS/replacing the disk?/buying a PCIe SATA extension?

---

### Post by TheFu on 2021-03-20
ZFS will only tell you if the data that was supposed to be written was not. If you have ECC RAM, then perhaps it can try to rewrite the data and get the correct stuff onto the drive.  Without ECC, you get what you get, which is better than fire-and-forget-and-hope that other file systems use.

Sometimes we get *lemon* hardware. If we aren't quick and return it within 30 days (local rules apply), then we are stuck with it. If the issues come up later, there isn't much to be done except to have excellent backups.

---

### Post by diridibindy on 2021-03-20
I guess I can go and do something about it. I will probably call the company that sold it to me. I still have a 2 year warranty that expires on October 1, 2021. 

I hope they will replace it, or at least let me buy another one at a discount. Those damn 1TB drives went up 15$ here.
The customer rights policy is quite a good one in my country so I will see. 
The biggest thing I fear is that replacing the drive wont fix the issue.

---

### Post by rsteinmetz70112 on 2021-03-20
If you do replace the drive ant the problems persdis at least you'll know it not the drive. :cool:
In an earlier post you mentioned trying a different motherboard and having the same problems, was it the same model board? if so which model(s)
In an earlier post the Fu mentioned updating the Firmware on the motherboard have you checked that you have the latest firmware?
Next step wpuld be swaping out components I've found that PSUs are often at fault.

---

