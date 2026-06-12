---
title: "HDD dying ? NEED HELP Too many Raw_Read_Error_Rate messages"
date: 2017-03-14
forum: Hardware
---

### Post by xdealmeida on 2017-03-14
Hello ALL,

It's been quite some time now I see these messages:
**Mar 14 22:10:54 SERVER smartd[1238]: Device: /dev/sda [SAT], Failed SMART usage Attribute: 1 Raw_Read_Error_Rate.**

But I have no idea if this is serious or not.
```
xabix@SERVER:~$ sudo hdparm -I /dev/sda

/dev/sda:


ATA device, with non-removable media
        Model Number:       Corsair Neutron SSD                     
        Serial Number:      132679020000973400A8
        Firmware Revision:  M311    
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
        Supported: 8 7 6 5 
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   0
        heads           16      0
        sectors/track   63      0
        --
        LBA    user addressable sectors:  250069680
        LBA48  user addressable sectors:  250069680
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:      122104 MBytes
        device size with M = 1000*1000:      128035 MBytes (128 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: Solid State Device
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
                WRITE_DMA_QUEUED_FUA_EXT
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
           *    Device automatic Partial to Slumber transitions
           *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
                Non-Zero buffer offsets in DMA Setup FIS
           *    DMA Setup Auto-Activate optimization
                Device-initiated interface power management
                In-order data delivery
           *    Software settings preservation
           *    Data Set Management TRIM supported (limit 1 block)
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct
xabix@SERVER:~$ sudo hdparm -t /dev/sda


/dev/sda:
 Timing buffered disk reads: 1086 MB in  3.00 seconds = 361.46 MB/sec
```

```
xabix@SERVER:/var/log$ sudo smartctl -a /dev/sdasmartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-66-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     Corsair Neutron SSD
Serial Number:    132679020000973400A8
Firmware Version: M311
User Capacity:    128 035 676 160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 6.0 Gb/s
Local Time is:    Tue Mar 14** 22:21:34 2017 CET**
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


General SMART Values:
Offline data collection status:  (0x02) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (    7) seconds.
Offline data collection
capabilities:                    (0x19) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0002) Does not save SMART data before
                                        entering power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (   5) minutes.


SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
**  1 Raw_Read_Error_Rate     0x000e   001   001   006    Old_age   Always   FAILING_NOW 62462**
  5 Reallocated_Sector_Ct   0x0032   253   253   036    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   065   065   000    Old_age   Always       -       31459
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       141
171 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0032   253   253   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   029   000   000    Old_age   Always       -       29 (Min/Max 21/61)
201 Unknown_SSD_Attribute   0x000e   100   100   000    Old_age   Always       -       0
204 Soft_ECC_Correction     0x000e   001   001   000    Old_age   Always       -       62462
231 Temperature_Celsius     0x0033   052   052   010    Pre-fail  Always       -       49
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       198915
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       12338
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       2808
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       13881351


SMART Error Log Version: 1
ATA Error Count: 2513 (device log contains only the most recent five errors)
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


Error 2513 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 fe 00 00 00 40  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 05 fe 00 00 00 40 40  13d+17:27:51.550  SET FEATURES [Enable APM]
  60 48 10 08 2e 04 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 08 08 d0 5f ae 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 88 00 50 2e 04 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 10 f0 18 d3 19 40 40  13d+17:27:51.550  READ FPDMA QUEUED


Error 2512 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00   at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 27 19 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 19 00 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 26 da 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 1a c0 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 25 9b 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT


Error 2511 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00   at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 27 19 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 19 00 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 26 da 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 1a c0 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 25 9b 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT


Error 2510 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 45 00 4f c2 e0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 e0 e0  13d+17:27:37.690  NOP [Abort queued commands]
  00 00 00 00 00 00 e0 e0  13d+17:27:37.690  NOP [Abort queued commands]
  25 00 63 02 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT
  25 00 01 01 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT
  25 00 01 00 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT


Error 2509 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  e7 00 00 00 00 00 a0 a0  13d+17:27:21.260  FLUSH CACHE
  60 08 c8 d8 0b 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 c0 88 09 01 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 b8 c8 0c 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 b0 20 0d 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     30955         -
# 2  Short offline       Completed without error       00%     30955         -
# 3  Extended offline    Completed without error       00%     30417         -
# 4  Extended offline    Completed without error       00%         1         -
# 5  Short offline       Completed without error       00%         1         -


Selective Self-tests/Logging not supported
```

