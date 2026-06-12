---
title: "Western Digital HDD getting ata3.0 errors"
date: 2014-02-24
forum: Hardware
---

### Post by mitsai on 2014-02-24
Hello guys!

I'm having a problem here. I have a WD 500GB HDD (SATA3) and is causing me some problems.
I was happy to switch finally to ubuntu and get away from windows, but some unexpected thing happend.
I did : tail -f /var/log/syslog to see the errors about my HDD low performance and  I found  this:

```
Feb 23 19:41:19 ubuntu kernel: [  594.521895] ata3.01: configured for UDMA/33
Feb 23 19:41:19 ubuntu kernel: [  594.521920] ata3: EH complete
Feb 23 19:41:19 ubuntu kernel: [  594.734472] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Feb 23 19:41:19 ubuntu kernel: [  594.734542] ata3.00: failed command: WRITE MULTIPLE EXT
Feb 23 19:41:19 ubuntu kernel: [  594.734591] ata3.00: cmd 39/00:00:10:74:06/00:02:1d:00:00/e0 tag 0 pio 262144 out
Feb 23 19:41:19 ubuntu kernel: [  594.734591]          res 51/84:31:10:74:06/84:00:1d:00:00/e0 Emask 0x10 (ATA bus error)
Feb 23 19:41:19 ubuntu kernel: [  594.734709] ata3.00: status: { DRDY ERR }
Feb 23 19:41:19 ubuntu kernel: [  594.734742] ata3.00: error: { ICRC ABRT }
Feb 23 19:41:19 ubuntu kernel: [  594.734797] ata3: soft resetting link
Feb 23 19:41:19 ubuntu kernel: [  594.913122] ata3.00: configured for PIO0
Feb 23 19:41:19 ubuntu kernel: [  594.929287] ata3.01: configured for UDMA/33
Feb 23 19:41:19 ubuntu kernel: [  594.929313] ata3: EH complete
Feb 23 19:41:34 ubuntu kernel: [  609.262781] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Feb 23 19:41:34 ubuntu kernel: [  609.262845] ata3.00: failed command: WRITE MULTIPLE EXT
Feb 23 19:41:34 ubuntu kernel: [  609.262895] ata3.00: cmd 39/00:00:18:86:07/00:02:1d:00:00/e0 tag 0 pio 262144 out
Feb 23 19:41:34 ubuntu kernel: [  609.262895]          res 51/84:d1:18:86:07/84:00:1d:00:00/e0 Emask 0x10 (ATA bus error)
Feb 23 19:41:34 ubuntu kernel: [  609.263012] ata3.00: status: { DRDY ERR }
Feb 23 19:41:34 ubuntu kernel: [  609.263045] ata3.00: error: { ICRC ABRT }
Feb 23 19:41:34 ubuntu kernel: [  609.263101] ata3: soft resetting link
Feb 23 19:41:34 ubuntu kernel: [  609.442769] ata3.00: configured for PIO0
Feb 23 19:41:34 ubuntu kernel: [  609.458887] ata3.01: configured for UDMA/33
Feb 23 19:41:34 ubuntu kernel: [  609.458905] ata3: EH complete
Feb 23 19:41:37 ubuntu kernel: [  613.107724] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Feb 23 19:41:37 ubuntu kernel: [  613.107788] ata3.00: failed command: WRITE MULTIPLE EXT
Feb 23 19:41:37 ubuntu kernel: [  613.107840] ata3.00: cmd 39/00:00:18:ca:07/00:02:1d:00:00/e0 tag 0 pio 262144 out
Feb 23 19:41:37 ubuntu kernel: [  613.107840]          res 51/84:31:18:ca:07/84:00:1d:00:00/e0 Emask 0x10 (ATA bus error)
Feb 23 19:41:37 ubuntu kernel: [  613.107881] ata3.00: status: { DRDY ERR }
Feb 23 19:41:37 ubuntu kernel: [  613.107893] ata3.00: error: { ICRC ABRT }
Feb 23 19:41:37 ubuntu kernel: [  613.107920] ata3: soft resetting link
Feb 23 19:41:38 ubuntu kernel: [  613.284862] ata3.00: configured for PIO0
Feb 23 19:41:38 ubuntu kernel: [  613.301174] ata3.01: configured for UDMA/33
Feb 23 19:41:38 ubuntu kernel: [  613.301194] ata3: EH complete
Feb 23 19:41:41 ubuntu kernel: [  616.542554] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Feb 23 19:41:41 ubuntu kernel: [  616.542617] ata3.00: failed command: WRITE MULTIPLE EXT
Feb 23 19:41:41 ubuntu kernel: [  616.542667] ata3.00: cmd 39/00:e8:18:06:08/00:01:1d:00:00/e0 tag 0 pio 249856 out
Feb 23 19:41:41 ubuntu kernel: [  616.542667]          res 51/84:49:18:06:08/84:00:1d:00:00/e0 Emask 0x10 (ATA bus error)
Feb 23 19:41:41 ubuntu kernel: [  616.542783] ata3.00: status: { DRDY ERR }
Feb 23 19:41:41 ubuntu kernel: [  616.542816] ata3.00: error: { ICRC ABRT }
Feb 23 19:41:41 ubuntu kernel: [  616.542872] ata3: soft resetting link
Feb 23 19:41:41 ubuntu kernel: [  616.719702] ata3.00: configured for PIO0
Feb 23 19:41:41 ubuntu kernel: [  616.735810] ata3.01: configured for UDMA/33
Feb 23 19:41:41 ubuntu kernel: [  616.735835] ata3: EH complete


```
I already changed sata cables, sata ports, well almost everything.
The HDD has warranty so I needed to check the disk with windows. So I did.
What happened? It runs like a charm...
I really don't understand where is the problem.

