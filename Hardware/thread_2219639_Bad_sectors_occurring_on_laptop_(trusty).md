---
title: "Bad sectors occurring on laptop (trusty)"
date: 2014-04-24
forum: Hardware
---

### Post by Scoobin on 2014-04-24
I've been running 12.04 on my HP laptop since it came out, but I've noticed since running the beta and now the final release of 14.04 (fresh install) I continually get bad sectors on my hard disk, but not a single one occurs while using 12.04. The major difference between the 2 is on 12.04 I use Catalyst AMD graphics and on 14.04 I am forced to use open source drivers (the x-version is newer than legacy Catalyst AMD graphics will support - HD2600). The system does seem to run a bit hotter overall but the harddisk can get to 40 Celcius even on 12.04 (I've seen it at 43 on 14.04 with open source). So I'm not 100% sure that heat is the cause.

Does anyone have any ideas?

---

### Post by bcschmerker on 2014-04-25
What make and model hard drive?  40°C is hot for consumer-grade hard drives; a 60°C-safe drive of the same capacity and size format will better serve you, especially in the face of a hot-running GPU on a portable.

I'm planning hardware improvements to both an Asus® CM1630-06 as upgraded and a LinUX box scheduled for a rebuild when equipment is afforded.  On the CM1630, I found that the stock 1 TB Seagate® ST31000528AS (packing a re-install of Microsoft® Windows® 7.0.8001) was intended for an air-conditioned office rather than the heat of a Central Valley summer, given a 40°C operating temperature limit.  Western Digital® has upgrade candidates of the same capacity in the WD10EFRX Caviar® Red&#8482; (3.5" form factor) and WD10JFCX Scorpio® Red&#8482; (2.5" form factor), both of which are safe to 60°C operating.  The LinUX box is slated for multiple hard drives, each packing a unique set of partitions for maximizing performance of the entire LinUX installation, so the 750GB Western Digital® WD7500BFCX Scorpio® Red&#8482;, also safe to 60°C operating, is my first choice for each drive in a stack of up to four.

---

### Post by sudodus on 2014-04-25
Time (due to wear) is also a factor. What is the ***S.M.A.R.T.*** status of the disk? You can install

```
sudo apt-get install smartmontools
```

and run

```

sudo smartctl -H /dev/sdx
sudo smartctl -a /dev/sdx

```

where x is the drive letter.

See ```
man smartctl
``` for details

You can run ```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number. This command line finds and marks bad blocks.

If you have an increasing number of bad blocks, the drive is failing, and you should back up its content before it is too late. ***ddrescue*** is a good tool and reading the info page is a way to start using it.

```
info ddrescue
```

But if there is still a difference: No bad sectors with 12.04 (when running now) and frequent bad sectors with 14.04, I suggest that you keep using 12.04. Ubuntu 12.04 LTS is supported until April 2017 (and for example Xubuntu 12.04 LTS is supported until April 2015). Wait and let 14.04 LTS be debugged for several months before trying it again, for example until August and the first point release 14.04.1. If you think the issue depends on the graphics and excessive heat and there is no improved graphics driver, stay with 12.04 LTS as long as it is supported.

---

### Post by Scoobin on 2014-04-25
> **bcschmerker said:**
> What make and model hard drive? 40°C is hot for consumer-grade hard drives; a 60°C-safe drive of the same capacity and size format will better serve you, especially in the face of a hot-running GPU on a portable.
Gnome Disk Utility reports it as ATA ST9250827AS so I guess it's a Seagate. Capacity is 250gb. I've read Seagate are the least reliable but that's what the system came with.

> **sudodus said:**
> Time (due to wear) is also a factor. What is the S.M.A.R.T. status of the disk? You can install
OK Let's see...

```
sudo smartctl -H /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-60-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

```
sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-60-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.4
Device Model:     ST9250827AS
Serial Number:    5RG6BE70
LU WWN Device Id: 5 000c50 011b21015
Firmware Version: 3.AHC
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Apr 25 20:53:50 2014 NZST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  426) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  93) minutes.
SCT capabilities:            (0x0035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   099   099   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   093   093   020    Pre-fail  Always       -       7452
  5 Reallocated_Sector_Ct   0x0033   056   056   036    Pre-fail  Always       -       1760
  7 Seek_Error_Rate         0x000f   086   060   030    Pre-fail  Always       -       4720116643
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       11931
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   095   095   020    Pre-fail  Always       -       5690
184 End-to-End_Error        0x0033   099   099   097    Pre-fail  Always       -       1
187 Reported_Uncorrect      0x003a   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   001   000    Old_age   Always       -       66308
189 High_Fly_Writes         0x0032   092   092   000    Old_age   Always       -       8
190 Airflow_Temperature_Cel 0x0032   071   047   040    Old_age   Always       -       29 (Min/Max 10/53)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       103
192 Power-Off_Retract_Count 0x003a   100   100   000    Old_age   Always       -       1904
193 Load_Cycle_Count        0x0012   025   025   000    Old_age   Always       -       151646
194 Temperature_Celsius     0x003a   029   053   000    Old_age   Always       -       29 (0 10 0 0)
195 Hardware_ECC_Recovered  0x003e   072   056   000    Old_age   Always       -       17721371
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     11716         -
# 2  Short offline       Completed without error       00%     11689         -
# 3  Short offline       Completed without error       00%     11688         -
# 4  Short offline       Completed without error       00%     11686         -
# 5  Short offline       Completed without error       00%      4284         -

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

Not sure what was happening here...
```
sudo e2fsck -cf /dev/sda
e2fsck 1.42 (29-Nov-2011)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```

> **sudodus said:**
> But if there is still a difference: No bad sectors with 12.04 (when running now) and frequent bad sectors with 14.04, I suggest that you keep using 12.04. Ubuntu 12.04 LTS is supported until April 2017 (and for example Xubuntu 12.04 LTS is supported until April 2015). Wait and let 14.04 LTS be debugged for several months before trying it again, for example until August and the first point release 14.04.1. If you think the issue depends on the graphics and excessive heat and there is no improved graphics driver, stay with 12.04 LTS as long as it is supported.
Yeah that has been my reasoning too. Stick with 12.04 for now. I'm planning on testing Elementary for performance out of curiosity. 

Good idea about waiting until 14.04.1. Is it worth logging this as a bug on Launchpad?

---

### Post by nedrerairo on 2014-04-25
well the smart capability is actually logged on the hard drive, not the os itself..  so readouts should not vary from distribution to distribution.

I would be worried about readout nr. 5 and nr. 7 .. while not high on #5 yet, it might be a prelude to increasing problems ..  and seek error rates should be close to zip/zero

also g-sense error rate is high, been dropped? mine is at 14 on one drive and 0 on the other..

---

### Post by Scoobin on 2014-04-25
I realise it is done on the drive but something on the 14.04 install is causing bad sectors which doesn't happen on 12.04. Oh, I think I see what you mean. My comment about Elementary was a bit of a side-comment to simply say I'm considering running it, but I realise it will give me the same SMART data as Ubuntu.

You're right about the reallocated sector count being of concern (if that's what you meant by readout nr 5). Just a couple months ago there were no bad sectors. Even using 14.04 for a day recently I got 100 or 200 new reallocated sectors. 

I don't know what G-sense is but I've not dropped the system in the time I've had it (bought second hand 2.5 years ago).

---

### Post by nedrerairo on 2014-04-25
g-sense error rate is, as far as I can see a read on g-force strain on the drive while "online", as in senses if it has been moved during spinning disks with excess force (up or down rapidly, with or without abrupt stop) .. might also be nothing, but I've had laptop drives with high g-sense and abysmal performance..

yes by nr 5 I mean the sector count part, reallocation is just another way to say ok - this sector is bad, so let's just point this bit of the drive to a healthy part so it doesn't corrupt data any further ..

might be coincidental with swap of distribution, or it might be that parts of the drive that were yet to be written to are now in use with new data on the hdd being written from day to day , as you say..

I guess no harm done to go back to 12.04 if you feel safer, but I'd still check the smart readouts once every 2 weeks just to be sure :)   oh, and do regular backups :)

with regards to temperature, laptops will without a doubt have a higher use temperature than normal desktops due to restricted space for heat to dissipate  and/or cooling solution .. higher temperatures mean lower life expectancy and as a result will fail sooner than later.. I would check the specs for max/min temperature for your drive in question, but usually around 30' celcius is good.  40' shouldn't be too bad either.. but 50+ isn't ok

---

### Post by sudodus on 2014-04-25
> **Scoobin said:**
> 
Not sure what was happening here...
```
sudo e2fsck -cf /dev/sda
e2fsck 1.42 (29-Nov-2011)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```

Yeah that has been my reasoning too. Stick with 12.04 for now. I'm planning on testing Elementary for performance out of curiosity. 

Good idea about waiting until 14.04.1. Is it worth logging this as a bug on Launchpad?

I need not comment the SMART data more than what has been mentioned already.

I forgot to tell you that a partition must not be mounted, when treated with e2fsck. It is a good idea to boot from an Ubuntu install CD/DVD/USB drive (or another linux live drive), and check that the partition is not automounted (unmount if necessary). Then you will be allowed to run

```
sudo e2fsck -cf /dev/sda
```

---

### Post by Scoobin on 2014-04-27
Thanks for your help guys.

I tried the e2fsck command on a live usb stick of Elementary and got the same result. I tried the mount command and didn't notice any hard-disk mounted but I'm not 100% sure.

---

### Post by sudodus on 2014-04-27
Well, as long as you keep an eye on the S.M.A.R.T. status, I think you need worry about that e2fsck command.

---