Thank you for your insight. Hopefull the drive is still fine :)
XabiX

Few minutes after:
```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-66-generic] (local build)Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     Corsair Neutron SSD
Serial Number:    132679020000973400A8
Firmware Version: M311
User Capacity:    128 035 676 160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 6.0 Gb/s
Local Time is:    Tue Mar 14** 22:42:37 2017 CET**
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


General SMART Values:
Offline data collection status:  (0x02) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  366) seconds.
Offline data collection
capabilities:                    (0x19) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0002) Does not save SMART data before
                                        entering power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (   5) minutes.


SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000e   001   001   006    Old_age   Always   FAILING_NOW 73515
  5 Reallocated_Sector_Ct   0x0032   253   253   036    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   065   065   000    Old_age   Always       -       31460
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       141
171 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0032   253   253   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   030   000   000    Old_age   Always       -       30 (Min/Max 21/61)
201 Unknown_SSD_Attribute   0x000e   100   100   000    Old_age   Always       -       0
204 Soft_ECC_Correction     0x000e   001   001   000    Old_age   Always       -       73515
231 Temperature_Celsius     0x0033   052   052   010    Pre-fail  Always       -       49
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       198920
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       12338
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       2808
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       13897608


SMART Error Log Version: 1
ATA Error Count: 2513 (device log contains only the most recent five errors)
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


Error 2513 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 fe 00 00 00 40  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 05 fe 00 00 00 40 40  13d+17:27:51.550  SET FEATURES [Enable APM]
  60 48 10 08 2e 04 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 08 08 d0 5f ae 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 88 00 50 2e 04 40 40  13d+17:27:51.550  READ FPDMA QUEUED
  60 10 f0 18 d3 19 40 40  13d+17:27:51.550  READ FPDMA QUEUED


Error 2512 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00   at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 27 19 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 19 00 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 26 da 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 1a c0 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 25 9b 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT


Error 2511 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00   at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 27 19 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 19 00 07 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 26 da 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 1a c0 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT
  25 00 25 9b 06 b5 e0 e0  13d+17:27:44.020  READ DMA EXT


Error 2510 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 50 45 00 4f c2 e0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 e0 e0  13d+17:27:37.690  NOP [Abort queued commands]
  00 00 00 00 00 00 e0 e0  13d+17:27:37.690  NOP [Abort queued commands]
  25 00 63 02 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT
  25 00 01 01 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT
  25 00 01 00 00 00 e0 e0  13d+17:27:37.690  READ DMA EXT


Error 2509 occurred at disk power-on lifetime: 31422 hours (1309 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 00 00 00 00 00 00


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  e7 00 00 00 00 00 a0 a0  13d+17:27:21.260  FLUSH CACHE
  60 08 c8 d8 0b 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 c0 88 09 01 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 b8 c8 0c 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED
  60 08 b0 20 0d 81 40 40  13d+17:27:21.260  READ FPDMA QUEUED


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     31459         -
# 2  Short offline       Completed without error       00%     30955         -
# 3  Short offline       Completed without error       00%     30955         -
# 4  Extended offline    Completed without error       00%     30417         -
# 5  Extended offline    Completed without error       00%         1         -
# 6  Short offline       Completed without error       00%         1         -


Selective Self-tests/Logging not supported



```

---

### Post by xdealmeida on 2017-03-24
Hello Everyone,

I am getting more and more notifications about this issue and I am scared to loose all the data on my HDD. Can someone tell if this is critical or can be ignored?

