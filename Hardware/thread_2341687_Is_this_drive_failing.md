---
title: "Is this drive failing?"
date: 2016-10-30
forum: Hardware
---

### Post by Harpz on 2016-10-30
One of my drives in my ubuntu server seems to be throwing alot of errors over the last few day when ever i try to write to it.

I've run smart tests short, long and conveyance and they all complete without error.
```

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     23918         -
# 2  Conveyance offline  Completed without error       00%     23912         -
# 3  Short offline       Completed without error       00%     23911         -
# 4  Short offline       Completed without error       00%     22561         -


```

Looking at the smart report for the drive the only thing i can see is that its getting a little old 

```

mike@Altair:~$ sudo smartctl -a /dev/sdj
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-45-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WMAZA8726413
LU WWN Device Id: 5 0014ee 159ffa550
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Sun Oct 30 19:26:24 2016 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(38580) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 372) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   171   021    Pre-fail  Always       -       1091
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5990
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   068   068   000    Old_age   Always       -       23922
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1152
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       155
193 Load_Cycle_Count        0x0032   175   175   000    Old_age   Always       -       75168
194 Temperature_Celsius     0x0022   120   108   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     23918         -
# 2  Conveyance offline  Completed without error       00%     23912         -
# 3  Short offline       Completed without error       00%     23911         -
# 4  Short offline       Completed without error       00%     22561         -
# 5  Extended offline    Completed without error       00%     22557         -
# 6  Short offline       Completed without error       00%     22529         -
# 7  Short offline       Completed without error       00%     22523         -
# 8  Short offline       Completed without error       00%     22495         -
# 9  Short offline       Completed without error       00%     22489         -
#10  Short offline       Completed without error       00%     22468         -
#11  Extended offline    Completed without error       00%     22450         -
#12  Short offline       Completed without error       00%     22416         -
#13  Short offline       Completed without error       00%     22404         -
#14  Extended offline    Completed without error       00%     22381         -
#15  Short offline       Completed without error       00%     22365         -
#16  Short offline       Completed without error       00%     22359         -
#17  Short offline       Completed without error       00%     22355         -
#18  Short offline       Completed without error       00%     22339         -
#19  Extended offline    Completed without error       00%     22315         -
#20  Short offline       Completed without error       00%     22262         -
#21  Short offline       Completed without error       00%     22237         -

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

smartd emailed me the following:
```

The following warning/error was logged by the smartd daemon:

Device: /dev/sdj [SAT], not capable of SMART self-check

Device info:
WDC WD20EARX-00PASB0, S/N:WD-WMAZA8726413, WWN:5-0014ee-159ffa550, FW:51.0AB51, 2.00 TB

```

Errors I'm getting:
```

