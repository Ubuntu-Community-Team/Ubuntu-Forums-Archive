---
title: "Diagnosing laptop hardware issue when everything seems to check out"
date: 2013-11-29
forum: Hardware
---

### Post by samcan on 2013-11-29
Hi,

I've been having some crazy problems with my laptop (HP Pavilion dv7-2173cl), and have tried to diagnose them but have not been having great success. The major problem is that the laptop randomly slows down and the hard drive light goes lit. This happens both in the Ubuntu 13.10 install and Windows 7 install, even when there is plenty of RAM available.

**Is it the hard drive?**
To diagnose it, I thought it might be a hard drive issue. To this end I checked the SMART data in Ubuntu, and downloaded Seagate's drive checker in Windows. The Seagate tool reported no problems.

I've attached the SMART data from a series of tests I ran in Crunchbang Linux on a live USB. As you can see, all the tests except for the drive temp passed.

```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
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
recommended polling time: 	 ( 136) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       144430528
  3 Spin_Up_Time            0x0002   099   097   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   098   098   000    Pre-fail  Always       -       2238
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       126506976
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6918
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   099   099   020    Pre-fail  Always       -       1823
183 Runtime_Bad_Block       0x0032   100   253   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   094   000    Old_age   Always       -       526
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   040   035   045    Old_age   Always   FAILING_NOW 60 (101 59 61 56)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   058   058   000    Old_age   Always       -       85798
194 Temperature_Celsius     0x0022   060   065   000    Old_age   Always       -       60 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   044   041   000    Old_age   Always       -       144430528
196 Reallocated_Event_Count 0x0033   100   100   036    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

```
Considering that maybe there were bad sectors on the drive, I ran a filesystem check in Windows. It did fix some stuff, but it didn't fix the major problem, which was the laptop acting incredibly slow. If it had been the drive going bad, shouldn't it have marked the bad sectors and thus avoided them?

**Is it the RAM?**
I considered the memory next. To test this, I booted into memtest+86 and ran a complete pass. There were no errors found.

**Is it the CPU?**
I booted into a Crunchbang Linux live USB, and ran cpuburn on the two CPUs for about fifteen minutes. The system was still responsive, and didn't lock up. So I don't think it's the CPU.

**My conclusions**
Despite the SMART data saying the hard drive is good, I think it's wrong. When I'm in the live USB, the system acts very responsive. Is there anything else I could test to ensure it's the hard drive?

Thanks!

---

### Post by electrohandyman501 on 2013-11-29
Is this a new install of both OS's? How old is the laptop? How long have you been using it.

What is your layout of the hard disk, ie... partition sizes, etc.....

Reading the online specs for what you listed only shows 4G total ram with 1-2.+G of it shared for video. Makes me wonder if the system is trying to put data into the swap file on the disk and low on disk space.

Have tried to look at system monitor before/during the systems running slow?

---

### Post by samcan on 2013-11-29
The laptop is about 3-4 years old, and I've had it since it was brand new. The Ubuntu 13.10 install is an upgrade from 12.10 and 13.04, and I think 12.10 had been a clean install. I did a clean install of Windows 7 also within the last year to year-and-a-half.

My hard drive layout is as follows (from cfdisk):

Free space 1.05MB
sda1 Primary ntfs 434,169.18MB (433GB)
Free space 1.06MB
sda2 Primary swap 2,147.49MB (2GB)
sda5 Logical ext4 50,282.37MB (49GB)
Free space 13,506.74MB (13.5GB)

Of my partitions, sda5 (my Ubuntu install) has 7.3GB free space, and sda1 (my Windows install) has 252GB free space. Again, when I startup both Windows and Ubuntu, the RAM isn't full. With Ubuntu, I'm not sure that it even goes into swap upon startup.

---

### Post by Yellow Pasque on 2013-11-30
Since it happens in two different OS's. I would start looking at hardware. It doesn't sound symptomatic of CPU or memory, so I would focus in disk-related items. Make sure your BIOS is updated, and if you have another disk drive to try, it might help.

---

### Post by andyfied on 2013-11-30
I would suspect the HD, Seagates tend to have overheating problems. Which model is it? The SMART data on my external drive has warned me that it will fail for the past 6 months (I just use it for transporting stuff I have other copies of elsewhere) but it is still going at full speed.

SMART data will give you a good idea of what is going on but is not 100% guaranteed. The fact that it says it is having heating problems means it could be to blame, but it could limp along working fine and slow for a long time to come. Or it might die without warning.

---

