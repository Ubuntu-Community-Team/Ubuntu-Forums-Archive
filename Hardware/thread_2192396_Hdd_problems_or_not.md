---
title: "Hdd problems or not?"
date: 2013-12-07
forum: Hardware
---

### Post by adrian89 on 2013-12-07
Can someone help me by telling me if my hdd will fail?I am not that good at reading S.M.A.R.T data from Gsmartcontrol.
The issues that I am having is that my laptop starts to freeze whenever I am working inside Windows file explorer(copying/moving), while in ubuntu I do not have this problem, it copies with around 40Mb/s.
It may be my fault for messing up the windows partition, tried to change file permission and settings on it,because it wouldn't let me install something in Program files, so I scheduled a disc check on windows and found bad clusters in a lot of files.
Now, I tried copying some files from Program files of windows to my ubuntu home directory and it gave me a error, on windows I also checked with Hddlife trial and it said the hdd is in excelent shape.

Further is a Gsmartcontrol output.
```
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-14-generic] (local build)Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint MP5
Device Model:     SAMSUNG HM250HJ
Serial Number:    S2J5J1QB605553
LU WWN Device Id: 5 0024e9 004f54502
Firmware Version: 2AK10001
User Capacity:    250,058,268,160 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sat Dec  7 21:27:26 2013 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		( 3060) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  51) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       1728
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   090   089   025    Pre-fail  Always       -       3212
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1772
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       7390
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   094   094   000    Old_age   Always       -       6098
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1776
191 G-Sense_Error_Rate      0x0022   084   084   000    Old_age   Always       -       162892
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   056   026   000    Old_age   Always       -       44 (Min/Max 9/74)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   099   099   000    Old_age   Always       -       79
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       22753
223 Load_Retry_Count        0x0032   094   094   000    Old_age   Always       -       6098
225 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       60253


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      7389         30141482


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_read_failure [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Tough this is more for a windows forum, I asked here because I know here a capable people, and I just want to know if the issue is from the hdd and if it will fail, so I know what to do.

---

### Post by bashiergui on 2013-12-08
I'm not familiar with those tools per se, but if it found bad sectors then I would 
1. boot from an Ubuntu live CD and use gparted to check the hard drive. It will fix errors found. 
2. Then run chkdsk on windows a couple times.
3. Defragment windows. If it's really fragmented then defrag a couple times.

---

### Post by Will_McDade on 2013-12-08
I had a case of this in my old laptop, where it would show in Windows that the disk was fine, and in any linux distro it would say that it had 2184 bad sectors and could die any second. I could easily go with linux's prediction as it was crashing and clicking and stuff. If you notice performance dipping or crashing or wierd sounds coming out of it, follow @bashiergui's advice.

---

### Post by adrian89 on 2013-12-09
The case is that the hdd has no crippling sounds, it was all handy-dandy until I tried copying a 20GB directory(to an upper level) in windows and file explorer started to freeze(unusuall thing since the OS was installed a few hours earlier).In ubuntu partitions there was no problem copying high amount of data from directory to directory like it happened on windows, but when I tried copying the directory 20GB directory from windows partition to my ext4 partition, then I got corrupted files errors.I tried erasing all of the data from HDD and then reinstall my OSs(ubuntu and win).First I made 2 windows partitions one for the os and one to fully format it with normal format and later to remake it as partitions for ubuntu.After that I installed GSmartControl and tried a few self-test which all failed, and then made a quick scan with HDTune trial on windows which gave bad sectors.The best part was that I just got it out of service, because my cooler failed and for my laptop I couldnt find a replacement so I used the ultimate solution, sent it to service. Well hopefully someone heard my plea for a new laptop hdd for christmas, cross your fingers, and thank you for your answers.

---

### Post by adrian89 on 2013-12-09
Also tested my Girlfriend's hdd with GSmart no realocated or pending realocation or raw read error but the funny thing it shows "Reported_Uncorrected value of: 94515036160"

---

### Post by bashiergui on 2013-12-09
You say there was no problem copying on the ubuntu side. Did you validate tat the copy really worked (i.e. did you try to open the copies of the files)? 

A failing drive doesn't necessarily make awful noises. They can fail quietly.

---

### Post by adrian89 on 2013-12-10
Did not verified if the file was working, because after that I formatted my entire HDD.
Well if it falls let it fall while figting :P, Is good that my important data is stored in Ubuntu one.

---

