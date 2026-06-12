---
title: "Hard drive problems - transfer speed goes down to 0 after few seconds"
date: 2011-10-20
forum: Hardware
---

### Post by Kdar on 2011-10-20
I am trying to back up files from internal drive of my HTPC.

First I just tried to re-install Linux. Re-format everything except for /home partition. That didn't work.

Then I tried to back up using some older Ubuntu live CD that I had laying around. That didn't work. Coping files end up with Input/output error.

Then I took this drive out and connected it internally to sata and power in my main (working) computer (I had to wait until Linux would start to boot and then connect sata cable).
Drive was acting very slow (it would always try to load its contents) and if I tried to copy something it would eventually end up with same Input/Output error (especially in case of big files.... Usually transfer speed gradually goes dawn to 0 as its trying to copy the file(s)). I was able to copy really small files.. like 5-8Mb files (audio files.. etc).. But anything bigger, in rancher of several Gb, I would have this problem.

Also.. after a while, I would loose connection to this drive and if I try to connect again by using mount, it drives me an error about not knowing the type of partition (it is ext4).

Does anyone have idea what I can do? I bought a new 3tb external drive mainly to copy everything from this problematic drive (which has about ~1.5Tb of stuff).

What can I do? Don't want to loose all those files... Have a lot of tv-shows and movies on there..

---

### Post by diasf on 2011-10-20
Honestly, seems fried to me. What is smart saying?

And sorry to say, but kinda late to be worried with the files.... never have only one copy of something you don't wanna lose.

---

### Post by Kdar on 2011-10-20
What do you mean by smart?

---

### Post by diasf on 2011-10-20
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

And notice that an damaged HD can still pass the smart test...

---

### Post by LinuxFan999 on 2011-10-20
How old is the Hard drive in your HTPC? What Brand is it?

---

### Post by Kdar on 2011-10-20
Its not that old. I bought it in April of 2010.

I bought this one:
Western Digital Caviar Green WD20EARS
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136513](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136513)

---

### Post by diasf on 2011-10-20
Despite the fact that age and brand are factors, they usually aren't the issue (I have a 7 yro Hitachi, IDE that still works like a charm.... and a seagate that made chose a pope -white smoke- 3 weeks after bought... right after i restored the backups...).

You already swapped PCs. The problem is obviously on the drive...

Run:

smartctl /dev/sdX -a

And paste the output, please

---

### Post by Kdar on 2011-10-20
Here is output:

PS. Is it ok that I connect another sata drive (the one what has problems) after Linux starts up? Because if I do it before I apply power to computer, it tries to boot from that broken drive.
```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0-ARCH] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD15EARS-00Z5B1
Serial Number:    WD-WMAVU2332306
LU WWN Device Id: 5 0014ee 0acbf3614
Firmware Version: 80.00A80
User Capacity:    1,500,301,910,016 bytes [1.50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Oct 20 16:34:34 2011 CDT
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
data collection:                (33600) seconds.
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
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3031) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   193   051    Pre-fail  Always       -       4162
  3 Spin_Up_Time            0x0027   195   182   021    Pre-fail  Always       -       5250
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       231
  5 Reallocated_Sector_Ct   0x0033   186   186   140    Pre-fail  Always       -       109
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       7
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6342
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       229
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       102
193 Load_Cycle_Count        0x0032   052   052   000    Old_age   Always       -       446993
194 Temperature_Celsius     0x0022   120   098   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   091   091   000    Old_age   Always       -       109
197 Current_Pending_Sector  0x0032   195   195   000    Old_age   Always       -       1294
198 Offline_Uncorrectable   0x0030   200   199   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   189   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 24228 (device log contains only the most recent five errors)
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

Error 24228 occurred at disk power-on lifetime: 6342 hours (264 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00      00:14:05.574  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:14:05.567  IDENTIFY DEVICE
  c8 00 08 00 01 00 e0 00      00:14:05.567  READ DMA
  ec 00 00 00 00 00 a0 00      00:14:05.553  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:14:05.547  SET FEATURES [Set transfer mode]

Error 24227 occurred at disk power-on lifetime: 6342 hours (264 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 08 00 01 00 e0  Device Fault; Error: ABRT 8 sectors at LBA = 0x00000100 = 256

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 01 00 e0 00      00:14:05.567  READ DMA
  ec 00 00 00 00 00 a0 00      00:14:05.553  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:14:05.547  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:14:05.540  IDENTIFY DEVICE
  c8 00 08 00 01 00 e0 00      00:14:05.540  READ DMA

Error 24226 occurred at disk power-on lifetime: 6342 hours (264 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00      00:14:05.547  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:14:05.540  IDENTIFY DEVICE
  c8 00 08 00 01 00 e0 00      00:14:05.540  READ DMA
  ec 00 00 00 00 00 a0 00      00:14:05.520  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:14:05.514  SET FEATURES [Set transfer mode]

Error 24225 occurred at disk power-on lifetime: 6342 hours (264 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 08 00 01 00 e0  Device Fault; Error: ABRT 8 sectors at LBA = 0x00000100 = 256

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 01 00 e0 00      00:14:05.540  READ DMA
  ec 00 00 00 00 00 a0 00      00:14:05.520  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:14:05.514  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:14:05.507  IDENTIFY DEVICE
  c8 00 08 00 01 00 e0 00      00:14:05.507  READ DMA

Error 24224 occurred at disk power-on lifetime: 6342 hours (264 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00      00:14:05.514  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:14:05.507  IDENTIFY DEVICE
  c8 00 08 00 01 00 e0 00      00:14:05.507  READ DMA
  ec 00 00 00 00 00 a0 00      00:14:05.487  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:14:05.481  SET FEATURES [Set transfer mode]

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


```

---

### Post by diasf on 2011-10-20
If your drive is hotswap capable, won't matter... if he isn't, well...  (most sata are, afaik)

You got 24k errors there. Even if the smart parameters are reporting pass, those errors might mean something.

---

### Post by Kdar on 2011-10-24
I gave up trying to recover the data and tried to write drive with all 0s (using software from WD) and to my surprise, it fixed the drive.. at least for now.

I was able to install Linux on there again.

---

### Post by jmate24 on 2011-10-24
i've only had trouble with that same drive and i just had to go to segate and a smaller drive and everything works now for me except i may have to get a second drive because i am running out of space.

---

