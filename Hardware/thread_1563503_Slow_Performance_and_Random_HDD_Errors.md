---
title: "Slow Performance and Random HDD Errors"
date: 2010-08-29
forum: Hardware
---

### Post by jbro164 on 2010-08-29
Sorry in advance for the long post, but I want to show everything I have tried so far.

I have a media PC that does a few things, but mainly is a MythTV PVR.  It has been running well for a while, however i did notice that the MythTV Menu was getting slower.  A reboot seemed to fix this, so I assumed it was just running out of ram to keep the menu in cache.  However about 3-4 days after the reboot, the computer crashed, and now I can't get it to work again.  The current situation is that (at first) the boot was spitting out a number of different errors, (i can't remember what they all were, as I was not really sure what was going on at that stage, but they were things about can't load init filesystem etc).

I started trying a few things with loading up live CD's, and now am at a point where the system takes about 10-15 minutes to load up (normally <1 minute), and is very slow and unresponsive.  /var/log/messages spits out the following errors:
```

Aug 29 11:19:42 mythtv kernel: [ 1340.127328] ata4: EH complete
Aug 29 11:19:44 mythtv kernel: [ 1342.949133] ata4.00: configured for UDMA/33
Aug 29 11:19:44 mythtv kernel: [ 1342.949162] sd 3:0:0:0: [sda] Unhandled sense code
Aug 29 11:19:44 mythtv kernel: [ 1342.949168] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 29 11:19:44 mythtv kernel: [ 1342.949176] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Aug 29 11:19:44 mythtv kernel: [ 1342.949187] Descriptor sense data with sense descriptors (in hex):
Aug 29 11:19:44 mythtv kernel: [ 1342.949192]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Aug 29 11:19:44 mythtv kernel: [ 1342.949214]         01 86 28 97
Aug 29 11:19:44 mythtv kernel: [ 1342.949223] sd 3:0:0:0: [sda] Add. Sense: Address mark not found for data field
Aug 29 11:19:44 mythtv kernel: [ 1342.949234] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 01 86 28 97 00 00 08 00
Aug 29 11:19:44 mythtv kernel: [ 1342.949303] ata4: EH complete
Aug 29 11:19:47 mythtv kernel: [ 1345.960398] ata4.00: configured for UDMA/33
Aug 29 11:19:47 mythtv kernel: [ 1345.960427] ata4: EH complete
Aug 29 11:19:50 mythtv kernel: [ 1348.782426] ata4.00: configured for UDMA/33
Aug 29 11:19:50 mythtv kernel: [ 1348.782452] ata4: EH complete
Aug 29 11:19:53 mythtv kernel: [ 1351.604822] ata4.00: configured for UDMA/33
Aug 29 11:19:53 mythtv kernel: [ 1351.604851] ata4: EH complete
Aug 29 11:19:56 mythtv kernel: [ 1354.426638] ata4.00: configured for UDMA/33
Aug 29 11:19:56 mythtv kernel: [ 1354.426668] ata4: EH complete
Aug 29 11:19:59 mythtv kernel: [ 1357.248457] ata4.00: configured for UDMA/33
Aug 29 11:19:59 mythtv kernel: [ 1357.248485] ata4: EH complete
Aug 29 11:20:01 mythtv kernel: [ 1360.071298] ata4.00: configured for UDMA/33
Aug 29 11:20:01 mythtv kernel: [ 1360.071329] sd 3:0:0:0: [sda] Unhandled sense code
Aug 29 11:20:01 mythtv kernel: [ 1360.071335] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 29 11:20:01 mythtv kernel: [ 1360.071343] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Aug 29 11:20:01 mythtv kernel: [ 1360.071353] Descriptor sense data with sense descriptors (in hex):
Aug 29 11:20:01 mythtv kernel: [ 1360.071359]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Aug 29 11:20:01 mythtv kernel: [ 1360.071381]         01 86 28 97
Aug 29 11:20:01 mythtv kernel: [ 1360.071390] sd 3:0:0:0: [sda] Add. Sense: Address mark not found for data field
Aug 29 11:20:01 mythtv kernel: [ 1360.071401] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 01 86 28 97 00 00 08 00
Aug 29 11:20:01 mythtv kernel: [ 1360.071472] ata4: EH complete
Aug 29 11:20:05 mythtv kernel: [ 1363.515791] ata4.00: configured for UDMA/33
Aug 29 11:20:05 mythtv kernel: [ 1363.515816] ata4: EH complete

```
This just keeps repeating every minute or so.

I am not really sure what these errors really mean, and have not been able to find anything on google.

