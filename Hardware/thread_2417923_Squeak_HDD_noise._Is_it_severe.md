---
title: "Squeak HDD noise. Is it severe?"
date: 2019-04-29
forum: Hardware
---

### Post by gipsyshadow on 2019-04-29
On Nov 2018 I've got a 1TB western digital black 3.5" @7200 HDD (WD1003FZEX-00K3CA0) directly from WD official web site and it worked within my desktop PC lightly for about 600 hours until now.
[This]("https://drive.google.com/file/d/1wRQl8fooeMv8vErf4WroWP7Y4p1qz5zl") is the weird noise I'm talking about. I herd it about a month ago for the 1st time and it occurs both ander windows and ubuntu and not regularly so I spent a lot of time to record it. Some days I don't hear it at all while other days it occurs every about 2 hours but consider I can hear it mainly at evening and night because at daytime there's a lot of noise around me (road traffic, etc.).

I've already run both tests under win with official WinDlg WD utility, I mean quick and extended, and they're "pass", moreover &#65279;CrystalDiskInfo says "good". I've red some wd stuff about hdd noises like [this one]("https://support-it.wd.com/app/answers/detail/a_id/17304") and I've also tried to use the other MB's sata cable but this weird noise goes on.
I run
```

smartctl --all /dev/sda
```
in an ubuntu 18.04.2lts recovery mode session and that was the output
```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-17-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Black
Device Model:     WDC WD1003FZEX-00K3CA0
Serial Number:    WD-************
LU WWN Device Id: ******************
Firmware Version: 01.01A01
User Capacity:    1.000.204.886.016 bytes [1,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 3b
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Apr 29 15:07:34 2019 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (11040) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 114) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   171   168   021    Pre-fail  Always       -       2433
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       328
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       650
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       326
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       51
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       433
194 Temperature_Celsius     0x0022   118   105   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       581         -
# 2  Conveyance offline  Completed without error       00%         3         -

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
I guess it's ok. Definitely it'd seem to be all good with the these sw anyway I've started to backup all my new data as usually.

I'd like to know if you've ever herd it and if it can suggest a trouble, I mean right now or in the long period as well.
If yes I'll ask wd a substitution and If you're already experienced with WD assistance & guarantee conditions I'd want to know if it's possible wd won't accept this noise as a condition of defect and won't give me a brand new hdd. I guess they could answer it was my fault due to ESD caused by myself during installation, couldn't they?

Thanks in advance for help and suggestions :)

---

### Post by Autodave on 2019-04-29
The only thing you could have done to make a squeaking noise would be to drop it or whack it against something.  Are you sure it is the HD making the noise and not a cooling fan?  Are you sure that the noise isn't coming from your speakers?  Generally, when a HD makes a noise like that, its life expectancy can be best guessed in seconds, not hours or days.  If it were my HD making the noise, I would be getting a replacement or my money back.

---

### Post by gipsyshadow on 2019-04-29
Neither drops or whacks, not by me of course, I mean I don't know if the courier dropped/whacked the package before I got it, it's impossible to know and this noise didn't exist at the beginning of hdd working life. I supposed an ESD caused this squeak because it was winter and I dressed lots of wool clothes when I built this pc, I paid attention to ESDs but I can't be so sure something went wrong or not.

I've no speakers but there're 3 stock fans in this case anyway I put a small microphone just below the hdd to record this squeak, I mean within the cage. I started to hear a "tak" sound only from some days ago, I can't say if this tak was present before and I didn't note it anyway I can't be sure this tak comes from the hdd too or somewhere else, I just remember a couple of time I herd tak+squeak one after the other one in this sequence (last time was just fews seconds ago!).
I'm very newbie and I'm not experienced with hdd anyway if this can be a hint of a danger I'll open a RMA, I just hope WD'll understand what's wrong with this hdd mechanically because it looks perfect by sw tests. I guess it's related to heads and I listened to many hdd noises recorded in youtube but none is my squeak.

---

### Post by him610 on 2019-04-29
It could be a fan. I have one system that sometimes wakes up screeching like a banshee then a couple of minutes later it quietens down.

---

### Post by Autodave on 2019-04-30
Computer case fans tend to be rather cheap: have replaced many over the years.  Power supply fans, too.

---

### Post by gipsyshadow on 2019-05-01
Last night I unplugged the 3 fans and the noises occurred again. I listened to the new audio file and checked the "tak" noise and I realized it's just the 1st part of the already posted squeak noise. It means that now the noise can occur both in the "complete" (already posted) version and in the only-tak version.

I've emailed WD just to ask informations, I mean not RMA. I could attach a file so I uploaded the squeak mp3 file and asked to let their technicians to hear it. They replied the noise was normal and they told me to use "Data Lifeguard Diagnostics" to test the drive and, in the case the tests failed, I could open a RMA. Finally they wrote I'd pay shipping cost for a RMA and, in the case of a replacing, they'll give me a refurbished hdd.

what can you suggest me to do after the WD reply? What do you think it's the best thing to do (or the least worst)?

---

### Post by him610 on 2019-05-01
1) As suggested, test the drive with Data Lifeguard Diagnostics - I suppose it is their diagnostics program.
2) If test indicates Fail, request RMA. 
2a) If test indicates Pass, accept disk as is. No further action needed.
or 
Consider disk a loss. 
Replace with new SSD.

---

### Post by TheFu on 2019-05-01
When any HDD is making noises, it is time to 
a) backup everything you don't want to lose, version those backups every day, until ... 
b) get a replacement storage device - RMA if possible, replace regardless.

Perhaps the credit card used for the purchase has features replace broken stuff within 90days for any reason or will double the manufacturer's warranty. I dropped a WD HDD a few years ago 2 days after purchase. Contacted the credit card, told them the truth, they credited the account a few days later.

Whether you want/need an SSD is a different question.  SSDs are a completely new deal and some knowledge is necessary so we don't make a bad choice. Not all SSDs are anywhere near the same.  Don't get burned with a cheap SSD with low endurance numbers.  There is nothing wrong with buying spinning rust still. Picked up a $9.95 250G refurb at MC last fall after destroying a few flash drives and a few SSDs by using them for video recording.  Pick the right storage for the right job, within budget constraints.  For video/music storage and playback, there is NO REASON at all to get an SSD.

---

### Post by gipsyshadow on 2019-05-01
already tested by Data Lifeguard Diagnostics: consider "WinDlg WD utility" i wrote @ my 1st post is "windows data..." :) i just didn't tell wd i had already done that.
what i didn't understand about wd reply is how to consider what they said, i mean "if the test says the hdd fails then you can rma it" (it's my own best translation). can we deduce that 1) "if the test says the hdd is good you can't rma it else we'll give it back to you" or 2) "if the test says the hdd fails it's broken for sure but there're some broken hdd not recognized only by test" in other words 2b) "the test gives a condition not necessary but only sufficient"?
i don't know if it's the best solution but my idea is to rma it and if they say hdd is good i'll keep it. i'll waste my money for shipping and possibly there will be issues due to the journey (drops, etc) these are the drawbacks.

---

### Post by him610 on 2019-05-01
@TheFu, always gives good advice.

If it passes your diagnostics testing, and you still RMA it. It arrives in their facility. First thing they will do is run the same diagnostics test; however, they may have a more comprehensive set of tests. If it passes their test, they will probably box it up to be sent back to you which means you will be out dollar$ for shipping both ways and no better off than you are now.

You could wait until it fails then RMA it. Nobody wants to use flaky equipment though. Perform backups frequently.

I have not had a disk failure in years, but normally when I hear the tak-tak sound I go ahead and replace the disk. It's a bummer when you recently bought the disk. Refer to post #8, second paragraph by TheFu.

---

### Post by dino99 on 2019-05-02
Do you get something usefull logged (glance at journalctl) ?
Some times ago , with a sata hdd, it became noisy; the tests was ok too; and finally i came to uninstall hdparm; No problem at all since that removal, and no more noise.
But it can be hardware related (fan/watercooler) or due to inapropriate power settings (bios/uefi)

---

