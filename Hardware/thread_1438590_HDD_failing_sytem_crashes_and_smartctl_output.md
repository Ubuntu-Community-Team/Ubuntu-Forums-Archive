---
title: "HDD failing? sytem crashes and smartctl output"
date: 2010-03-25
forum: Hardware
---

### Post by dash86no on 2010-03-25
Hello, 

I am experiencing system freezes, the type where ALT sysrqd REISUB etc have no effect, and the only escape is a hard reboot. 

These have been happening mainly when encoding DVDs with the tovid suite, but not exclusively so. 

Although I am running Lucid alpha 64 bit, I suspect hardware failure. I ran Memtest86+ for 24 hours. There were 31 passes and 0 errors, so I am assuming the memory is good. 

For the HDD, I downloaded smartmontools. Please see the information below:

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MJA2500BH G2
Serial Number:    K90DT95279UB
Firmware Version: 00000018
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Thu Mar 25 20:58:54 2010 JST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (1574) seconds.
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
recommended polling time: 	 ( 223) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       41191
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       71368704
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       68
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       9019431321600
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3843
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       241
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       3641
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       35 (Lifetime Min/Max 14/46)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       9769
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       974782464
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       26832
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       3732307968246
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       239         -
# 2  Short offline       Completed without error       00%       235         -
# 3  Short offline       Completed without error       00%         0         -

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

+++++++++++++++++++++++++++++++++++++++++

Notice the RAW values for 5 and 196. I am getting warnings in gsmartcontrol that "this drive has a non-zero raw value, but there are no SMART warnings yet. This could be an indication of future failures. 

My system is fairly new, and the HDD is not yet in smartmontools database. Could this be a cause of the RAW reading being off? Or is it looking like my HDD might be screwed?
Any other ideas for testing the HDD? I will be running spinrite overnight to see what kind of feedback it comes back with. 

Thanks,

DA

---

### Post by dash86no on 2010-03-26
OK, I ran spinrite and it ended without showing up any errors. 

I am currently running mprime to test for cpu defects:

[http://en.wikipedia.org/wiki/MPrime](http://en.wikipedia.org/wiki/MPrime)

It's a cracking program that will put a load on your CPU for an extended period of time, and stop and tell you if there are any errors. Also, the version I downloaded off the site supports multi-core so there is no need to run separate instances of the program for each core. 

Anyway, can anyway familiar with SMART confirm that the output from smartmontools I posted above is anything to worry about?

Thanks,

DA

---

### Post by dash86no on 2010-03-26
Ok, I've been running mprime for 12 hours solid with no errors. I'm pretty sure I can rule out CPU and memory defects at this point. 

So, back to my original question, can anyone out there help me interpret the gsmartcontrol output?  Are there any other HDD testing utilities I can use to diagnose the health of the disk?

---

### Post by tgalati4 on 2010-03-26
I'm more concerned with the following:

Raw_Read_Error_Rate 0x000f 100 100 046

and

Reallocated_Sector_Ct 0x0033 100 100 024

Each manufacturer uses there own raw data and conversion factors for assigning SMART attributes.  If I'm reading the output correctly, your raw (uncorrected) read errors have reached 46% out of 100% of the threshold value to trigger a SMART prefail warning.  Your sector relocation has reached 24% of the programmed threshold.

Try running badblocks on the drive.  It will take a while:

sudo badblocks /dev/sda

Encoding DVD's or recording live music is stressful on hard disks because the write heads are in continuous use.  They get hot because writing data takes a lot more electrical current through the head than reading data.  With continuous writing--say 20 minutes to rip a DVD, the heads don't have time to cool down.  New drives are susceptable because they haven't broken in yet and the compensation mechanisms (temperature, bearing wear, arm jitter, etc) may not be able to correct for such conditions in a single session.  Hence read errors start to show up.

Check your log files:

cat /var/log/syslog
cat /var/log/syslog.0 

cat /var/log/syslog | grep error
or
cat /var/log/syslog | grep Error

---

### Post by dash86no on 2010-03-27
OK, did some more research, and found out the following:

The key to the smartlctl output is the two values: VALUE and THRESH

The VALUE is based on the RAW VALUE, but is "normalized" by the HDD's firmware to a number between 0 and 100. (Some are 200). The higher the value, the better. 

As long as VALUE remains above THRESH, then that attribute is considered healthy, and there is no SMART warning. If the VALUE drops to equal or below the THRESH, your HDD is close to failure and the disk will give you the appropriate SMART warning. 

In my case, all VALUES are at their healthiest, as far as I can make out. The RAW values look a bit scary, but these are being normalized by firmware unique to the HDD maker showing healthy values. Added to the fact that my HDD model is not in the smartctl database, it is clear that the RAW value by itself is not making much sense here, as it is most likely being misinterpreted by smartctl. 



ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x000f 100 100 046 Pre-fail Always - 41191
2 Throughput_Performance 0x0005 100 100 030 Pre-fail Offline - 71368704
3 Spin_Up_Time 0x0003 100 100 025 Pre-fail Always - 1
4 Start_Stop_Count 0x0032 100 100 000 Old_age Always - 68
5 Reallocated_Sector_Ct 0x0033 100 100 024 Pre-fail Always - 9019431321600
7 Seek_Error_Rate 0x000f 100 100 047 Pre-fail Always - 3843
8 Seek_Time_Performance 0x0005 100 100 019 Pre-fail Offline - 0
9 Power_On_Hours 0x0032 100 100 000 Old_age Always - 241
10 Spin_Retry_Count 0x0013 100 100 020 Pre-fail Always - 0
12 Power_Cycle_Count 0x0032 100 100 000 Old_age Always - 66
192 Power-Off_Retract_Count 0x0032 100 100 000 Old_age Always - 14
193 Load_Cycle_Count 0x0032 100 100 000 Old_age Always - 3641
194 Temperature_Celsius 0x0022 100 100 000 Old_age Always - 35 (Lifetime Min/Max 14/46)
195 Hardware_ECC_Recovered 0x001a 100 100 000 Old_age Always - 9769
196 Reallocated_Event_Count 0x0032 100 100 000 Old_age Always - 974782464
197 Current_Pending_Sector 0x0012 100 100 000 Old_age Always - 0
198 Offline_Uncorrectable 0x0010 100 100 000 Old_age Offline - 0
199 UDMA_CRC_Error_Count 0x003e 200 253 000 Old_age Always - 0
200 Multi_Zone_Error_Rate 0x000f 100 100 060 Pre-fail Always - 26832
203 Run_Out_Cancel 0x0002 100 100 000 Old_age Always - 3732307968246
240 Head_Flying_Hours 0x003e 200 200 000 Old_age Always - 0

---

### Post by dash86no on 2010-03-27
Considering memtest86+, mprime, spinrite and smartctl are indicating there are no problems with my hardware, I will now try to install 9.10 64 bit and do some DVD authoring with that. 

If I am able to do this without issue, then it would indicate a problem with Lucid, and I would have to move this discussion over to the lucid discussion forum. 

Cheers, 

DA

---

### Post by tgalati4 on 2010-03-27
I stand corrected. The first number is the normalized value, the third number is the warning threshold.

---

### Post by dash86no on 2010-03-27
Well my system is running very stable under 9.10; I've been encoding 3 dvds simultaneously for hours now and no crashes. 

So my issue is solved. There is nothing wrong with my HDD; this was a lucid issue. 

Thanks

DA

---