I have run a memtest (only one complete test at the moment, with no errors (recently I had HDD errors, and it turned out that the ram was faulty, so I got it replaced under warranty)

I have booted into the liveCD, and had a look at the disk utility's smart data. The output:

```
sudo smartctl /dev/sda -a
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce All                                                                                         en
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EADS-00S2B0
Serial Number:    WD-WCAVY1267649
Firmware Version: 01.00A01
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Aug 29 11:47:54 2010 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85) Offline data collection activity
                                        was aborted by an interrupting command                                                                                          from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 241) Self-test routine in progress...
                                        10% of test remaining.
Total time to complete Offline
data collection:                 (30660) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off sup                                                                                         port.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN                                                                                         _FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always                                                                                                -       35701
  3 Spin_Up_Time            0x0027   162   146   021    Pre-fail  Always                                                                                                -       8858
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always                                                                                                -       64
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always                                                                                                -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always                                                                                                -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always                                                                                                -       5853
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always                                                                                                -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always                                                                                                -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always                                                                                                -       59
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always                                                                                                -       40
193 Load_Cycle_Count        0x0032   109   109   000    Old_age   Always                                                                                                -       273047
194 Temperature_Celsius     0x0022   106   096   000    Old_age   Always                                                                                                -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always                                                                                                -       0
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always                                                                                                -       1445
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline                                                                                               -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always                                                                                                -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline                                                                                               -       0

SMART Error Log Version: 1
ATA Error Count: 11281 (device log contains only the most recent five errors)
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

Error 11281 occurred at disk power-on lifetime: 5843 hours (243 days + 11 hours                                                                                         )
  When the command that caused the error occurred, the device was active or idl                                                                                         e.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 6f 24 87 e1  Error: AMNF 8 sectors at LBA = 0x0187246f = 25633903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 6f 24 87 e1 08      00:49:08.172  READ DMA
  ec 00 00 00 00 00 a0 08      00:49:08.170  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:49:08.170  SET FEATURES [Set transfer mode]

Error 11280 occurred at disk power-on lifetime: 5843 hours (243 days + 11 hours                                                                                         )
  When the command that caused the error occurred, the device was active or idl                                                                                         e.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 6f 24 87 e1  Error: AMNF 8 sectors at LBA = 0x0187246f = 25633903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 6f 24 87 e1 08      00:49:05.364  READ DMA
  ec 00 00 00 00 00 a0 08      00:49:05.362  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:49:05.362  SET FEATURES [Set transfer mode]

Error 11279 occurred at disk power-on lifetime: 5843 hours (243 days + 11 hours                                                                                         )
  When the command that caused the error occurred, the device was active or idl                                                                                         e.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 6f 24 87 e1  Error: AMNF 8 sectors at LBA = 0x0187246f = 25633903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 6f 24 87 e1 08      00:49:02.555  READ DMA
  ec 00 00 00 00 00 a0 08      00:49:02.553  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:49:02.553  SET FEATURES [Set transfer mode]

Error 11278 occurred at disk power-on lifetime: 5843 hours (243 days + 11 hours                                                                                         )
  When the command that caused the error occurred, the device was active or idl                                                                                         e.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 6f 24 87 e1  Error: AMNF 8 sectors at LBA = 0x0187246f = 25633903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 6f 24 87 e1 08      00:48:59.747  READ DMA
  ec 00 00 00 00 00 a0 08      00:48:59.745  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:48:59.745  SET FEATURES [Set transfer mode]

Error 11277 occurred at disk power-on lifetime: 5843 hours (243 days + 11 hours                                                                                         )
  When the command that caused the error occurred, the device was active or idl                                                                                         e.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 6f 24 87 e1  Error: AMNF 8 sectors at LBA = 0x0187246f = 25633903

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 6f 24 87 e1 08      00:48:56.939  READ DMA
  ec 00 00 00 00 00 a0 08      00:48:56.937  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:48:56.937  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LB                                                                                         A_of_first_error
# 1  Conveyance offline  Completed without error       00%      4020         -
# 2  Conveyance offline  Completed: read failure       90%      4015         16                                                                                         93160661

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
the disk utility gui says current pending sector rate is quite high, but everything else is good.  I started an extended self-check, which said it would take "Ten's on minutes".  It has been about 10 hours, and still has not quite finished (may have hung now), but doesn't seem to show anything.

I have also run an fsck on the HDD under the live CD, and it says the FS is fine.

I have run an hdparm -tT to test the disk speed, adn get the following numbers (seems ok)
```
sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   1440 MB in  2.00 seconds = 720.31 MB/sec
 Timing buffered disk reads:  214 MB in  3.00 seconds =  71.29 MB/sec
```

No errors are logged to the /var/log/messages file when in the livecd environment regarding the HDD, althouh I am basically only doing the Disk checks.


I am reluctant to go and replace the HDD (it is under warranty, but don't have another HDD big enough to take all the data) as there don't seem to be any real errors relating to the data on the disk.

My system specs are as follows:

Nvidia ION Board with Atom Processor
4GB ram (although only 3GB usable by the system)
Ubuntu 10.04 (64bit)
WD Cavier Green HDD (1.5TB) on SATA

Any Help / Incite would be greatly appreciated

Thanks in advance

---

### Post by jbro164 on 2010-08-31
Just some extra Information that Might help - I seem to have isolated it mostly to when I copy between Partitions on the same drive, or use applications that are dealing a lot between 2 partitions (e.g. the mythTV Backend), then I get the errors.  If I am not doing this, then it seems to work ok (although seems to be slow still)

---

