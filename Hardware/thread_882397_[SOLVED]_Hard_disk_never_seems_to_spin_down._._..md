---
title: "[SOLVED] Hard disk never seems to spin down. . ."
date: 2008-08-06
forum: Hardware
---

### Post by pi.boy.travis on 2008-08-06
Hi.  I have a Dell Inspiron 1520 and the hard disk never seems to spin down.  Even if I leave it on for hours it is still buzzing away.  Should I be concerned, or am I just paranoid?

---

### Post by Yuki_Nagato on 2008-08-06
_[http://ubuntuforums.org/showthread.php?t=795327]("http://ubuntuforums.org/showthread.php?t=795327")_

Run this test to see if your machine is killing its hard drive.

If your cycles fall into a normal range, we can check running processes with 

```
top
```

If nothing is consuming large amounts of memory and the hard drive is still sawing away, then we need to get worried.

---

### Post by pi.boy.travis on 2008-08-06
Here is the output of the test described in the thread you liked me to:

```
travis@travis-laptop:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Wed Aug  6 23:18:09 EDT 2008
194 Temperature_Celsius     0x0022   124   094   000    Old_age   Always       -       38 (Lifetime Min/Max 10/48)
```

I have little experience in this area. . . I can't make sense of any of this. . . But I do hope that my hdd temp isn't 194C !

EDIT: My two external HDDs do spin down properly.

---

### Post by darco on 2008-08-06
> **pi.boy.travis said:**
> Here is the output of the test described in the thread you liked me to:

```
travis@travis-laptop:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Wed Aug  6 23:18:09 EDT 2008
194 Temperature_Celsius     0x0022   124   094   000    Old_age   Always       -       38 (Lifetime Min/Max 10/48)
```

I have little experience in this area. . . I can't make sense of any of this. . . But I do hope that my hdd temp isn't 194C !

EDIT: My two external HDDs do spin down properly.

Thats 381 degrees Farenheit!!!!......Does it feel a little WARM!!!!!

The thread above is what you need to follow, I did it for my Toshiba, its very easy to do,dont delay

good luck
darco

---

### Post by pi.boy.travis on 2008-08-06
It doesn't get really hot, it just doesn't spin down. . .

Should I be worried?

---

### Post by pi.boy.travis on 2008-08-07
OK, my drive doesn't spin down in Vista either. . .  I am begining to think that this may be a hardware issue.

---

### Post by darco on 2008-08-07
Why dont you run the steps in the thread above...you have nothing to lose

darco

---

### Post by pi.boy.travis on 2008-08-07
I don't even know which number is my load cycle count. :confused:  I'm pathetic, I know. . . :lolflag:

---

### Post by Yuki_Nagato on 2008-08-07
Ok.  What is going on (you have to read the directions carefully) is that we take a "snapshot" of the current number of hard drive cycles.  We then wait, recording the time that has passed, and do it again.  We need to know how many cycles went down while we were waiting.

So run the command, 

wait fifteen minutes,

run the command again.

Subtract the 2nd's data from the 1st's.  Then compare to the data on the thread mentioned.

---

### Post by pi.boy.travis on 2008-08-08
I must be doing something wrong.  If I copy and paste the command directly, I only get drive temperature. (which is normal)  It skips the load cycle line. . . ARRGH!

Thanks for the clarification though Yuki_Nagato.

---

### Post by pi.boy.travis on 2008-08-08
OK, so if I narrow it down to the part I'm looking for:

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

I get no output at all.  My internal disk is /dev/sda.  I'm officially stumped. . .

---

### Post by kevmitch on 2008-08-08
The load cycle count issue is the OPPOSITE of your problem. There was a big uproar about a year ago about hard disks that were spinning down too often. Since hard disks have a limited number of times that they can do this before failure, it caused a lot of people to worry. 

The smartctl command checks the status of various indicators on your disk of which the number of times the disk has spun down is one of them. The fact that you don't have this value is suggesting that either the smartctl command isn't working correctly, or your disk doesn't have that capabitlty

I guess the first question is whether /dev/sda is actually your hard disk. 

what does 

```
sudo fdisk -l
```

give you

That should give you a list of your disks and tell you what device they are. It might be that your disk is /dev/hda or something like that.
Then run

```
sudo smartctl -a <your device>
```

That will give you the full output (including the header to the columns) and LOAD_CYCLE_COUNT should probably be in there. 


Finally, you can try manually spinning down your disk by issuing the command

```
sudo hdparm -y <your device>
```

You should find that your load cycle count increases by one each time you run that command.

---

### Post by kevmitch on 2008-08-08
Oh, and I should add that in the output to smartctl, your looking for the "Raw Value" column, which is the last one. So your temperature Celsius is 38, not 194. 194 is the id of the temperature Celsius attribute. load cycle count is 193.

---

### Post by jpkotta on 2008-08-08
OP said HD is NOT spinning down.  If this is the problem, you can use hdparm's -B and -S options.  You can also see what programs are causing the disk to spinup with /proc/sys/vm/block_dump (hint: kswapd, pdflush, and kjournald will always be running and are quite necessary).

See also: [www.lesswatts.org](www.lesswatts.org)

---

### Post by pi.boy.travis on 2008-08-08
OK, here are the outputs:

```
travis@travis-laptop:~$ sudo fdisk -l
[sudo] password for travis: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5505    44217344    7  HPFS/NTFS
/dev/sda2            5506       38913   268349760    5  Extended
/dev/sda5            5506       38159   262293223+  83  Linux
/dev/sda6           38160       38913     6056473+  82  Linux swap / Solaris

Disk /dev/sdb: 5475 MB, 5475778560 bytes
255 heads, 63 sectors/track, 665 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ace8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         665     5341581    b  W95 FAT32

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x528f7427

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36482   293035008    7  HPFS/NTFS

Disk /dev/sdd: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x492ae1eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2431    19526976    c  W95 FAT32 (LBA)
travis@travis-laptop:~$ 


```

/dev/sda is my internal drive.  255 heads?!?!?!  

```
travis@travis-laptop:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM320JI
Serial Number:    S19FJD0PB32498
Firmware Version: 2SS00_01
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Fri Aug  8 22:44:02 2008 EDT

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
data collection: 		 ( 120) seconds.
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
recommended polling time: 	 ( 120) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       106
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2625
  4 Start_Stop_Count        0x0032   075   075   000    Old_age   Always       -       256390
  5 Reallocated_Sector_Ct   0x0033   097   097   010    Pre-fail  Always       -       32
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2005
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1389
191 G-Sense_Error_Rate      0x0032   002   002   000    Old_age   Always       -       999999
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       243
194 Temperature_Celsius     0x0022   127   094   000    Old_age   Always       -       37 (Lifetime Min/Max 10/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       81322
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2700
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       6236
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       00%       348         327764648
# 2  Short offline       Aborted by host               150%        62         -
# 3  Short offline       Completed without error       00%         2         -
# 4  Short offline       Completed without error       00%         0         -

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

As you can see, the field I am looking for is missing. . . :(


I am thinking that perhaps this is a hardware issue, as this occurs not only in Ubuntu, but Windows Vista, GRUB, Live CD's as well.  I don't really care that my disk never spins down, as I'm not too concerned with saving power, and I rarely operate on battery.  What I don't want to do is wear out my disk.  I have had this machine for about seven months now, and nothing has failed my yet.  I have never had a drive fail on me, and I don't want to lose this one.

sudo hdparm -y /dev/sda  didn't seem to stop my disk for even a fraction of a second.

Last but not least, /proc/sys/vm/block_dump  is an empty file. . . 

Thanks to everyone who posted!

I am probably just being paranoid, as everything else seems to be normal.  I'm not the type to worry about problems I haven't confirmed, but when I read that post about hard disks wearing out after six months, I started to worry, as my laptop is on the list.

---

### Post by jpkotta on 2008-08-09
When you say "never spins down" and "buzzing away" do you mean it's constantly being accessed, or just always spinning?  Is the LED always lit?  

It is absolutely not a big deal if it's just spinning all the time.  What's hard on hard drives is spinning up and spinning down.  If they always stay in the same state, there is less wear.  

In my experience, the default behavior of a drive is to always spin unless told to spin down.

If the drive is constantly being accessed, that's not too big of a deal either, but I would want to know why.  Constant seeking may reduce the lifetime of the drive.

---

### Post by pi.boy.travis on 2008-08-09
> **jpkotta said:**
> When you say "never spins down" and "buzzing away" do you mean it's constantly being accessed, or just always spinning?  Is the LED always lit?  

It is absolutely not a big deal if it's just spinning all the time.  What's hard on hard drives is spinning up and spinning down.  If they always stay in the same state, there is less wear.  

In my experience, the default behavior of a drive is to always spin unless told to spin down.

If the drive is constantly being accessed, that's not too big of a deal either, but I would want to know why.  Constant seeking may reduce the lifetime of the drive.

Thanks!  The drive isn't being accessed, and the LED stays off, the platter just never stops.  I know next to nothing about hard disks, and I don't want to wear mine out. . .

---

### Post by Dane1217 on 2008-09-16
I am new here so not sure how to start a new post, but thought other people might see this on the thread.  I am new to Linux but my brother has been using it for a long time.  Recently the hard drive on the laptop would not stop spinning.  Went through some fixes that I found but did not cure problem.  Finally figured out that it wasn't a power management problem.  I had installed mythtv and then unistalled using the add/remove function. However this didn't remove everything.  finally found a link and ran in terminal

sudo apt-get remove myth*   

saw it removing a lot of files and the problem was resolved.  Apparently the mythtv server kept trying to log in users.

---

