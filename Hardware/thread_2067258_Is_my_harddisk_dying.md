---
title: "Is my harddisk dying?"
date: 2012-10-06
forum: Hardware
---

### Post by Erik1984 on 2012-10-06
Since more than a year ago I'm occasionally plagued by a hanging *buntu. Everytime this has happened the problem could be related to "FPDMA QUEUED" errors in the kernel log. Like in this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559) As this problem is really really annoying (makes your computer unreliable) I want to take a better look and determine if its the drive or just a linux kernel thing.

I have run multiple SMART tests the past year and everytime the disk passed the test. The resent extended (more than 2 hours) test does present read errors but no pending sectors. Also the test could be completed. Furthermore I booted the Ultimate Boot CD and the Western Digital diagnostics tool found no errors on a full scan.

Another weird thing is Windows in this regard. I have had Vista running on this machine for 2 years without any apparent HDD errors (at least no 'show stoppers' for the OS). Presently I have a Windows 7 / Kubuntu dual boot and again never a sign of hard drive trouble in W7. 

This is (hard) driving me insane, can anyone shed a light on this situation, what should I do? 

Below I have provided some relevant lines from /var/log/kern.log and the results from a SMART test performed today.

This is one of the caught situations where my *buntu install hangs:
```
Sep 30 17:30:33 mycomputer kernel: [31175.824062] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x6 frozen
Sep 30 17:30:33 mycomputer kernel: [31175.824074] ata1.00: failed command: READ FPDMA QUEUED
Sep 30 17:30:33 mycomputer kernel: [31175.824086] ata1.00: cmd 60/40:00:00:15:7e/00:00:38:00:00/40 tag 0 ncq 32768 in
Sep 30 17:30:33 mycomputer kernel: [31175.824089]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 30 17:30:33 mycomputer kernel: [31175.824095] ata1.00: status: { DRDY }
Sep 30 17:30:33 mycomputer kernel: [31175.824100] ata1.00: failed command: WRITE FPDMA QUEUED
Sep 30 17:30:33 mycomputer kernel: [31175.824110] ata1.00: cmd 61/20:08:18:30:f9/00:00:34:00:00/40 tag 1 ncq 16384 out
Sep 30 17:30:33 mycomputer kernel: [31175.824113]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 30 17:30:33 mycomputer kernel: [31175.824119] ata1.00: status: { DRDY }
Sep 30 17:30:33 mycomputer kernel: [31175.824124] ata1.00: failed command: WRITE FPDMA QUEUED
Sep 30 17:30:33 mycomputer kernel: [31175.824133] ata1.00: cmd 61/18:10:20:1b:0b/00:00:32:00:00/40 tag 2 ncq 12288 out
Sep 30 17:30:33 mycomputer kernel: [31175.824136]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 30 17:30:33 mycomputer kernel: [31175.824140] ata1.00: status: { DRDY }
Sep 30 17:30:33 mycomputer kernel: [31175.824149] ata1: hard resetting link
Sep 30 17:30:34 mycomputer kernel: [31176.316050] ata1: softreset failed (device not ready)
Sep 30 17:30:34 mycomputer kernel: [31176.316059] ata1: applying PMP SRST workaround and retrying
Sep 30 17:30:34 mycomputer kernel: [31176.488053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 30 17:30:34 mycomputer kernel: [31176.511416] ata1.00: configured for UDMA/133
Sep 30 17:30:34 mycomputer kernel: [31176.524026] ata1.00: device reported invalid CHS sector 0
Sep 30 17:30:34 mycomputer kernel: [31176.524033] ata1.00: device reported invalid CHS sector 0
Sep 30 17:30:34 mycomputer kernel: [31176.524038] ata1.00: device reported invalid CHS sector 0
Sep 30 17:30:34 mycomputer kernel: [31176.524052] ata1: EH complete
Sep 30 17:31:04 mycomputer kernel: [31206.880065] ata1.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x6 frozen
Sep 30 17:31:04 mycomputer kernel: [31206.880185] ata1.00: failed command: READ FPDMA QUEUED
Sep 30 17:31:04 mycomputer kernel: [31206.880267] ata1.00: cmd 60/40:10:00:15:7e/00:00:38:00:00/40 tag 2 ncq 32768 in
Sep 30 17:31:04 mycomputer kernel: [31206.880269]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 30 17:31:04 mycomputer kernel: [31206.880460] ata1.00: status: { DRDY }
Sep 30 17:31:04 mycomputer kernel: [31206.880520] ata1: hard resetting link
Sep 30 17:31:05 mycomputer kernel: [31207.372037] ata1: softreset failed (device not ready)
Sep 30 17:31:05 mycomputer kernel: [31207.372135] ata1: applying PMP SRST workaround and retrying
Sep 30 17:31:05 mycomputer kernel: [31207.544059] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 30 17:31:05 mycomputer kernel: [31207.574052] ata1.00: configured for UDMA/133
Sep 30 17:31:05 mycomputer kernel: [31207.588038] ata1.00: device reported invalid CHS sector 0
Sep 30 17:31:05 mycomputer kernel: [31207.588053] ata1: EH complete
Sep 30 17:31:35 mycomputer kernel: [31237.856070] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Sep 30 17:31:35 mycomputer kernel: [31237.856191] ata1.00Sep 30 20:57:34 mycomputer kernel: imklog 5.8.6, log source = /proc/kmsg started.
```Here are the results from
```
sudo smartctl -a /dev/sda
```after an extended selftest:
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-31-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD5000AACS-00ZUB0
Serial Number:    WD-WCASU2847586
LU WWN Device Id: 5 0014ee 2014e7ec9
Firmware Version: 01.01B01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Oct  6 14:59:14 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (13980) seconds.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 163) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   198   197   051    Pre-fail  Always       -       31671
  3 Spin_Up_Time            0x0003   167   161   021    Pre-fail  Always       -       4633
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3304
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       15556
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3300
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       134
193 Load_Cycle_Count        0x0032   016   016   000    Old_age   Always       -       552064
194 Temperature_Celsius     0x0022   112   100   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       33
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     15555         -
# 2  Extended offline    Completed without error       00%     15455         -
# 3  Short offline       Completed without error       00%     15452         -
# 4  Conveyance offline  Completed without error       00%     15439         -
# 5  Extended offline    Completed without error       00%     15255         -
# 6  Short offline       Completed without error       00%     15247         -
# 7  Short offline       Completed without error       00%     14841         -
# 8  Extended offline    Completed without error       00%     12729         -
# 9  Short offline       Completed without error       00%     12649         -
#10  Extended offline    Completed without error       00%     12266         -
#11  Short offline       Completed without error       00%     12264         -
#12  Short offline       Aborted by host               10%     12263         -
#13  Conveyance offline  Completed without error       00%     11071         -
#14  Extended offline    Completed without error       00%     11070         -
#15  Short offline       Completed without error       00%     11016         -

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

