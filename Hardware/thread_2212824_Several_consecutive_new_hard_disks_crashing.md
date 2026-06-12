---
title: "Several consecutive new hard disks crashing"
date: 2014-03-23
forum: Hardware
---

### Post by anbelo on 2014-03-23
Hello. During the last two years I've had several consecutive hard disk crashes (fortunately covered by the guaranty, but now it's running out). They were WD and Seagate disks, unsealed in front of me by the seller. Everything works fine for a few months, but then the system starts freezing for about 30 seconds, more and more often, until the hard disk fails. Before the latest crash I found entries like these appearing in syslog when those "freezes" happen:

Mar 23 14:14:58 CYA-Ubu kernel: [18704.992050] ata1: lost interrupt (Status 0x50)
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992077] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992085] ata1.00: failed command: READ DMA EXT
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992095] ata1.00: cmd 25/00:40:00:cd:52/00:00:59:00:00/e0 tag 0 dma 32768 in
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992095]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992101] ata1.00: status: { DRDY }
Mar 23 14:14:58 CYA-Ubu kernel: [18704.992115] ata1: soft resetting link
Mar 23 14:14:59 CYA-Ubu kernel: [18705.172386] ata1.00: configured for UDMA/133
Mar 23 14:14:59 CYA-Ubu kernel: [18705.172400] ata1.00: device reported invalid CHS sector 0
Mar 23 14:14:59 CYA-Ubu kernel: [18705.172418] ata1: EH complete

I searched for the error and found it could be related to a bad SATA cable, so I replaced it for a new one, but the error kept appearing and eventually the crash happened. I got a new replacement and now after three months the freezes and the errors are back. It seems like there is another component in my computer that is affecting the hard disk. I already replaced the SATA cable, and don't know what to do to detect the root of the problem. Thank you very much for any help you can bring.

---

### Post by anbelo on 2014-03-25
Today a slight variation of the error has appeared (along with the 30 seconds freeze), with no "EXT" at the end of the third line.

Mar 25 14:40:42 CYA-Ubu kernel: [18171.000046] ata1: lost interrupt (Status 0x50)
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000074] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000082] ata1.00: failed command: READ DMA
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000092] ata1.00: cmd c8/00:10:98:53:2d/00:00:00:00:00/ec tag 0 dma 8192 in
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000092]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000097] ata1.00: status: { DRDY }
Mar 25 14:40:42 CYA-Ubu kernel: [18171.000112] ata1: soft resetting link
Mar 25 14:40:42 CYA-Ubu kernel: [18171.172383] ata1.00: configured for UDMA/133
Mar 25 14:40:42 CYA-Ubu kernel: [18171.172397] ata1.00: device reported invalid CHS sector 0
Mar 25 14:40:42 CYA-Ubu kernel: [18171.172414] ata1: EH complete

Any clue of what can be happening would be very welcome. Thank you.

---

### Post by tgalati4 on 2014-03-25
How old is the motherboard?  Have you inspected it for bad capacitors?  It could be a motherboard problem, a power supply problem, or the disk SATA controllers are failing.  What temperatures do these drives operate at?

```
sudo smartctl -a /dev/sda
```

---

### Post by anbelo on 2014-03-25
Hi tgalati4 and thank you for your response. The motherboard is only a pair of years old, as is the power supply. It hasn't been checked for bad capacitors that I know (I mean by the seller/technician; I wouldn't know how to do it). This is the output for the smartctl command. Thank you very much again.

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.8.0-37-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     ST1000DM003-1CH162
Serial Number:    Z1D39P62
LU WWN Device Id: 5 000c50 03cdc0ea4
Firmware Version: CC46
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Mar 25 19:45:33 2014 CET
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
data collection:         (  584) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 116) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x3085)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006    Pre-fail  Always       -       93884528
  3 Spin_Up_Time            0x0003   099   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       156
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       17656873
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1900
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       142
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   067   045    Old_age   Always       -       30 (Min/Max 29/30)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       22
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       164
194 Temperature_Celsius     0x0022   030   040   000    Old_age   Always       -       30 (0 16 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       19580755904373
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2383972873
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2019982125

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1723         -

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