I'm using (was) ubuntu 13.04, and this is my specs(what is needed):
Motherboard: Asus M5A97 r2.0 LE [https://www.asus.com/Motherboards/M5A97_LE_R20/](https://www.asus.com/Motherboards/M5A97_LE_R20/)
WD 500 GB HDD: [http://www.wdc.com/global/products/specs/?driveID=896&language=1](http://www.wdc.com/global/products/specs/?driveID=896&language=1)

I hope someone say something :(

PS: I also tested with Linux mint 16 and still the same.

---

### Post by Yellow Pasque on 2014-02-24
> configured for UDMA/33
That's not good. Perhaps the driver for the SB950's SATA controller is not negotiating correctly? If there is an option in your BIOS to force SATA 3Gbps (aka SATA II) mode, try that. If not, try to jumper the drive to force SATA 3Gbps: [http://wdc.custhelp.com/app/answers/detail/a_id/981/p/227,295/session/L3RpbWUvMTM5MzI3NDE3NC9zaWQvOGVFZ0tMTmw%3D#satadesktopjump](http://wdc.custhelp.com/app/answers/detail/a_id/981/p/227,295/session/L3RpbWUvMTM5MzI3NDE3NC9zaWQvOGVFZ0tMTmw%3D#satadesktopjump)

---

### Post by tgalati4 on 2014-02-24
Or perhaps the drive is failing.  What is the SMART status of the drive?

Open a terminal:

```
sudo smartctl -a /dev/sda
```

---

### Post by mitsai on 2014-02-25
I am now testing the HDD with the jump set to put HDD on 3Gbps mode. And I didnt see any errors yet. But the speed is always 35 to 40MB/s stable. (Obvious)

```
mint ~ # smartctl -a /dev/sdc
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-12-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD5000AAKX-00ERMA0
Serial Number:    WD-WCC2ESA77839
LU WWN Device Id: 5 0014ee 25e9e8c20
Firmware Version: 15.01H15
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Feb 25 20:04:50 2014 UTC
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
data collection:         ( 8460) seconds.
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
recommended polling time:      (  86) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   145   139   021    Pre-fail  Always       -       3725
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       360
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       596
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       142
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       32
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       327
194 Temperature_Celsius     0x0022   122   104   000    Old_age   Always       -       21
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   198   000    Old_age   Always       -       53772
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       590         -
# 2  Extended offline    Interrupted (host reset)      90%       586         -

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

After this, Im going to test again without the jumper and see if this line: "SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)" changes or not.
Im thinking about buying a PCI-E SATA controller. anyone have one chipset that does not cause any problems?

Thanks ! :D
mitsai

---

### Post by Yellow Pasque on 2014-02-25
> **mitsai said:**
> I am now testing the HDD with the jump set to put HDD on 3Gbps mode. And I didnt see any errors yet. But the speed is always 35 to 40MB/s stable. (Obvious)

Are you saying that SATA 3Gbps is slowing down the drive or that you're expecting faster transfer rates? It's not so obvious to me...

---

### Post by mitsai on 2014-02-25
Well, I think it is right. If with 6gbps on windows I got 100MB/s and  starts to slowing down and stable on 70, so on 3Gbps mode, 40MB/s It is  fine I guess.

without the jumper (6Gbps mode and this took like 5 minutes....):

```
mint ~ # smartctl -a /dev/sdc
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-12-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD5000AAKX-00ERMA0
Serial Number:    WD-WCC2ESA77839
LU WWN Device Id: 5 0014ee 25e9e8c20
Firmware Version: 15.01H15
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Tue Feb 25 20:23:22 2014 UTC
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
data collection:         ( 8460) seconds.
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
recommended polling time:      (  86) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   145   139   021    Pre-fail  Always       -       3725
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       361
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       597
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       143
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       327
194 Temperature_Celsius     0x0022   121   104   000    Old_age   Always       -       22
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   198   000    Old_age   Always       -       54024
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       590         -
# 2  Extended offline    Interrupted (host reset)      90%       586         -

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

### Post by tgalati4 on 2014-02-25
This line is troubling:

UDMA_CRC_Error_Count    0x0032   200   198   000    Old_age   Always       -      ** 54024**  And this number is increasing!

Something is wrong.  Perhaps it is the controller hardware on the drive.  WD Caviar Blues are generally fast (between 70 to 100 MB/sec as you have seen).  It could also be a conflict or problem on your motherboard SATA bus.  Perhaps you have too many drives plugged in.  Do some research on your motherboard.  Some chipsets only support 2 IDE and 4 SATA or 6 SATA.  And some won't give you full bandwidth in IDE mode or when fully populated.  If you have a lot of drives, remove them and retest.

Perhaps your power supply is sagging.  Try unplugging a few things to reduce the power load and see if that improves the throughput.

---

### Post by mitsai on 2014-02-25
I tested that tgalati4.
And it seems to have less errors, better speed, but soon or later it completly "crash" and the flood of ata errors begin.
Anyway, I have 4 SATA devices: 2x SSD (raid0 for the OS), 1x Sata3 HDD (WD), 1x Sata 2 HDD(Seagate).
I switched the SATA power cables and I noticed what I said the first lines of this reply. but this does not make any sense since with windows operating system I don't have this issues...

I just installed the edubuntu desktop and I'm enjoying this. I really don't "feel" the loss of speed, but when I need to make the backup of the disk to a secure device, it will be a nightmare. :p

So, the new chipset sata controller could be the solution.

---

