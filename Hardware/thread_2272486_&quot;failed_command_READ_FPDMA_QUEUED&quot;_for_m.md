---
title: "&quot;failed command: READ FPDMA QUEUED&quot; for my WD10EZEX-08M2NA0 drive."
date: 2015-04-07
forum: Hardware
---

### Post by negora on 2015-04-07
Hello:

I've an ASUS M5A97 EVO R2.0 motherboard and 3 hard disks. One of them is a Western Digital Caviar Blue 1TB SATA3 (model WD10EZEX-08M2NA0). I use it to store the /home directory exclusively. Some times, when I boot my computer, the kernel logs several messages that indicate that there have been errors with this drive. Some times it doesn't prevent me from logging in with my user, but others it seems to get stuck in that step. Then I've to reset my computer abruptly and pass the "fsck" command to fix whatever that has failed. I believe that the error messages only appear during the boot. I've checked the "dmesg" output after hours of work and nothing else related to this failure has been logged.

```

[    1.792425] ata2: SATA max UDMA/133 abar m1024@0xfe50b000 port 0xfe50b180 irq 19
[    2.281038] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.281598] ata2.00: ATA-9: WDC WD10EZEX-08M2NA0, 01.01A01, max UDMA/100
[    2.281601] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.282311] ata2.00: configured for UDMA/100
[    9.259321] ata2.00: exception Emask 0x0 SAct 0x8 SErr 0x0 action 0x6
[    9.259351] ata2.00: irq_stat 0x40000008
[    9.259362] ata2.00: failed command: READ FPDMA QUEUED
[    9.259376] ata2.00: cmd 60/08:18:08:00:00/00:00:00:00:00/40 tag 3 ncq 4096 in
[    9.259398] ata2.00: status: { DRDY ERR }
[    9.259407] ata2.00: error: { ICRC ABRT }
[    9.259419] ata2: hard resetting link
[    9.748016] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    9.749363] ata2.00: configured for UDMA/100
[    9.749373] ata2: EH complete
[   10.341975] ata2.00: exception Emask 0x2 SAct 0x100 SErr 0x200401 action 0x6
[   10.341989] ata2.00: irq_stat 0x44000008
[   10.341999] ata2: SError: { RecovData Proto BadCRC }
[   10.342009] ata2.00: failed command: READ FPDMA QUEUED
[   10.342021] ata2.00: cmd 60/20:40:00:08:00/00:00:00:00:00/40 tag 8 ncq 16384 in
[   10.342043] ata2.00: status: { DRDY ERR }
[   10.342051] ata2.00: error: { ICRC ABRT }
[   10.342062] ata2: hard resetting link
[   10.831301] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   10.832752] ata2.00: configured for UDMA/100
[   10.832784] ata2: EH complete
[   11.123146] ata2.00: exception Emask 0x10 SAct 0x1000 SErr 0x200100 action 0x6 frozen
[   11.123165] ata2.00: irq_stat 0x08000000, interface fatal error
[   11.123178] ata2: SError: { UnrecovData BadCRC }
[   11.123189] ata2.00: failed command: READ FPDMA QUEUED
[   11.123204] ata2.00: cmd 60/f8:60:10:09:80/00:00:04:00:00/40 tag 12 ncq 126976 in
[   11.123227] ata2.00: status: { DRDY }
[   11.123238] ata2: hard resetting link
[   11.622694] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   11.623851] ata2.00: configured for UDMA/100
[   11.623912] ata2: EH complete
[   11.631038] ata2: limiting SATA link speed to 3.0 Gbps
[   11.631043] ata2.00: exception Emask 0x10 SAct 0x2000 SErr 0x200100 action 0x6 frozen
[   11.631077] ata2.00: irq_stat 0x08000000, interface fatal error
[   11.631100] ata2: SError: { UnrecovData BadCRC }
[   11.631123] ata2.00: failed command: READ FPDMA QUEUED
[   11.631147] ata2.00: cmd 60/f0:68:18:09:80/00:00:04:00:00/40 tag 13 ncq 122880 in
[   11.631207] ata2.00: status: { DRDY }
[   11.631228] ata2: hard resetting link
[   12.126528] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   12.127952] ata2.00: configured for UDMA/100
[   12.127975] ata2: EH complete

```