Oct 30 19:18:22 Altair kernel: [ 3535.767498] ata5: hard resetting link
Oct 30 19:18:30 Altair kernel: [ 3543.772019] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:18:30 Altair kernel: [ 3543.810903] ata5.00: configured for UDMA/33
Oct 30 19:18:30 Altair kernel: [ 3543.810924] ata5: EH complete
Oct 30 19:18:31 Altair kernel: [ 3545.583835] ata5.00: exception Emask 0x50 SAct 0x18000000 SErr 0x90a00 action 0xe frozen
Oct 30 19:18:31 Altair kernel: [ 3545.587069] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:18:31 Altair kernel: [ 3545.590336] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:18:31 Altair kernel: [ 3545.593565] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:31 Altair kernel: [ 3545.596785] ata5.00: cmd 60/00:d8:00:84:7d/02:00:5c:00:00/40 tag 27 ncq 262144 in
Oct 30 19:18:31 Altair kernel: [ 3545.596785]          res 40/00:dc:00:84:7d/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:31 Altair kernel: [ 3545.603238] ata5.00: status: { DRDY }
Oct 30 19:18:31 Altair kernel: [ 3545.606446] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:31 Altair kernel: [ 3545.609640] ata5.00: cmd 60/00:e0:00:86:7d/02:00:5c:00:00/40 tag 28 ncq 262144 in
Oct 30 19:18:31 Altair kernel: [ 3545.609640]          res 40/00:dc:00:84:7d/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:31 Altair kernel: [ 3545.615987] ata5.00: status: { DRDY }
Oct 30 19:18:31 Altair kernel: [ 3545.619139] ata5: hard resetting link
Oct 30 19:18:39 Altair kernel: [ 3553.175764] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:18:39 Altair kernel: [ 3553.211911] ata5.00: configured for UDMA/33
Oct 30 19:18:39 Altair kernel: [ 3553.211929] ata5: EH complete
Oct 30 19:18:40 Altair kernel: [ 3554.455630] ata5.00: exception Emask 0x50 SAct 0x18000000 SErr 0x90a00 action 0xe frozen
Oct 30 19:18:40 Altair kernel: [ 3554.459163] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:18:40 Altair kernel: [ 3554.462938] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:18:40 Altair kernel: [ 3554.466645] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:40 Altair kernel: [ 3554.469858] ata5.00: cmd 60/00:d8:00:72:84/02:00:5c:00:00/40 tag 27 ncq 262144 in
Oct 30 19:18:40 Altair kernel: [ 3554.469858]          res 40/00:dc:00:72:84/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:40 Altair kernel: [ 3554.476839] ata5.00: status: { DRDY }
Oct 30 19:18:40 Altair kernel: [ 3554.480042] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:40 Altair kernel: [ 3554.483606] ata5.00: cmd 60/00:e0:00:74:84/02:00:5c:00:00/40 tag 28 ncq 262144 in
Oct 30 19:18:40 Altair kernel: [ 3554.483606]          res 40/00:dc:00:72:84/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:40 Altair kernel: [ 3554.490412] ata5.00: status: { DRDY }
Oct 30 19:18:40 Altair kernel: [ 3554.493617] ata5: hard resetting link
Oct 30 19:18:48 Altair kernel: [ 3562.107521] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:18:48 Altair kernel: [ 3562.143956] ata5.00: configured for UDMA/33
Oct 30 19:18:48 Altair kernel: [ 3562.143977] ata5: EH complete
Oct 30 19:18:49 Altair kernel: [ 3563.407382] ata5.00: exception Emask 0x50 SAct 0x600 SErr 0x90a00 action 0xe frozen
Oct 30 19:18:49 Altair kernel: [ 3563.410623] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:18:49 Altair kernel: [ 3563.413891] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:18:49 Altair kernel: [ 3563.417109] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:49 Altair kernel: [ 3563.420279] ata5.00: cmd 60/00:48:f0:6c:88/02:00:5c:00:00/40 tag 9 ncq 262144 in
Oct 30 19:18:49 Altair kernel: [ 3563.420279]          res 40/00:54:f0:6e:88/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:49 Altair kernel: [ 3563.426593] ata5.00: status: { DRDY }
Oct 30 19:18:49 Altair kernel: [ 3563.429754] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:49 Altair kernel: [ 3563.432905] ata5.00: cmd 60/00:50:f0:6e:88/02:00:5c:00:00/40 tag 10 ncq 262144 in
Oct 30 19:18:49 Altair kernel: [ 3563.432905]          res 40/00:54:f0:6e:88/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:49 Altair kernel: [ 3563.439210] ata5.00: status: { DRDY }
Oct 30 19:18:49 Altair kernel: [ 3563.442376] ata5: hard resetting link
Oct 30 19:18:57 Altair kernel: [ 3571.111276] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:18:57 Altair kernel: [ 3571.149104] ata5.00: configured for UDMA/33
Oct 30 19:18:57 Altair kernel: [ 3571.149124] ata5: EH complete
Oct 30 19:18:58 Altair kernel: [ 3572.447127] ata5.00: exception Emask 0x50 SAct 0x30 SErr 0x90a00 action 0xe frozen
Oct 30 19:18:58 Altair kernel: [ 3572.450506] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:18:58 Altair kernel: [ 3572.453877] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:18:58 Altair kernel: [ 3572.457183] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:58 Altair kernel: [ 3572.460347] ata5.00: cmd 60/00:20:00:b8:8b/02:00:5c:00:00/40 tag 4 ncq 262144 in
Oct 30 19:18:58 Altair kernel: [ 3572.460347]          res 40/00:24:00:b8:8b/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:58 Altair kernel: [ 3572.466711] ata5.00: status: { DRDY }
Oct 30 19:18:58 Altair kernel: [ 3572.469882] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:18:58 Altair kernel: [ 3572.473041] ata5.00: cmd 60/00:28:00:ba:8b/02:00:5c:00:00/40 tag 5 ncq 262144 in
Oct 30 19:18:58 Altair kernel: [ 3572.473041]          res 40/00:24:00:b8:8b/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:18:58 Altair kernel: [ 3572.479394] ata5.00: status: { DRDY }
Oct 30 19:18:58 Altair kernel: [ 3572.482531] ata5: hard resetting link
Oct 30 19:19:06 Altair kernel: [ 3580.207029] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:19:06 Altair kernel: [ 3580.249844] ata5.00: configured for UDMA/33
Oct 30 19:19:06 Altair kernel: [ 3580.249864] ata5: EH complete
Oct 30 19:19:07 Altair kernel: [ 3581.394900] ata5.00: exception Emask 0x50 SAct 0xc0 SErr 0x90a00 action 0xe frozen
Oct 30 19:19:07 Altair kernel: [ 3581.398121] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:19:07 Altair kernel: [ 3581.401355] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:19:07 Altair kernel: [ 3581.404553] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:19:07 Altair kernel: [ 3581.407724] ata5.00: cmd 60/00:30:00:2a:90/02:00:5c:00:00/40 tag 6 ncq 262144 in
Oct 30 19:19:07 Altair kernel: [ 3581.407724]          res 40/00:34:00:2a:90/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:19:07 Altair kernel: [ 3581.414056] ata5.00: status: { DRDY }
Oct 30 19:19:07 Altair kernel: [ 3581.417204] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:19:07 Altair kernel: [ 3581.420340] ata5.00: cmd 60/00:38:00:2c:90/02:00:5c:00:00/40 tag 7 ncq 262144 in
Oct 30 19:19:07 Altair kernel: [ 3581.420340]          res 40/00:34:00:2a:90/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:19:07 Altair kernel: [ 3581.426651] ata5.00: status: { DRDY }
Oct 30 19:19:07 Altair kernel: [ 3581.429809] ata5: hard resetting link
Oct 30 19:19:15 Altair kernel: [ 3589.154786] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:19:15 Altair kernel: [ 3589.194334] ata5.00: configured for UDMA/33
Oct 30 19:19:15 Altair kernel: [ 3589.194354] ata5: EH complete
Oct 30 19:19:16 Altair kernel: [ 3590.382634] ata5.00: exception Emask 0x50 SAct 0x18000 SErr 0x90a00 action 0xe frozen
Oct 30 19:19:16 Altair kernel: [ 3590.386338] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:19:16 Altair kernel: [ 3590.389698] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:19:16 Altair kernel: [ 3590.393219] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:19:16 Altair kernel: [ 3590.396443] ata5.00: cmd 60/00:78:00:78:93/02:00:5c:00:00/40 tag 15 ncq 262144 in
Oct 30 19:19:16 Altair kernel: [ 3590.396443]          res 40/00:7c:00:78:93/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:19:16 Altair kernel: [ 3590.403447] ata5.00: status: { DRDY }
Oct 30 19:19:16 Altair kernel: [ 3590.406650] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:19:16 Altair kernel: [ 3590.410128] ata5.00: cmd 60/00:80:00:7a:93/02:00:5c:00:00/40 tag 16 ncq 262144 in
Oct 30 19:19:16 Altair kernel: [ 3590.410128]          res 40/00:7c:00:78:93/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:19:16 Altair kernel: [ 3590.416583] ata5.00: status: { DRDY }
Oct 30 19:19:16 Altair kernel: [ 3590.420010] ata5: hard resetting link
Oct 30 19:19:24 Altair kernel: [ 3598.206542] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 30 19:19:24 Altair kernel: [ 3598.247156] ata5.00: configured for UDMA/33
Oct 30 19:19:24 Altair kernel: [ 3598.247177] ata5: EH complete
Oct 30 19:19:25 Altair kernel: [ 3599.506449] ata5.00: exception Emask 0x50 SAct 0xc0000 SErr 0x90a00 action 0xe frozen
Oct 30 19:19:25 Altair kernel: [ 3599.509879] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 30 19:19:25 Altair kernel: [ 3599.513354] ata5: SError: { Persist HostInt PHYRdyChg 10B8B }
Oct 30 19:19:25 Altair kernel: [ 3599.516539] ata5.00: failed command: READ FPDMA QUEUED
Oct 30 19:19:25 Altair kernel: [ 3599.519953] ata5.00: cmd 60/00:90:00:32:97/02:00:5c:00:00/40 tag 18 ncq 262144 in
Oct 30 19:19:25 Altair kernel: [ 3599.519953]          res 40/00:94:00:32:97/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 30 19:19:25 Altair kernel: [ 3599.526267] ata5.00: status: { DRDY }

