---
title: "Inspiron 1420 Spindown/overheating"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by Penguinnerd on 2008-01-12
I noticed a rapidly increasing Load count on my HD. I used the "hdparm -B 255 /dev/sda" fix. 

I think this fixed the load count, but I can't be sure as I suddenly had to shut down my laptop due to a temp of 38 celsius and climbing at like 1 degree per two minutes.

How do I reverse the fix, or reduce it to lower the temp?

---

### Post by Penguinnerd on 2008-01-12
"Bump"

BTW, thanks to a 9 volt battery, an old cooling fan and some books to prop it up, I am back on the laptop. 

I need at least some power management because it has a definite impact on the temp. (And I can't stand having to be paranoid about it)

---

### Post by Penguinnerd on 2008-01-13
Hello?

Here's my output to "sudo smartctl -d ata -a /dev/sda" directly after startup.


> smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD800BEVS-75RST0
Serial Number:    WD-WXCY07594112
Firmware Version: 04.01G04
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Jan 13 08:52:42 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (3600) seconds.
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
recommended polling time:        (  49) minutes.
Conveyance self-test routine
recommended polling time:        (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   158   157   021    Pre-fail  Always       -       1066
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       48
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   100   253   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       37
 10 Spin_Retry_Count        0x0012   100   253   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       43
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       304
194 Temperature_Celsius     0x0022   117   093   000    Old_age   Always       -       26
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -
# 2  Short offline       Completed without error       00%         0         -

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

### Post by Penguinnerd on 2008-01-13
I would really appreciate a little help from someone. It's probably a very simple fix that I just don't know about.

---

### Post by Penguinnerd on 2008-01-13
I just read that the fix that I used is not supposed to be  permanent, but My Load cycle count only changes on a reboot and my temp is quite high. What's the deal?

---

### Post by Penguinnerd on 2008-01-14
Could someone just give me a hint or something?

---

### Post by Yellow Pasque on 2008-01-14
HD's should be rated to at least 55C. So what is your temp maxing out at?

---

### Post by Penguinnerd on 2008-01-14
Thanks for the reply.

I think it leveled at 42 before I set up my improvised cooling. So I guess it should be fine, but It's a little close for comfort based on what I've read. I was under the impression that 40 was quite high.

I don't believe there are any "Fixes" (For Load Cycle Count) active on my machine right now but I observe that my Load Cycle Count only increases on a suspend/Hibernate/reboot now. (And that it seems fairly warm.)

Edit: Forgot to mention, right now I'm holding at around 30-33 degrees.

---

### Post by Yellow Pasque on 2008-01-14
[http://www.wdc.com/en/products/Products.asp?DriveID=102](http://www.wdc.com/en/products/Products.asp?DriveID=102)
> Temperature (Metric)
Operating	5° C to 60° C
Non-operating	-40° C to 65° C

---

### Post by Penguinnerd on 2008-01-15
Thanks, that's definitely reassuring. I guess I'm fine, but if anyone knows why my load cycle count stopped increasing constantly, do tell. (But It's definitely not a problem!)

---

