---
title: "Um... this looks bad."
date: 2008-07-05
forum: Hardware
---

### Post by damis648 on 2008-07-05
Output of:
```
sudo smartctl -a /dev/sda
```
Here:
```
=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM250JI
Serial Number:    S0TVJD0PA84968
Firmware Version: HS100-08
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sat Jul  5 21:02:25 2008 EDT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32)	The self-test routine was interrupted
					by the host with a hard or soft reset.
Total time to complete Offline 
data collection: 		 ( 107) seconds.
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
recommended polling time: 	 ( 107) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       25
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2812
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2675
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       634
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       730
191 G-Sense_Error_Rate      0x0032   099   099   000    Old_age   Always       -       18508
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       125
194 Temperature_Celsius     0x0022   130   094   000    Old_age   Always       -       36 (Lifetime Min/Max 15/48)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       10682
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       966
225 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       41544

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
Now I know the HM250JI is not a great drive, I only found that out after I bought it... but this looks BAD. Can anyone help? Something is wierd though... 41544 as the Load_Cycle_Count doesn't really make sense... does it? Can anybody help? Or should I just buy a new hard drive? (I can do that, it is really not an issue on that part; i would just have to reinstall...). Any ideas?

---

### Post by damis648 on 2008-07-05
I seem to be having the same issue as the poster of post #361 on this page:
[http://ubuntuforums.org/showthread.php?t=591503&page=37](http://ubuntuforums.org/showthread.php?t=591503&page=37)

---

### Post by linfidel on 2008-07-05
What looks so bad? I don't claim to know very much about those figures, but I'm wondering why you think it's so bad; have you been having any problems?

Also, did you try running with the -F option.  Since it's only for Samsung, it may be important, especially since it warned you that you may need it.  Perhaps the figures are not meaningful without that option.

---

### Post by damis648 on 2008-07-05
I have tried that... the figures stay the same. I do not claim to knoiw much about this either, but I am really focused on that load count.

---

### Post by damis648 on 2008-07-05
No ideas? I was just looking... I would like a fast system with significant improvement in either both speed and storage, or just speed for a new hard drive **if this thing doesn't work out**. I was looking at these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136280](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136280)
and
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822116084](http://www.newegg.com/Product/Product.aspx?Item=N82E16822116084)
Which would anybody recommend?

---

### Post by starcannon on 2008-07-05
One of those is a SaS hdd and the other is a SaTa, I've never run SaS so I have no knowledge of how they work or what interfaces they use, but if you have the hardware to support it, and your willing to spend $250, then the 10k rpm drive seems an excellent choice. If however your computer is only capable of sata, then the WD is a good solid contender; I've used alot of WD hdd's and never had a failure yet (knocks on wood). Indeed I have always upgraded before I've worn one out, I still have an old 4gb WD cavier here somewhere that I bought over 10 years ago, it refuses to die.

---

### Post by linfidel on 2008-07-05
> **damis648 said:**
> I have tried that... the figures stay the same. I do not claim to knoiw much about this either, but I am really focused on that load count.From what I read, Hard disk manufacturers claim about 600,000 for that figure, so it seems like you're a long way from that.

I read a fairly interesting article here: [http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/](http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/)

---

### Post by damis648 on 2008-07-06
> **linfidel said:**
> From what I read, Hard disk manufacturers claim about 600,000 for that figure, so it seems like you're a long way from that.

I read a fairly interesting article here: [http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/](http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/)

Ahh... I thought it was 600, not 600,000. Well I seem to be Okay then, at least for a while.

---

### Post by damis648 on 2008-07-06
> **starcannon said:**
> One of those is a SaS hdd and the other is a SaTa, I've never run SaS so I have no knowledge of how they work or what interfaces they use, but if you have the hardware to support it, and your willing to spend $250, then the 10k rpm drive seems an excellent choice. If however your computer is only capable of sata, then the WD is a good solid contender; I've used alot of WD hdd's and never had a failure yet (knocks on wood). Indeed I have always upgraded before I've worn one out, I still have an old 4gb WD cavier here somewhere that I bought over 10 years ago, it refuses to die.

Well see that is what I was curious about... is SaS backward compatible with SATA... I seem to remember hearing that, but I was not completely sure. Can anybody shed some light on this?

---

### Post by linfidel on 2008-07-07
> **damis648 said:**
> Well see that is what I was curious about... is SaS backward compatible with SATA... I seem to remember hearing that, but I was not completely sure. Can anybody shed some light on this?Well, according to wikipedia, which, as we all know, is infallible, it says:
"At present it is slightly slower than the final parallel SCSI implementation, but in 2009 it will double its present speed to 6 Gbit/s, allowing for much higher speed data transfers than previously available, and is "downwards"-compatible with second generation[COLOR=DarkSlateGray] [/COLOR][COLOR=DarkSlateGray]_[SATA]("http://en.wikipedia.org/wiki/Serial_ATA")_[/COLOR] drives. SATA 3.0Gbps drives may be connected to SAS backplanes, but SAS drives may not be connected to SATA backplanes."

Other than that, I don't know anything about them.

---

### Post by Bucky Ball on 2008-07-09
Yes, it is 600,000 (all depending on the drive and accuracy of the manufacturer's info). 

You may find the page below interesting though because it is a problem with a lot of **laptop** hard drives, not desktop ... more a matter of comparing it over time rather than once. Check it now and check it in 24 hours, then in 24 hours and if you are racking up a zillion cycles a day, then you got trouble. Get an average and figure it from there. You could say this; when was the drive brand new? If you have a date, calculate the Load_Cycle_Count with the weeks or days from then til now, then panic or not! lol

Check out the first section here, 'Ubuntu Eats Your Hard Disk':

[http://ubuntuforums.org/showthread.php?t=781966&highlight=load_cycle_count](http://ubuntuforums.org/showthread.php?t=781966&highlight=load_cycle_count)

Cheers

---

