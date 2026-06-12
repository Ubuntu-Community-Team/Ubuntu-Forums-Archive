---
title: "Hard lockups / Possible SSD Issue"
date: 2013-03-16
forum: Hardware
---

### Post by Thomas Kenobi on 2013-03-16
Since yesterday I've been having the following issue. First I found that my computer had rebooted by itself and was stuck on the GRUB 2 rescue screen with a message indicating it couldn't find the drive. This kept happening at every restart and I eventually fixed it booting through a live USB disk and using boot-repair. Since then I've had the following. On three occasions Ubuntu (and Windows) have hard locked up leaving no option but a restart (no ctrl-alt-backspace or ctrl-alt-del). After reboot grub again goes to rescue and says it can't find the drive. This is fixed by booting from one the other drives (which should have the same grub installation copied), but if afterward I set the boot drive back to the original one it still works... (I have one SSD with the OSs and 2 HDD. Grub is on all three and I have been alternating booting between the two HDDs). Also once BIOS couldn't see the ssd at all, but a restart fixed that.

I have attempted to run some tests on the SSD itself and I have experienced a problem where upon the SMART test will hung on 90% and stay there. SMART tests on the other two drives finish as normal and reveal no serious issues.
SMART data read through SpeedFan reveal a bunch of uncorrectable sectors and recommends a drive replacement (on this drive I either can't read the smart data through smartctl or smartctl can't read it. All I see is the raw values)

Now to the point of this post. Can anyone confirm that this is in fact a drive problem and not an issue with say the M/B controller or bad smart data concealing a different problem?

```
###################################
sudo smartctl -a /dev/sdb
###################################
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Indilinx Barefoot based SSDs
Device Model:     OCZ-VERTEX
Serial Number:    F209P8RE2Q273PQ9M6A2
Firmware Version: 1.6
User Capacity:    96,029,466,624 bytes [96.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Mar 16 11:44:50 2013 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 249)    Self-test routine in progress...
                    90% of test remaining.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x1d) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Abort Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x00)    Error logging NOT supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   0) minutes.
Extended self-test routine
recommended polling time:      (   0) minutes.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   ---   ---   ---    Old_age   Offline      -       5
  9 Power_On_Hours          0x0000   ---   ---   ---    Old_age   Offline      -       18675
 12 Power_Cycle_Count       0x0000   ---   ---   ---    Old_age   Offline      -       452
184 Initial_Bad_Block_Count 0x0000   ---   ---   ---    Old_age   Offline      -       154
195 Program_Failure_Blk_Ct  0x0000   ---   ---   ---    Old_age   Offline      -       0
196 Erase_Failure_Blk_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       1
197 Read_Failure_Blk_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       6
198 Read_Sectors_Tot_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       15214792026
199 Write_Sectors_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       33491820142
200 Read_Commands_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       312125377
201 Write_Commands_Tot_Ct   0x0000   ---   ---   ---    Old_age   Offline      -       342350163
202 Error_Bits_Flash_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       384410997
203 Corr_Read_Errors_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       203023164
204 Bad_Block_Full_Flag     0x0000   ---   ---   ---    Old_age   Offline      -       0
205 Max_PE_Count_Spec       0x0000   ---   ---   ---    Old_age   Offline      -       5000
206 Min_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       5035
207 Max_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       14546
208 Average_Erase_Count     0x0000   ---   ---   ---    Old_age   Offline      -       14092
209 Remaining_Lifetime_Perc 0x0000   ---   ---   ---    Old_age   Offline      -       97
211 SATA_Error_Ct_CRC       0x0000   ---   ---   ---    Old_age   Offline      -       0
212 SATA_Error_Ct_Handshake 0x0000   ---   ---   ---    Old_age   Offline      -       0
213 Indilinx_Internal       0x0000   ---   ---   ---    Old_age   Offline      -       0


Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%       243         -
# 2  Short offline       Aborted by host               90%       243         -
# 3  Short offline       Aborted by host               90%       243         -
# 4  Short offline       Aborted by host               90%       243         -
# 5  Extended offline    Aborted by host               90%       242         -
# 6  Extended offline    Aborted by host               90%       242         -
# 7  Extended offline    Aborted by host               90%       242         -


Device does not support Selective Self Tests/Logging

```



```

###################################
sudo smartctl -l gplog,0x3 /dev/sdb
###################################
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


General Purpose Log 0x03 [Ext. Comprehensive SMART error log], Page 0-0 (of 77)
0000000: 31 75 b9 fd af e6 2d 0b 00 00 00 00 af e6 2d 0b |1u....-.......-.|
0000010: 00 00 00 00 07 00 7f 40 8b 01 00 00 00 00 00 00 |.......@........|
0000020: 05 00 00 00 f4 48 00 00 c4 01 00 00 9a 00 00 00 |.....H..........|
0000030: 00 00 00 00 01 00 00 00 06 00 00 00 00 00 00 00 |................|
0000040: ca df e0 8a 03 00 00 00 e6 6a 4a cc 07 00 00 00 |.........jJ.....|
0000050: a1 b4 9a 12 00 00 00 00 94 15 68 14 00 00 00 00 |..........h.....|
0000060: 87 c5 e9 16 b4 ee 19 0c 00 00 00 00 88 13 00 00 |................|
0000070: ab 13 00 00 d3 38 00 00 0d 37 00 00 61 00 00 00 |.....8...7..a...|
0000080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000090: 01 01 01 00 00 00 00 00 20 20 20 20 20 20 20 20 |........        |
00000a0: 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 20 |                |
00000b0: 20 20 20 20 20 20 20 20 00 00 00 00 00 00 00 00 |        ........|
00000c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000d0: 00 00 00 00 00 00 00 00 00 00 fe ff 00 00 00 00 |................|
00000e0: 5f eb cf 01 d7 98 23 03 3d 56 bd 01 ea 95 ef 01 |_.....#.=V......|
00000f0: bb f9 bd 01 be 52 66 01 fa 02 df 01 3c ba 8a 01 |.....Rf.....<...|
0000100: 9e af 11 02 dc 15 35 02 e8 ed f0 01 63 98 83 01 |......5.....c...|
0000110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
0000160: f1 5a 00 01 c4 20 40 01 15 6f fc 00 e0 0f 00 01 |.Z... @..o......|
0000170: 4f 79 00 01 df 75 df 00 52 79 00 01 ba 73 e9 00 |Oy...u..Ry...s..|
0000180: c6 ea 12 01 07 c3 0d 01 ea 21 0f 01 34 48 e3 00 |.........!..4H..|
0000190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00001a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00001b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00001c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00001d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00001e0: 01 00 01 00 01 01 00 00 3f 10 ff 3f 00 00 00 00 |........?..?....|
00001f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|

```

---

### Post by ahallubuntu on 2013-03-16
~

---

### Post by dabl on 2013-03-16
What mode is your SATA channel set in BIOS?  If it is set to AHCI, change it to "legacy" or "compatibility" or whatever the other choice is, and see whether it makes a difference.  Also swap out the data cable with one that you trust, just in case.

---