### Post by Yellow Pasque on 2012-10-06
I would try turning off ncq (boot with libata.force=noncq flag).

---

### Post by Erik1984 on 2012-10-06
> **Temüjin said:**
> I would try turning off ncq (boot with libata.force=noncq flag).

Thanks for the reply. Guess I have to add this to the grub config? Doe this flag has any possible negative consequences?

---

### Post by Yellow Pasque on 2012-10-06
Yeah, you would add it to /etc/default/grub right after the quiet keyword (still within the parentheses), then you would save the file and run:
```
sudo update-grub
```

The worst that could happen is slightly reduced performance. From what I remember of NCQ benches on mechanical hard disks, desktop workloads didn't show a lot of benefit (and some drives/controllers were actually slower) with NCQ. Server workloads are a different story..

---

### Post by Erik1984 on 2012-10-07
Thanks again. I added the option and Kubuntu booted fine. So at least it didn't do any harm :P It's hard to tell if the problem is solved cause it occurs at irregular intervals.

---

### Post by Erik1984 on 2012-10-07
Unfortunately Kubuntu hung again and looking at the kernel log showed the cause: ata errors. It did recover though and I could continue normal operation and shut down my system properly (I've booted into Windows now :() Also I could grab the relevant lines:

```

Oct  7 15:05:19 mycomputer kernel: [19977.824078] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:05:19 mycomputer kernel: [19977.824090] ata1.00: failed command: READ DMA EXT
Oct  7 15:05:19 mycomputer kernel: [19977.824103] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:05:19 mycomputer kernel: [19977.824105]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:05:19 mycomputer kernel: [19977.824111] ata1.00: status: { DRDY }
Oct  7 15:05:19 mycomputer kernel: [19977.824120] ata1: hard resetting link
Oct  7 15:05:19 mycomputer kernel: [19978.316035] ata1: softreset failed (device not ready)
Oct  7 15:05:19 mycomputer kernel: [19978.316044] ata1: applying PMP SRST workaround and retrying
Oct  7 15:05:19 mycomputer kernel: [19978.488055] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  7 15:05:19 mycomputer kernel: [19978.513335] ata1.00: configured for UDMA/133
Oct  7 15:05:19 mycomputer kernel: [19978.528028] ata1.00: device reported invalid CHS sector 0
Oct  7 15:05:19 mycomputer kernel: [19978.528044] ata1: EH complete
Oct  7 15:05:50 mycomputer kernel: [20008.928133] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:05:50 mycomputer kernel: [20008.928173] ata1.00: failed command: READ DMA EXT
Oct  7 15:05:50 mycomputer kernel: [20008.928185] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:05:50 mycomputer kernel: [20008.928188]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:05:50 mycomputer kernel: [20008.928194] ata1.00: status: { DRDY }
Oct  7 15:05:50 mycomputer kernel: [20008.928203] ata1: hard resetting link
Oct  7 15:05:50 mycomputer kernel: [20009.420051] ata1: softreset failed (device not ready)
Oct  7 15:05:50 mycomputer kernel: [20009.420061] ata1: applying PMP SRST workaround and retrying
Oct  7 15:05:50 mycomputer kernel: [20009.592043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  7 15:05:50 mycomputer kernel: [20009.620215] ata1.00: configured for UDMA/133
Oct  7 15:05:51 mycomputer kernel: [20009.636027] ata1.00: device reported invalid CHS sector 0
Oct  7 15:05:51 mycomputer kernel: [20009.636044] ata1: EH complete
Oct  7 15:06:21 mycomputer kernel: [20039.904077] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:06:21 mycomputer kernel: [20039.904194] ata1.00: failed command: READ DMA EXT
Oct  7 15:06:21 mycomputer kernel: [20039.904269] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:06:21 mycomputer kernel: [20039.904271]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:06:21 mycomputer kernel: [20039.904469] ata1.00: status: { DRDY }
Oct  7 15:06:21 mycomputer kernel: [20039.904529] ata1: hard resetting link
Oct  7 15:06:21 mycomputer kernel: [20040.396047] ata1: softreset failed (device not ready)
Oct  7 15:06:21 mycomputer kernel: [20040.396054] ata1: applying PMP SRST workaround and retrying
Oct  7 15:06:21 mycomputer kernel: [20040.568054] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  7 15:06:21 mycomputer kernel: [20040.594347] ata1.00: configured for UDMA/133
Oct  7 15:06:21 mycomputer kernel: [20040.608027] ata1.00: device reported invalid CHS sector 0
Oct  7 15:06:21 mycomputer kernel: [20040.608045] ata1: EH complete
Oct  7 15:06:52 mycomputer kernel: [20070.880072] ata1: limiting SATA link speed to 1.5 Gbps
Oct  7 15:06:52 mycomputer kernel: [20070.880083] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:06:52 mycomputer kernel: [20070.880202] ata1.00: failed command: READ DMA EXT
Oct  7 15:06:52 mycomputer kernel: [20070.880276] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:06:52 mycomputer kernel: [20070.880278]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:06:52 mycomputer kernel: [20070.880470] ata1.00: status: { DRDY }
Oct  7 15:06:52 mycomputer kernel: [20070.880530] ata1: hard resetting link
Oct  7 15:06:52 mycomputer kernel: [20071.372051] ata1: softreset failed (device not ready)
Oct  7 15:06:52 mycomputer kernel: [20071.372145] ata1: applying PMP SRST workaround and retrying
Oct  7 15:06:52 mycomputer kernel: [20071.544053] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct  7 15:06:52 mycomputer kernel: [20071.568391] ata1.00: configured for UDMA/133
Oct  7 15:06:52 mycomputer kernel: [20071.584047] ata1.00: device reported invalid CHS sector 0
Oct  7 15:06:52 mycomputer kernel: [20071.584067] ata1: EH complete
Oct  7 15:07:23 mycomputer kernel: [20101.856108] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:07:23 mycomputer kernel: [20101.856230] ata1.00: failed command: READ DMA EXT
Oct  7 15:07:23 mycomputer kernel: [20101.856305] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:07:23 mycomputer kernel: [20101.856308]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:07:23 mycomputer kernel: [20101.856501] ata1.00: status: { DRDY }
Oct  7 15:07:23 mycomputer kernel: [20101.856561] ata1: hard resetting link
Oct  7 15:07:23 mycomputer kernel: [20102.348051] ata1: softreset failed (device not ready)
Oct  7 15:07:23 mycomputer kernel: [20102.348147] ata1: applying PMP SRST workaround and retrying
Oct  7 15:07:23 mycomputer kernel: [20102.520052] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct  7 15:07:23 mycomputer kernel: [20102.542494] ata1.00: configured for UDMA/133
Oct  7 15:07:23 mycomputer kernel: [20102.556043] ata1.00: device reported invalid CHS sector 0
Oct  7 15:07:23 mycomputer kernel: [20102.556065] ata1: EH complete
Oct  7 15:07:54 mycomputer kernel: [20132.832061] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 15:07:54 mycomputer kernel: [20132.832183] ata1.00: failed command: READ DMA EXT
Oct  7 15:07:54 mycomputer kernel: [20132.832258] ata1.00: cmd 25/00:00:80:39:7e/00:02:38:00:00/e0 tag 0 dma 262144 in
Oct  7 15:07:54 mycomputer kernel: [20132.832261]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct  7 15:07:54 mycomputer kernel: [20132.832452] ata1.00: status: { DRDY }
Oct  7 15:07:54 mycomputer kernel: [20132.832512] ata1: hard resetting link
Oct  7 15:07:54 mycomputer kernel: [20133.324042] ata1: softreset failed (device not ready)
Oct  7 15:07:54 mycomputer kernel: [20133.324135] ata1: applying PMP SRST workaround and retrying
Oct  7 15:07:54 mycomputer kernel: [20133.496056] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct  7 15:07:54 mycomputer kernel: [20133.516610] ata1.00: configured for UDMA/133
Oct  7 15:07:54 mycomputer kernel: [20133.532048] ata1.00: device reported invalid CHS sector 0
Oct  7 15:07:54 mycomputer kernel: [20133.532077] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  7 15:07:54 mycomputer kernel: [20133.532084] sd 0:0:0:0: [sda]  Sense Key : Aborted Command [current] [descriptor]
Oct  7 15:07:54 mycomputer kernel: [20133.532092] Descriptor sense data with sense descriptors (in hex):
Oct  7 15:07:54 mycomputer kernel: [20133.532096]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  7 15:07:54 mycomputer kernel: [20133.532114]         00 00 00 00 
Oct  7 15:07:54 mycomputer kernel: [20133.532124] sd 0:0:0:0: [sda]  Add. Sense: No additional sense information
Oct  7 15:07:54 mycomputer kernel: [20133.532131] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 38 7e 39 80 00 02 00 00
Oct  7 15:07:54 mycomputer kernel: [20133.532145] end_request: I/O error, dev sda, sector 947796352
Oct  7 15:07:54 mycomputer kernel: [20133.532309] ata1: EH complete

```

This looks serious:
```

end_request: I/O error, dev sda, sector 947796352

```

Maybe it is the disk itself having bad sectors. But still, why does Windows never reports a problem with the drive then?

---

### Post by Erik1984 on 2012-11-05
I upgraded to 12.10 recently, but the problem persists :(

```

Nov  5 23:07:12 mycomputer kernel: [18628.213595] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:07:12 mycomputer kernel: [18628.213607] ata1.00: failed command: READ DMA EXT
Nov  5 23:07:12 mycomputer kernel: [18628.213618] ata1.00: cmd 25/00:40:18:3b:79/00:00:36:00:00/e0 tag 0 dma 32768 in
Nov  5 23:07:12 mycomputer kernel: [18628.213624] ata1.00: status: { DRDY }
Nov  5 23:07:12 mycomputer kernel: [18628.213632] ata1: hard resetting link
Nov  5 23:07:12 mycomputer kernel: [18628.705296] ata1: softreset failed (device not ready)
Nov  5 23:07:12 mycomputer kernel: [18628.705306] ata1: applying PMP SRST workaround and retrying
Nov  5 23:07:12 mycomputer kernel: [18628.877213] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  5 23:07:12 mycomputer kernel: [18628.907061] ata1.00: configured for UDMA/133
Nov  5 23:07:12 mycomputer kernel: [18628.921181] ata1.00: device reported invalid CHS sector 0
Nov  5 23:07:12 mycomputer kernel: [18628.921224] Descriptor sense data with sense descriptors (in hex):
Nov  5 23:07:12 mycomputer kernel: [18628.921314] ata1: EH complete
Nov  5 23:08:37 mycomputer kernel: [18714.180246] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:08:37 mycomputer kernel: [18714.180258] ata1.00: failed command: READ DMA EXT
Nov  5 23:08:37 mycomputer kernel: [18714.180270] ata1.00: cmd 25/00:00:00:d0:2c/00:01:33:00:00/e0 tag 0 dma 131072 in
Nov  5 23:08:37 mycomputer kernel: [18714.180275] ata1.00: status: { DRDY }
Nov  5 23:08:37 mycomputer kernel: [18714.180283] ata1: hard resetting link
Nov  5 23:08:38 mycomputer kernel: [18714.671933] ata1: softreset failed (device not ready)
Nov  5 23:08:38 mycomputer kernel: [18714.671942] ata1: applying PMP SRST workaround and retrying
Nov  5 23:08:38 mycomputer kernel: [18714.843850] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  5 23:08:38 mycomputer kernel: [18714.874721] ata1.00: configured for UDMA/133
Nov  5 23:08:38 mycomputer kernel: [18714.887811] ata1.00: device reported invalid CHS sector 0
Nov  5 23:08:38 mycomputer kernel: [18714.887844] Descriptor sense data with sense descriptors (in hex):
Nov  5 23:08:38 mycomputer kernel: [18714.887927] ata1: EH complete
Nov  5 23:09:26 mycomputer kernel: [18763.176112] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:09:26 mycomputer kernel: [18763.176123] ata1.00: failed command: READ DMA EXT
Nov  5 23:09:26 mycomputer kernel: [18763.176134] ata1.00: cmd 25/00:20:d0:9e:75/00:00:37:00:00/e0 tag 0 dma 16384 in
Nov  5 23:09:26 mycomputer kernel: [18763.176139] ata1.00: status: { DRDY }
Nov  5 23:09:26 mycomputer kernel: [18763.176148] ata1: hard resetting link
Nov  5 23:09:27 mycomputer kernel: [18763.667807] ata1: softreset failed (device not ready)
Nov  5 23:09:27 mycomputer kernel: [18763.667817] ata1: applying PMP SRST workaround and retrying
Nov  5 23:09:27 mycomputer kernel: [18763.839713] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  5 23:09:27 mycomputer kernel: [18763.869547] ata1.00: configured for UDMA/133
Nov  5 23:09:27 mycomputer kernel: [18763.883682] ata1.00: device reported invalid CHS sector 0
Nov  5 23:09:27 mycomputer kernel: [18763.883719] Descriptor sense data with sense descriptors (in hex):
Nov  5 23:09:27 mycomputer kernel: [18763.883805] ata1: EH complete
Nov  5 23:10:11 mycomputer kernel: [18808.110317] ata1: limiting SATA link speed to 1.5 Gbps
Nov  5 23:10:11 mycomputer kernel: [18808.110329] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:10:11 mycomputer kernel: [18808.110336] ata1.00: failed command: READ DMA EXT
Nov  5 23:10:11 mycomputer kernel: [18808.110347] ata1.00: cmd 25/00:30:f0:9e:75/00:00:37:00:00/e0 tag 0 dma 24576 in
Nov  5 23:10:11 mycomputer kernel: [18808.110352] ata1.00: status: { DRDY }
Nov  5 23:10:11 mycomputer kernel: [18808.110361] ata1: hard resetting link
Nov  5 23:10:12 mycomputer kernel: [18808.602009] ata1: softreset failed (device not ready)
Nov  5 23:10:12 mycomputer kernel: [18808.602019] ata1: applying PMP SRST workaround and retrying
Nov  5 23:10:12 mycomputer kernel: [18808.773932] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  5 23:10:12 mycomputer kernel: [18808.805477] ata1.00: configured for UDMA/133
Nov  5 23:10:12 mycomputer kernel: [18808.817882] ata1.00: device reported invalid CHS sector 0
Nov  5 23:10:12 mycomputer kernel: [18808.817918] Descriptor sense data with sense descriptors (in hex):
Nov  5 23:10:12 mycomputer kernel: [18808.818002] ata1: EH complete
Nov  5 23:11:24 mycomputer kernel: [18881.060442] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:11:24 mycomputer kernel: [18881.060454] ata1.00: failed command: READ DMA EXT
Nov  5 23:11:24 mycomputer kernel: [18881.060465] ata1.00: cmd 25/00:00:00:62:70/00:01:33:00:00/e0 tag 0 dma 131072 in
Nov  5 23:11:24 mycomputer kernel: [18881.060470] ata1.00: status: { DRDY }
Nov  5 23:11:24 mycomputer kernel: [18881.060479] ata1: hard resetting link
Nov  5 23:11:25 mycomputer kernel: [18881.552126] ata1: softreset failed (device not ready)
Nov  5 23:11:25 mycomputer kernel: [18881.552134] ata1: applying PMP SRST workaround and retrying
Nov  5 23:11:25 mycomputer kernel: [18881.724043] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  5 23:11:25 mycomputer kernel: [18881.744713] ata1.00: configured for UDMA/133
Nov  5 23:11:25 mycomputer kernel: [18881.760005] ata1.00: device reported invalid CHS sector 0
Nov  5 23:11:25 mycomputer kernel: [18881.760041] Descriptor sense data with sense descriptors (in hex):
Nov  5 23:11:25 mycomputer kernel: [18881.760129] ata1: EH complete
Nov  5 23:12:22 mycomputer kernel: [18939.075170] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  5 23:12:22 mycomputer kernel: [18939.075182] ata1.00: failed command: READ DMA EXT
Nov  5 23:12:22 mycomputer kernel: [18939.075194] ata1.00: cmd 25/00:20:d8:9e:76/00:00:38:00:00/e0 tag 0 dma 16384 in
Nov  5 23:12:22 mycomputer kernel: [18939.075199] ata1.00: status: { DRDY }
Nov  5 23:12:22 mycomputer kernel: [18939.075208] ata1: hard resetting link
Nov  5 23:12:23 mycomputer kernel: [18939.566820] ata1: softreset failed (device not ready)
Nov  5 23:12:23 mycomputer kernel: [18939.566829] ata1: applying PMP SRST workaround and retrying

```

---

### Post by Yellow Pasque on 2012-11-05
What mobo do you have, and do you have the latest BIOS?
```
sudo dmidecode
```

---

### Post by Erik1984 on 2012-11-06
> **Temüjin said:**
> What mobo do you have, and do you have the latest BIOS?
```
sudo dmidecode
```

```

# dmidecode 2.11
SMBIOS 2.5 present.
54 structures occupying 1975 bytes.
Table at 0x000FC580.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: American Megatrends Inc.
        Version: A7501MLN.10E
        Release Date: 04/10/2008
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
        BIOS Revision: 8.14

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: MEDIONPC
        Product Name: MS-7501
        Version: 2.1
        Serial Number: To Be Filled By O.E.M.
        UUID: 9CDF285D-35B8-DC11-9B85-7A08306CF635
        Wake-up Type: Power Switch
        SKU Number: To Be Filled By O.E.M.
        Family: To Be Filled By O.E.M.

```

The mother board is a MSI MS-7501. I have never updated the BIOS. Do you need more output from that command? 

FWIW: After yesterday's crash I booted into Windows (everything apparently fine there) and ran an extended SMART self-test in HDTune:
```

HD Tune: WDC WD5000AACS-00ZUB0 Error Scan

Scanned data   : 476749 MB
Damaged Blocks : 0.0 %
Elapsed Time   : 145:30

HD Tune: WDC WD5000AACS-00ZUB0 Health

ID                               Current  Worst    ThresholdData     Status   
(01) Raw Read Error Rate         198      197      51       32582    Ok       
(03) Spin Up Time                166      161      21       4658     Ok       
(04) Start/Stop Count            97       97       0        3371     Ok       
(05) Reallocated Sector Count    200      200      140      0        Ok       
(07) Seek Error Rate             100      253      51       0        Ok       
(09) Power On Hours Count        79       79       0        15869    Ok       
(0A) Spin Retry Count            100      100      51       0        Ok       
(0B) Calibration Retry Count     100      100      51       0        Ok       
(0C) Power Cycle Count           97       97       0        3367     Ok       
(C0) Power Off Retract Count     200      200      0        137      Ok       
(C1) Load Cycle Count            14       14       0        559183   Ok       
(C2) Temperature                 112      100      0        35       Ok       
(C4) Reallocated Event Count     200      200      0        0        Ok       
(C5) Current Pending Sector      200      200      0        0        Ok       
(C6) Offline Uncorrectable       200      200      0        0        Ok       
(C7) Ultra DMA CRC Error Count   200      199      0        33       Ok       
(C8) Write Error Rate            200      200      51       0        Ok       

Power On Time         : 15869
Health Status         : Ok

```

---