I've checked the output of "smartctl" and I've not seen anything wrong. However, I admit that I might not be reading that figures correctly:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-48-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA 6Gb/s)
Device Model:     WDC WD10EZEX-08M2NA0
Serial Number:    WD-WCC3F3180973
LU WWN Device Id: 5 0014ee 2b49d97fe
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Apr  7 09:36:00 2015 CEST
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
data collection:                (11400) seconds.
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
recommended polling time:        ( 118) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   172   167   021    Pre-fail  Always       -       2383
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       503
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       2957
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       503
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       26
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       476
194 Temperature_Celsius     0x0022   116   105   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   198   000    Old_age   Always       -       27
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               80%      2941         -
# 2  Conveyance offline  Completed without error       00%      2919         -
# 3  Short offline       Completed without error       00%      2876         -
# 4  Short offline       Completed without error       00%      2793         -
# 5  Extended offline    Completed without error       00%      2769         -
# 6  Extended offline    Interrupted (host reset)      70%      2767         -
# 7  Extended offline    Completed without error       00%      2675         -
# 8  Extended offline    Completed without error       00%      2642         -
# 9  Short offline       Completed without error       00%      2623         -
#10  Short offline       Completed without error       00%      1948         -
#11  Short offline       Completed without error       00%      1579         -
#12  Short offline       Completed without error       00%      1061         -
#13  Short offline       Completed without error       00%       119         -

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

I've read that it could be because of the SATA or power cables, which could be faulty. I've connected the cables of my DVD drive but the result has been the same. I've also tried disabling the NCQ feature in this unit, but it hasn't helped. I did this because I interpreted from a bug report that [the chipset of my mother board might have some type of problem under ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559")Ubuntu (it's an AMD 970/SB950). 

In other computers, when the kernel warned me about errors in a SATA unit, "smartctl" showed obvious signs that the drive was faulty. However, in this case, I'm completely lost. Can you help me?

Thank you!

---

### Post by negora on 2015-04-11
Yesterday I purchased a new unit of the same model of hard drive (manufactured in December 2,014 instead of in February 2,104). I copied my data from the older disk to the newer one and tested it. It worked fine. This morning I've turned my computer on, but the same error has arisen!!! :S

I'm really surprised. Days ago I replaced the cables of this disk by the ones of other of my hard drives, one which works OK (a Samsung SpinPoint F2). But it failed too, so I discarded that it was a faulty cable. Could it be an issue between the model of my motherboard and the model of the disk?

PS: in both units the SMART UDMA_CRC_Error_Count counter has increased.

---

### Post by negora on 2015-04-20
Finally I returned the new Western Digital Caviar Blue 1TB SATA3 and purchased a Seagate Barracuda 7200.14 1TB SATA (ST1000DM003). After copying the data from one disk to the other one, I rebooted my computer several times and it never failed. I kept my computer running for several hours, then rebooted it again, but it didn't fail either. I thought that the error had been solved, until I turned on my computer the next morning and it showed the same failure messages!!! >_<

So it was clear that I hadn't been persevering enough when I checked the cables days ago. Because the error came up randomly, I guess that I didn't give it enough time to appear again during some of my checks. But after trying more combinations, plugging the hard drive here and there, **it resulted that the 2nd SATA connector of my main board has some kind of problem.** Because I've been using the same hard drive for 2 days, but plugged into a different connector, and it has been working fine. I hope that my conclusion isn't too premature and it fails again. Sincerely, I doubt it, because in the previous days it already failed one or two times in the same interval of time.

---

### Post by negora on 2015-07-22
Last update. It failed again :S .

However, I found the real cause thanks to a blog article called ["Power supply failures can be pretty annoying to find"]("http://eliasoenal.com/2012/10/31/power-supply-failures-can-be-pretty-annoying-to-find/"). **It resulted to be the PSU.** The voltages weren't the right ones. It was a good a PSU from the glory days of Enermax, but even a good PSU may fail after ~10 years of service, he he he. So I replaced it by a Seasonic G-550 and all my problems vanished. It has passed almost 2 months without errors :) .

PS: I opened the Enermax PSU and several capacitors were damaged. I'll try to replace them, just for fun.

---

### Post by VMC on 2015-07-23
> **negora said:**
> Last update. It failed again :S .

However, I found the real cause thanks to a blog article called ["Power supply failures can be pretty annoying to find"]("http://eliasoenal.com/2012/10/31/power-supply-failures-can-be-pretty-annoying-to-find/"). **It resulted to be the PSU.** The voltages weren't the right ones. It was a good a PSU from the glory days of Enermax, but even a good PSU may fail after ~10 years of service, he he he. So I replaced it by a Seasonic G-550 and all my problems vanished. It has passed almost 2 months without errors :) .

PS: I opened the Enermax PSU and several capacitors were damaged. I'll try to replace them, just for fun.

Negore,
That's an interesting find you linked to. I'll have to remember that. I have a WD10EZEX also, which this topic got my attention. Mine went bad, but it was the HD itself.

---

### Post by negora on 2015-07-23
For me it has been a great discovering. Because the SMART information of my hard drive didn't show any error. Indeed, time ago I discarded another hard drive for the same reason: the SMART info was OK but it was causing errors during the boot of the OS. I hope that article is also helpful for you and more people ;) .

---

