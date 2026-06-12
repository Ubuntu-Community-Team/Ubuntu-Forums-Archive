---
title: "Are my hard drives dying?"
date: 2009-11-17
forum: Hardware
---

### Post by AaronBuntu on 2009-11-17
Recently updated to 9.10, and had troubles during the install and getting the new kernel to be used and in the process I had a look at my logs - and saw these worrying messages

```

[72079.522144] sd 9:0:1:0: [sdd] Sense Key : Recovered Error [current] [descriptor]
[72079.522151] Descriptor sense data with sense descriptors (in hex):
[72079.522153]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
[72079.522160]         00 00 00 00 40 50 
[72079.522164] sd 9:0:1:0: [sdd] Add. Sense: ATA pass through information available

[72079.757969] sd 9:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[72079.757976] Descriptor sense data with sense descriptors (in hex):
[72079.757978]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[72079.757986]         00 00 00 00 00 00 
[72079.757989] sd 9:0:0:0: [sdc] Add. Sense: ATA pass through information available
[72079.908080] sd 9:0:0:0: [sdc] Sense Key : Recovered Error [current] [descriptor]
[72079.908089] Descriptor sense data with sense descriptors (in hex):
[72079.908090]         72 01 00 1d 00 00 00 0e 09 0c 00 00 01 00 00 00 
[72079.908098]         00 4f 00 c2 00 50 
[72079.908102] sd 9:0:0:0: [sdc] Add. Sense: ATA pass through information available

```I have 2 SATA HDDs installed - sdc for / and sdd for /home - both under a year old, so I would be surprised if they are dying already! Googled a bit, and saw to run SMART tools to see if there are any errors going on there, but dont really know how to interpret the results

```
 sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K1000
Device Model:     Hitachi HDS721010KLA330
Serial Number:    GTE002PAKSWSVE
Firmware Version: GKAOA97A
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Tue Nov 17 16:55:28 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (15354) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   130   130   054    Old_age   Offline      -       150
  3 Spin_Up_Time            0x0007   127   127   024    Pre-fail  Always       -       581 (Average 516)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       29
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   134   134   020    Old_age   Offline      -       32
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       9320
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       49
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       49
194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Lifetime Min/Max 22/41)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%         5         -
# 2  Short offline       Completed without error       00%         1         -
# 3  Short captive       Completed without error       00%         0         -

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

``````

sudo smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST31500341AS
Serial Number:    9VS11G3K
Firmware Version: CC1H
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Nov 17 16:55:32 2009 EST
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
data collection:          ( 609) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       198152988
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       8
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       3
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       17822657
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2448
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       8
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   069   069   000    Old_age   Always       -       31
190 Airflow_Temperature_Cel 0x0022   066   064   045    Old_age   Always       -       34 (Lifetime Min/Max 34/36)
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   055   032   000    Old_age   Always       -       198152988
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       215396904864144
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       4014703102
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       4115987969

SMART Error Log Version: 1
No Errors Logged

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


```Both HDDs test the overall health checks, so whats going on? I just checked and these "sense data" messages only started appearing yesterday, which is when I got the new kernel to boot (Im pretty sure) - I think the smartctl says my hdds are fine.

What should I look at next? 

Thanks, 
Aaron

---

### Post by AaronBuntu on 2009-11-18
No ideas anyone?

---

### Post by openuniverse on 2009-11-18
.

---

### Post by zsitvaij on 2009-11-18
Dying? Doubtful. I have an external usb hard drive that displays the same messages in the system log, but works fine on Jaunty. It also works fine on any other distro I've used, mainly Gentoo. I'm not sure if it actually impacts usage in Karmic.

I'm looking into what it would take to file a meaningful bug report, but as I can still just reboot to a working distro, it's not the highest on my list of priorities.

---

### Post by scheidtm on 2009-11-26
For me this is a kernel thing:

With 2.6.31-15-generic, I get similar error message before the system hangs (reproducibly) when storing large amounts of data on an external USB drive.

With 2.6.28-16-generic, this does not happen and I am able to store large amounts on the same USB drive.

YMMV,

Jens

---

### Post by DigitaLink on 2009-11-29
I'm also having issues with my USB hard drive (SATA drive via USB) on 2.6.31-15 on an Aspire One netbook.  (Ubuntu Netbook Remix)

Considering pretty much ALL of my files are on this drive, not being able to get to them without massive wait times or outright failures is very frustrating.

What's the easiest way to roll back to an older kernel?  Or would that cause more grief than it's worth?  I really don't want to have to wipe Ubuntu and put XP back on it.
------------------------------
Update: after trying a bunch of things, I've managed to get a bit better transfer speeds, but it still halts for almost exactly 40 seconds in between 'bursts' of file transfers.  Still very frustrating.

---

### Post by zsitvaij on 2009-11-30
We're having different issues, I think. My external drive still works reliably even under load, and copying and checksumming some 70GB of data revealed no problems.

In my case, the log messages are triggered by libatasmart automatically checking the SMART status every x minutes. It also spams the log during manually initiated scans, but does not impact transfer speeds or stability at all.

---

### Post by nutznboltz on 2010-04-01
See 

[https://bugzilla.kernel.org/show_bug.cgi?id=13594](https://bugzilla.kernel.org/show_bug.cgi?id=13594)

---

### Post by DigitaLink on 2010-04-01
Yep, turns out my issue was a weak power supply for the drive.  Plugged the drive into the power supply from a tower and it worked just great.  Took way too long to figure that out though.  And far too much frustration.

---

### Post by nutznboltz on 2010-05-10
See also
[http://hardforum.com/showthread.php?p=1035475999](http://hardforum.com/showthread.php?p=1035475999)

---

### Post by nutznboltz on 2010-05-10
``mptsas hangs caused by ATA pass-through explained''
[http://lkml.org/lkml/2010/4/26/335](http://lkml.org/lkml/2010/4/26/335)

same:
[http://kerneltrap.org/mailarchive/linux-scsi/2010/4/26/6884716](http://kerneltrap.org/mailarchive/linux-scsi/2010/4/26/6884716)

---