```

I've tried moving the drive along in the caddie to another slot so its on a different cable but this has thew same result, I've also changed the cables from that caddie to the motherboard as well, this has same result.

I haven't tried moving the drive to a spare slot on my m1015 yet that will be next.

Could this be a drive issue or a m/b issue as i read that it could be a sign the m/b controllers are failing somewhere?

---

### Post by kpatz on 2016-10-30
How many drives are connected to the motherboard?  Is that the only drive throwing the errors?  If you swap the SATA ports on 2 drives, do the errors follow the drive?

The SMART stats on the drive look ok other than a really high LOAD_CYCLE_COUNT.  The drive's been running for 2.7 years straight, that's not unheard of (I had 4 WD Greens running in a server 24/7 for 7 years, I only just recently upgraded that server and the drives still work flawlessly).

Maybe the controller board on the drive is starting to go.

---

### Post by Harpz on 2016-10-31
Currently there are 4 drive on the m/b controller and that's the only one throwing errors at the moment.

In the past its happened to a few of them on the m/b controller but then it stopped so i thought nothing of it. 

I moved the drive again to an empty slot in my rack, one that was still connected to the m/b controller and copied some files to the drive, around 10Gb in total this time and it only threw a few errors.

```

Oct 31 06:44:06 Altair kernel: [  188.912849] ata5.00: exception Emask 0x50 SAct 0xc0000 SErr 0x90a02 action 0xe frozen
Oct 31 06:44:06 Altair kernel: [  188.912963] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 31 06:44:06 Altair kernel: [  188.913038] ata5: SError: { RecovComm Persist HostInt PHYRdyChg 10B8B }
Oct 31 06:44:06 Altair kernel: [  188.913156] ata5.00: failed command: READ FPDMA QUEUED
Oct 31 06:44:06 Altair kernel: [  188.913232] ata5.00: cmd 60/00:90:00:f4:2e/02:00:5c:00:00/40 tag 18 ncq 262144 in
Oct 31 06:44:06 Altair kernel: [  188.913232]          res 40/00:94:00:f4:2e/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 31 06:44:06 Altair kernel: [  188.913432] ata5.00: status: { DRDY }
Oct 31 06:44:06 Altair kernel: [  188.913484] ata5.00: failed command: READ FPDMA QUEUED
Oct 31 06:44:06 Altair kernel: [  188.913559] ata5.00: cmd 60/00:98:00:f6:2e/02:00:5c:00:00/40 tag 19 ncq 262144 in
Oct 31 06:44:06 Altair kernel: [  188.913559]          res 40/00:94:00:f4:2e/00:00:5c:00:00/40 Emask 0x50 (ATA bus error)
Oct 31 06:44:06 Altair kernel: [  188.913755] ata5.00: status: { DRDY }
Oct 31 06:44:06 Altair kernel: [  188.913808] ata5: hard resetting link
Oct 31 06:44:14 Altair kernel: [  196.752083] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 31 06:44:14 Altair kernel: [  196.795115] ata5.00: configured for UDMA/133
Oct 31 06:44:14 Altair kernel: [  196.795133] ata5: EH complete
Oct 31 06:45:47 Altair kernel: [  289.439245] ata5.00: exception Emask 0x50 SAct 0x6000000 SErr 0x90b02 action 0xe frozen
Oct 31 06:45:47 Altair kernel: [  289.439415] ata5.00: irq_stat 0x01400000, PHY RDY changed
Oct 31 06:45:47 Altair kernel: [  289.439489] ata5: SError: { RecovComm UnrecovData Persist HostInt PHYRdyChg 10B8B }
Oct 31 06:45:47 Altair kernel: [  289.439589] ata5.00: failed command: READ FPDMA QUEUED
Oct 31 06:45:47 Altair kernel: [  289.439665] ata5.00: cmd 60/00:c8:00:9c:96/02:00:ba:00:00/40 tag 25 ncq 262144 in
Oct 31 06:45:47 Altair kernel: [  289.439665]          res 40/00:cc:00:9c:96/00:00:ba:00:00/40 Emask 0x50 (ATA bus error)
Oct 31 06:45:47 Altair kernel: [  289.439886] ata5.00: status: { DRDY }
Oct 31 06:45:47 Altair kernel: [  289.439944] ata5.00: failed command: READ FPDMA QUEUED
Oct 31 06:45:47 Altair kernel: [  289.440046] ata5.00: cmd 60/00:d0:00:9e:96/02:00:ba:00:00/40 tag 26 ncq 262144 in
Oct 31 06:45:47 Altair kernel: [  289.440046]          res 40/00:cc:00:9c:96/00:00:ba:00:00/40 Emask 0x50 (ATA bus error)
Oct 31 06:45:47 Altair kernel: [  289.440245] ata5.00: status: { DRDY }
Oct 31 06:45:47 Altair kernel: [  289.440298] ata5: hard resetting link
Oct 31 06:45:55 Altair kernel: [  297.390596] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 31 06:45:55 Altair kernel: [  297.428418] ata5.00: configured for UDMA/133
Oct 31 06:45:55 Altair kernel: [  297.428437] ata5: EH complete