The messages are:
> This message was generated by the smartd daemon running on:

   host name:  SERVER
   DNS domain: [Empty]


The following warning/error was logged by the smartd daemon:


Device: /dev/sda [SAT], Failed SMART usage Attribute: 1 Raw_Read_Error_Rate.


Device info:
Corsair Neutron SSD, S/N:132679020000973400A8, FW:M311, 128 GB


For details see host's SYSLOG.


You can also use the smartctl utility for further investigation.


---

### Post by xdealmeida on 2017-04-02
Up.
Anyone who is some insight on how critical or not the issue is? or what can be done to fix such messages?

---

### Post by oldos2er on 2017-04-02
Backup your data NOW and get a new hard disk?

---

### Post by Autodave on 2017-04-02
You should have been backing up all along: sounds like time for a new HD. At the very least, that one needs cleared and formatted while checking for errors.  I have seen similar probs when machine is not shut down properly and bits and pieces of data or lost.

---

### Post by SeijiSensei on 2017-04-02
Are you using just the one SSD for all of Linux?  I think SSDs are fine for the OS itself, but I'd put data on a separate SATA drive.  Format that drive as ext4, copy the contents of /home onto it, and mount it into the OS as /home.  I might consider creating two partitions on the SATA drive, one for /home and one for /var.  Those are the two parts of the filesystem that get the most use.

---

### Post by xdealmeida on 2017-04-04
Thanks for the answers. It seems I should plan to replace it as there may be no way to fix it without formatting the drive and reinstalling for a result that is unsure.

Yes this SSD is being used for my main Ubuntu OS in ext4.
```
Disk /dev/sda: 119,2 GiB, 128035676160 bytes, 250069680 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xef700b09


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 233529343 233527296 111,4G 83 Linux
/dev/sda2       233531390 250068991  16537602   7,9G  5 Extended
/dev/sda5       233531392 250068991  16537600   7,9G 82 Linux swap / Solaris

xabix@SERVER:~$ mount | grep sda
/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro,data=ordered)


syslog
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda, type changed from 'scsi' to 'sat'
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], opened
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], Corsair Neutron SSD, S/N:132679020000973400A8, FW:M311, 128 GB
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], not found in smartd database.
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], can't monitor Current_Pending_Sector count - no Attribute 197
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], can't monitor Offline_Uncorrectable count - no Attribute 198
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], is SMART capable. Adding to "monitor" list.
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], state read from /var/lib/smartmontools/smartd.Corsair_Neutron_SSD-132679020000973400A8.ata.state
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], Failed SMART usage Attribute: 1 Raw_Read_Error_Rate.
Apr  4 23:00:00 SERVER smartd[1073]: Device: /dev/sda [SAT], ATA error count increased from 2518 to 2523
Apr  4 23:00:00 SERVER kernel: [    1.276279] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
Apr  4 23:00:00 SERVER kernel: [    1.276299] sd 0:0:0:0: [sda] Write Protect is off
Apr  4 23:00:00 SERVER kernel: [    1.276301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  4 23:00:00 SERVER kernel: [    1.276309] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  4 23:00:00 SERVER kernel: [    1.277278]  sda: sda1 sda2 < sda5 >
Apr  4 23:00:00 SERVER kernel: [    1.277864] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  4 23:00:00 SERVER kernel: [    6.370505] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr  4 23:00:00 SERVER kernel: [    6.764658] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Apr  4 23:00:00 SERVER kernel: [    7.301669] Adding 8268796k swap on /dev/sda5.  Priority:-1 extents:1 across:8268796k SSFS
Apr  4 23:00:01 SERVER smartd[1073]: Device: /dev/sda [SAT], state written to /var/lib/smartmontools/smartd.Corsair_Neutron_SSD-132679020000973400A8.ata.state

```

I tried running an ext4 check at boot but didn't fix anything. So there is no way to understand if the issue is HW linked or the partition/OS files?

Thanks

---