```

Are theses type of errors usually drive controller related or m/b controller related?
 
Would moving the drive off the m/b controller and to my M1015 to see if i still get any errors be worth doing?

---

### Post by mastablasta on 2016-10-31
green are meant to record and then power down /go into staby. red are nearly always on. purple are for recording data non-stop e.g. video. blue for os, black high performance. so dependign on their use, the green can actually last long.

back to your issue, doesn't look like the drive. as kpatz suggested you need to figure out if the rrors "follow" the drive. you could plug it into anything else actually with a live OS booted to do soem testing on the drive. if erorrs persist then SMART is wrong and drive is dying.

i had a black one fail on me. looks like something was wrogn with the disk contorllers, could spin it up well when power was added. anyway smart showed good disk state. that's because it was checkign the disk not device it seems. device was dying after 11 years, but data on it was good. i cloned the data using clonezilla on a new biger drive as soon as i could mount it.

---

### Post by Harpz on 2016-11-01
I've tried the drive in a few different m/b sata ports now and they all seem to yield the same results, i get the same error relating to disk 5.

I have 3 other disks attached to the m/b controller and they seem fine at this time.

```

Nov  1 18:06:52 Altair kernel: [  126.437110] ata3.00: exception Emask 0x50 SAct 0x800 SErr 0x90a02 action 0xe frozen
Nov  1 18:06:52 Altair kernel: [  126.437229] ata3.00: irq_stat 0x00400000, PHY RDY changed
Nov  1 18:06:52 Altair kernel: [  126.437308] ata3: SError: { RecovComm Persist HostInt PHYRdyChg 10B8B }
Nov  1 18:06:52 Altair kernel: [  126.437402] ata3.00: failed command: READ FPDMA QUEUED
Nov  1 18:06:52 Altair kernel: [  126.437481] ata3.00: cmd 60/00:58:00:5c:04/02:00:00:00:00/40 tag 11 ncq 262144 in
Nov  1 18:06:52 Altair kernel: [  126.437481]          res 40/00:5c:00:5c:04/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Nov  1 18:06:52 Altair kernel: [  126.437687] ata3.00: status: { DRDY }
Nov  1 18:06:52 Altair kernel: [  126.437744] ata3: hard resetting link
Nov  1 18:07:00 Altair kernel: [  134.449030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  1 18:07:00 Altair kernel: [  134.482931] ata3.00: configured for UDMA/133
Nov  1 18:07:00 Altair kernel: [  134.482947] ata3: EH complete
Nov  1 18:07:01 Altair kernel: [  134.705045] ata3.00: exception Emask 0x50 SAct 0x600000 SErr 0x90a02 action 0xe frozen
Nov  1 18:07:01 Altair kernel: [  134.705155] ata3.00: irq_stat 0x01400000, PHY RDY changed
Nov  1 18:07:01 Altair kernel: [  134.705225] ata3: SError: { RecovComm Persist HostInt PHYRdyChg 10B8B }
Nov  1 18:07:01 Altair kernel: [  134.705311] ata3.00: failed command: READ FPDMA QUEUED
Nov  1 18:07:01 Altair kernel: [  134.705381] ata3.00: cmd 60/00:a8:00:88:04/02:00:00:00:00/40 tag 21 ncq 262144 in
Nov  1 18:07:01 Altair kernel: [  134.705381]          res 40/00:ac:00:88:04/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Nov  1 18:07:01 Altair kernel: [  134.705571] ata3.00: status: { DRDY }
Nov  1 18:07:01 Altair kernel: [  134.705619] ata3.00: failed command: READ FPDMA QUEUED
Nov  1 18:07:01 Altair kernel: [  134.705689] ata3.00: cmd 60/00:b0:00:8a:04/02:00:00:00:00/40 tag 22 ncq 262144 in
Nov  1 18:07:01 Altair kernel: [  134.705689]          res 40/00:ac:00:88:04/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Nov  1 18:07:01 Altair kernel: [  134.705878] ata3.00: status: { DRDY }
Nov  1 18:07:01 Altair kernel: [  134.705928] ata3: hard resetting link
Nov  1 18:07:09 Altair kernel: [  142.992971] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  1 18:07:09 Altair kernel: [  143.029487] ata3.00: configured for UDMA/133
Nov  1 18:07:09 Altair kernel: [  143.029504] ata3: EH complete
Nov  1 18:07:09 Altair kernel: [  143.193950] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Nov  1 18:07:09 Altair kernel: [  143.194051] ata3: irq_stat 0x00400000, PHY RDY changed
Nov  1 18:07:09 Altair kernel: [  143.194120] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
Nov  1 18:07:09 Altair kernel: [  143.194198] ata3: hard resetting link
Nov  1 18:07:17 Altair kernel: [  151.484811] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  1 18:07:17 Altair kernel: [  151.528315] ata3.00: configured for UDMA/133
Nov  1 18:07:17 Altair kernel: [  151.528325] ata3: EH complete
Nov  1 18:07:18 Altair kernel: [  152.128834] ata3: limiting SATA link speed to 1.5 Gbps
Nov  1 18:07:18 Altair kernel: [  152.128844] ata3.00: exception Emask 0x50 SAct 0x8 SErr 0x90a02 action 0xe frozen
Nov  1 18:07:18 Altair kernel: [  152.128958] ata3.00: irq_stat 0x01400000, PHY RDY changed
Nov  1 18:07:18 Altair kernel: [  152.129035] ata3: SError: { RecovComm Persist HostInt PHYRdyChg 10B8B }
Nov  1 18:07:18 Altair kernel: [  152.129128] ata3.00: failed command: READ FPDMA QUEUED
Nov  1 18:07:18 Altair kernel: [  152.129207] ata3.00: cmd 60/00:18:00:22:05/02:00:00:00:00/40 tag 3 ncq 262144 in

```

```

lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sda -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:0/end_device-0:0/target0:0:0/0:0:0:0/block/sda
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdb -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:1/end_device-0:1/target0:0:1/0:0:1:0/block/sdb
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdc -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:2/end_device-0:2/target0:0:2/0:0:2:0/block/sdc
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdd -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:3/end_device-0:3/target0:0:3/0:0:3:0/block/sdd
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sde -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:4/end_device-0:4/target0:0:4/0:0:4:0/block/sde
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdf -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host0/port-0:5/end_device-0:5/target0:0:5/0:0:5:0/block/sdf
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdg -> ../devices/pci0000:00/0000:00:11.0/ata1/host1/target1:0:0/1:0:0:0/block/sdg
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdh -> ../devices/pci0000:00/0000:00:11.0/ata2/host2/target2:0:0/2:0:0:0/block/sdh
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdi -> ../devices/pci0000:00/0000:00:11.0/ata3/host3/target3:0:0/3:0:0:0/block/sdi
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdj -> ../devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sdj
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdk -> ../devices/pci0000:00/0000:00:09.0/0000:04:00.0/ata9/host7/target7:0:0/7:0:0:0/block/sdk
lrwxrwxrwx 1 root root 0 Nov  1 18:05 /sys/block/sdl -> ../devices/pci0000:00/0000:00:09.0/0000:04:00.0/ata10/host8/target8:0:0/8:0:0:0/block/sdl

mike@Altair:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       459G  416G   38G  92% /mnt/D9_S0MUJ1GP711754
/dev/sda1       1.8T  1.6T  258G  86% /mnt/D6_MCE7215P09P7GW
/dev/sdh1       2.7T  2.6T  173G  94% /mnt/P2_Z3GGZ0PGS
/dev/sdj1       2.7T  2.6T  121G  96% /mnt/D2_Y47UL8DGS
/dev/sdg1       2.7T  2.6T  173G  94% /mnt/P1_43PPYJEYS
/dev/sdf1       917G  317G  591G  35% /mnt/D7_WD-WCAV5D092592
/dev/sdb1       2.7T  2.5T  233G  92% /mnt/D1_WD-WMC1T2102007
/dev/sde1       917G  585G  324G  65% /mnt/D8_S246J90Z914777
/dev/sdk1       1.8T  1.6T  203G  89% /mnt/D4_WD-WMAZA8726413
/dev/sdc1       1.8T  1.7T  168G  91% /mnt/D3_WD-WCAZA4585231
/dev/sdi1       1.8T  1.6T  229G  88% /mnt/D5_WD-WMAZA9227899
/dev/sdl5       415G   12G  382G   3% /home
mergerfsPool    9.0T  8.1T  749G  92% /mnt/TV_Shows

```

I then tried the disk in one of my M1015 ports to see if it would act the same, it didn't.
```

/dev/sdd1       1.8T  1.6T  229G  88% /mnt/D5_WD-WMAZA9227899

lrwxrwxrwx 1 root root 0 Nov  1 18:43 /sys/block/sdd -> ../devices/pci0000:00/0000:00:02.0/0000:02:00.0/host2/port-2:3/end_device-2:3/target2:0:3/2:0:3:0/block/sdd

```

Disk 5 has run fine on the m/b controller for years, any idea why it appears to no longer want to work as it should when attached to the m/b.

Decided to have a look through some of the older server logs and noticed the following a few times:
```

Oct 14 22:20:08 Altair kernel: [16306.086632] sd 10:0:3:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Oct 14 22:20:08 Altair kernel: [16306.086643] sd 10:0:3:0: [sdd] tag#0 CDB: Read(10) 28 00 02 40 09 08 00 00 08 00
Oct 14 22:20:08 Altair kernel: [16306.086648] blk_update_request: I/O error, dev sdd, sector 37751048
Oct 14 22:20:08 Altair kernel: [16306.086756] sd 10:0:3:0: [sdd] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:20:08 Altair kernel: [16306.086762] sd 10:0:3:0: [sdd] tag#1 Sense Key : Not Ready [current] 
Oct 14 22:20:08 Altair kernel: [16306.086767] sd 10:0:3:0: [sdd] tag#1 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:20:08 Altair kernel: [16306.086773] sd 10:0:3:0: [sdd] tag#1 CDB: Read(10) 28 00 02 40 09 10 00 00 08 00
Oct 14 22:20:08 Altair kernel: [16306.086776] blk_update_request: I/O error, dev sdd, sector 37751056
Oct 14 22:20:08 Altair kernel: [16306.086869] sd 10:0:3:0: [sdd] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:20:08 Altair kernel: [16306.086874] sd 10:0:3:0: [sdd] tag#2 Sense Key : Not Ready [current] 
Oct 14 22:20:08 Altair kernel: [16306.086879] sd 10:0:3:0: [sdd] tag#2 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:20:08 Altair kernel: [16306.086884] sd 10:0:3:0: [sdd] tag#2 CDB: Read(10) 28 00 02 40 09 18 00 00 08 00
Oct 14 22:20:08 Altair kernel: [16306.086887] blk_update_request: I/O error, dev sdd, sector 37751064
Oct 14 22:20:08 Altair kernel: [16306.086979] sd 10:0:3:0: [sdd] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:20:08 Altair kernel: [16306.086984] sd 10:0:3:0: [sdd] tag#3 Sense Key : Not Ready [current] 
Oct 14 22:20:08 Altair kernel: [16306.086989] sd 10:0:3:0: [sdd] tag#3 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:20:08 Altair kernel: [16306.086993] sd 10:0:3:0: [sdd] tag#3 CDB: Read(10) 28 00 02 40 09 20 00 00 08 00
Oct 14 22:20:08 Altair kernel: [16306.086997] blk_update_request: I/O error, dev sdd, sector 37751072
Oct 14 22:20:09 Altair sSMTP[3601]: Creating SSL connection to host
Oct 14 22:20:09 Altair sSMTP[3601]: SSL connection using RSA_AES_128_CBC_SHA1
Oct 14 22:20:12 Altair sSMTP[3601]: Sent mail for root@gmail.com (221 2.0.0 closing connection vx1sm529815wjc.3 - gsmtp) uid=0 username=root outbytes=1895
Oct 14 22:20:17 Altair sSMTP[3607]: Creating SSL connection to host
Oct 14 22:20:17 Altair sSMTP[3607]: SSL connection using RSA_AES_128_CBC_SHA1
Oct 14 22:20:19 Altair sSMTP[3607]: Sent mail for root@gmail.com (221 2.0.0 closing connection q63sm376832wma.2 - gsmtp) uid=0 username=root outbytes=953
Oct 14 22:40:01 Altair CRON[3614]: (root) CMD (/home/mike/scripts/snapraid_sync_new.sh)
Oct 14 22:41:33 Altair kernel: [17591.371088] sd 10:0:5:0: [sdf] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Oct 14 22:41:33 Altair kernel: [17591.371099] sd 10:0:5:0: [sdf] tag#0 CDB: Read(10) 28 00 17 80 09 08 00 00 08 00
Oct 14 22:41:33 Altair kernel: [17591.371104] blk_update_request: I/O error, dev sdf, sector 394266888
Oct 14 22:41:33 Altair kernel: [17591.371215] sd 10:0:5:0: [sdf] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:41:33 Altair kernel: [17591.371221] sd 10:0:5:0: [sdf] tag#1 Sense Key : Not Ready [current] 
Oct 14 22:41:33 Altair kernel: [17591.371226] sd 10:0:5:0: [sdf] tag#1 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:41:33 Altair kernel: [17591.371232] sd 10:0:5:0: [sdf] tag#1 CDB: Read(10) 28 00 17 80 09 10 00 00 08 00
Oct 14 22:41:33 Altair kernel: [17591.371235] blk_update_request: I/O error, dev sdf, sector 394266896
Oct 14 22:41:33 Altair kernel: [17591.371330] sd 10:0:5:0: [sdf] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:41:33 Altair kernel: [17591.371335] sd 10:0:5:0: [sdf] tag#2 Sense Key : Not Ready [current] 
Oct 14 22:41:33 Altair kernel: [17591.371340] sd 10:0:5:0: [sdf] tag#2 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:41:33 Altair kernel: [17591.371344] sd 10:0:5:0: [sdf] tag#2 CDB: Read(10) 28 00 17 80 09 18 00 00 08 00
Oct 14 22:41:33 Altair kernel: [17591.371348] blk_update_request: I/O error, dev sdf, sector 394266904
Oct 14 22:41:43 Altair kernel: [17601.348575] sd 10:0:4:0: [sde] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Oct 14 22:41:43 Altair kernel: [17601.348586] sd 10:0:4:0: [sde] tag#0 CDB: Read(10) 28 00 1e 80 09 08 00 00 08 00
Oct 14 22:41:43 Altair kernel: [17601.348591] blk_update_request: I/O error, dev sde, sector 511707400
Oct 14 22:41:43 Altair kernel: [17601.348697] sd 10:0:4:0: [sde] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:41:43 Altair kernel: [17601.348703] sd 10:0:4:0: [sde] tag#1 Sense Key : Not Ready [current] 
Oct 14 22:41:43 Altair kernel: [17601.348709] sd 10:0:4:0: [sde] tag#1 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:41:43 Altair kernel: [17601.348714] sd 10:0:4:0: [sde] tag#1 CDB: Read(10) 28 00 1e 80 09 10 00 00 08 00
Oct 14 22:41:43 Altair kernel: [17601.348717] blk_update_request: I/O error, dev sde, sector 511707408
Oct 14 22:41:43 Altair kernel: [17601.348812] sd 10:0:4:0: [sde] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 14 22:41:43 Altair kernel: [17601.348817] sd 10:0:4:0: [sde] tag#2 Sense Key : Not Ready [current] 
Oct 14 22:41:43 Altair kernel: [17601.348822] sd 10:0:4:0: [sde] tag#2 Add. Sense: Logical unit not ready, initializing command required
Oct 14 22:41:43 Altair kernel: [17601.348827] sd 10:0:4:0: [sde] tag#2 CDB: Read(10) 28 00 1e 80 09 18 00 00 08 00
Oct 14 22:41:43 Altair kernel: [17601.348830] blk_update_request: I/O error, dev sde, sector 511707416
```

Could the m/b on the way out or do i have more the one suspect disk :confused:

---

### Post by Harpz on 2016-11-04
Any pointers, anyone?

---

