---
title: "Faltering hard disk access"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by PersistentLurker on 2007-05-12
**Edit:** The problem described here appears to be identical to [Bug #119730](https://bugs.launchpad.net/ubuntu/+bug/119730); this laptop does indeed have an SATA hard disk, and lately, Ubuntu seems to be struggling with SATA support. Thanks to colanderman for pointing this out to me.  I no longer have this laptop and I'm no longer using Ubuntu, so I have abandoned this issue. Best of luck to everyone with this problem.


If the thread title sounds bizarre, that's because the problem I'm facing is bizarre.

Often, when starting applications (especially large ones, e.g. OpenOffice), there is disk activity for a fraction of a second, a pause for nearly a second, another spike of disk activity, and on and on. It might sound like the CPU is the bottleneck here, but I suspect not: during the pauses, CPU usage often drops to near-zero and spikes up when disk activity spikes. When it remains high during the pauses, top(1) shows that the majority of that time (~90%) is "iowait" time.

The result is that some very important applications are so slow that they are unusable.


**The system:**

This is Xubuntu 7.04, installed yesterday via Wubi-7.04-minefield0.7 (which basically means that the Linux filesystem is in loopmounted files sitting in a Windows partition, eliminating the need for partitioning).

This is laptop (specifically, an Acer TravelMate 2300). It is very heavily used and regularly moved, so a hardware failure would not be surprising. 


**Patterns:**

I find that the system does not display this behavior when booting up. Usually, I first notice it toward the end of XFCE startup. All subsequent swapping and application startups seem to be affected by these intermittent pauses.

Just yesterday and earlier today, the system seemed to last longer before these pauses started wreaking havoc. It seems that, with each reboot, it lasts a little less time before I start getting this behavior (but that my just be my pessimistic perception).

On rare occasions (once a week at most) when under heavy load, Windows XP also displays this behavior on this laptop. I don't remember when I first noticed this; until now, I assumed it was an WinXP bug.


**My troubleshooting attempts:**

I know nil about hard disks and how Linux uses them, so I'm not sure how to troubleshoot this. Here's all I could think of:
[list][*]I checked dmesg for errors spewed during these pauses. I found none.
[*]I tried manipulating /sys/block/sda/queue/scheduler to try all of the different disk scheduler modes available. Changing modes had no effect.
[/list]

Attached are the results of the dmesg and lshw commands. Note that I had to split dmesg into two files due to these forums file size limits.


**My request:**

If anyone has any ideas as to how to troubleshoot this or can give any reading suggestions, I would be very grateful. This problem prevents me from using Xubuntu, which is a shame since it is the most impressive distro I have ever installed.

---

### Post by tgalati4 on 2007-05-13
Find a terminal:

sudo apt-get install smartmontools
sudo smartctl -s on /dev/hda
sudo smartctl -t short /dev/hda
sudo smartctl -l selftest /dev/hda
sudo smartctl -a /dev/hda

Post the output of the last two commands.

---

### Post by PersistentLurker on 2007-05-13
The hard disk is ATA, but apparently, Feisty treats everything as SCSI devices. This required two modifications to the commands you gave me:
[list][*]Replacing "/dev/hda" with "/dev/sda"
[*]Adding "-d ata" (mentioned in the manual page)[/list]

With those modifications, I ran the commands. Here are the results you suggested I post:

```
$ sudo smartctl -d ata -l selftest /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2725         -
# 2  Short offline       Completed without error       00%      2725         -

$ sudo smartctl -d ata -a /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     HTS424040M9AT00
Serial Number:    MPA241Q2CA4SLA
Firmware Version: MA2OA71A
User Capacity:    40,007,761,920 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a
Local Time is:    Sun May 13 07:47:46 2007 EDT
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
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  37) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   165   165   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   096   096   000    Old_age   Always       -       7872
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   094   094   000    Old_age   Always       -       2725
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       4008
191 G-Sense_Error_Rate      0x000a   095   095   000    Old_age   Always       -       524291
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       112
193 Load_Cycle_Count        0x0012   069   069   000    Old_age   Always       -       313833
194 Temperature_Celsius     0x0002   196   196   000    Old_age   Always       -       28 (Lifetime Min/Max 12/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2725         -
# 2  Short offline       Completed without error       00%      2725         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
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

No errors seem to jump out at me there.

Thanks for pointing me towards these tools. I'll check out its man page(s) and see if I find anything else to test.

---

### Post by PersistentLurker on 2007-05-13
I tried running "sudo smartctl -d ata -a /dev/sda" a second time after starting OpenOffice (which strongly triggered the behavior in question), hoping to notice some changes in the output. I only found these differences, which don't look significant to me:

```
<   3 Spin_Up_Time            0x0007   165   165   033    Pre-fail  Always       -       1
<   4 Start_Stop_Count        0x0012   096   096   000    Old_age   Always       -       7872
---
>   3 Spin_Up_Time            0x0007   161   161   033    Pre-fail  Always       -       1
>   4 Start_Stop_Count        0x0012   095   095   000    Old_age   Always       -       7885
72c62
< 193 Load_Cycle_Count        0x0012   069   069   000    Old_age   Always       -       313833
---
> 193 Load_Cycle_Count        0x0012   069   069   000    Old_age   Always       -       313884
```

Not sure what else I can do.

---

### Post by tgalati4 on 2007-05-13
Well,  you can run smartd (the daemon that stays resident and checks your drive health every 1/2 hour so.  It's part of smartmontools.

I'm glad you picked up on the device name change.  I was too lasy to read the dmesg, and I'm sure your devices are enumerated there.  It was late last night.

After reading your dmesg, I think you could benefit from more RAM.  It looks like you have less than 256MB.  Your 1.4 GHz processor is OK.  Ubuntu can do a lot of disk thrashing with less than 256MB of RAM.

Also, others have suggested putting Ubuntu on a small, fast hardrive (say a 7200 RPM, 20 to 40GB size) and using the large disks for media or /home static storage.  This gives you a faster system without the worry of the OS taking out the big disk with your data on it.

I think you are seeing normal behavior for your hardware.

---

### Post by PersistentLurker on 2007-05-13
First of all, tgalati4, thank you very much for your help so far.


> **tgalati4 said:**
> Well,  you can run smartd (the daemon that stays resident and checks your drive health every 1/2 hour so.  It's part of smartmontools. 

Well, this is the only working computer I have access to ATM, and until this problem is fixed I need to work under WinXP. So I can't really do that.

I did a manual check just now: still no errors. I think I'll assume that my HD is sound (impressive, given the obscene amount of thrashing WinXP does) . I guess the next thing I could check is the IDE controller.

> **tgalati4 said:**
> After reading your dmesg, I think you could benefit from more RAM.  It looks like you have less than 256MB.  Your 1.4 GHz processor is OK.  Ubuntu can do a lot of disk thrashing with less than 256MB of RAM.

A RAM upgrade or any other hardware change is not an option on this borrowed laptop :( . (Neither is partitioning, hence the use of Wubi.)

But wouldn't thrashing be characterized by nearly constant disk activity? Because that is most emphatically not what I see. Also notable is the fact that, right after installation, apps started very quickly, without any thrashing. This problem has worsened with time.

Other observations made since my original post: [list]
[*]I also observe the "halting" disk access when coping large files via cp.
[*]When reading a single large file (e.g. cat /path/to/a/600MB/iso > /dev/null), disk access seems to be reasonably (but not perfectly) constant.
[*]I found /proc/sys/dev/scsi/logging_level and set it to maximum verbosity. During disk access, a tremendous number of messages are spewed out. But pauses in these messages correspond to pauses in disk activity. I have not, however, found any pattern in terms of what happens before a pause.[/list]

Here's that free -m says when I'm logged in, running terminal emulators, running firefox, and running a text editor:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           233        228          5          0          3         59
-/+ buffers/cache:        165         68
Swap:          499         45        454
```

FYI: My system has exactly 256 MB of RAM physically installed. I'm guessing some of that is being used for video. 


> **tgalati4 said:**
> I think you are seeing normal behavior for your hardware.

If that's the case, then that's extremely disappointing. That would mean that WinXP is faster *by far* than this Xubuntu install. Most people in this forum suggest that such a situation is likely due to bad drivers. I tend to suspect that to be the case.

---

### Post by tgalati4 on 2007-05-13
I could be wrong.  But what is the motherboard?  What are the chipsets that control I/O?  

dmesg will enumerate the hardware and if the chipset is not Intel, VIA, SIS or some recognizable (i.e. pronounceable) name then you could be right.

In normal circumstances, Xubuntu on a 1.4 GHz machine with 256 MB should fly.

I think you may be experiencing thermal halts of the CPU.  It's possible that Windows XP is managing the processor heat effectively.  It's also possible that Ubuntu is not throttling the CPU or fan speed such that the processor is heating up cause either slow downs or down-right halts.  This would explain why things degrade over time.

Do you have any thermal monitoring?  Look in /proc/acpi/fan or thermal and see if you can find any files with temperatures.  If so, add an applet that will display those temps.

This thermal halting seems consistent with the behavior that you are experiencing.

Go into the BIOS and turn the fans on max and try again.  Does the laptop get excessively hot on the bottom?  If so, then raise the back end with the edge of a book, or use an iLap, like I do.

---

### Post by PersistentLurker on 2007-05-13
Thanks again.

I'm certainly glad to hear that Xubuntu should "fly" when things are set in order. I was fearing that I would have to go distro-hunting again.](*,) 

**CPU halting?**

Regarding the possibility that I'm getting CPU thermal halting: does this mean that the CPU shuts down for a moment to cool off? Am I correct to assume that would mean that all programs, including those that don't require disk access, would freeze during those moments? Would that mean that if I ran a CPU-intensive program that doesn't access the disk, the resulting CPU heating should produce halting of that program's operation similar to the disk access halting I've described?

Because none of that is consistent with what I'm observing. As a test, I ran, in a terminal emulator, the following code for about 12 minutes: 
```
$ i=0
$ while true; do i=`expr 1 + $i`; echo $i; done
```
This created a scrolling list of numbers, and CPU usage was 100% the entire time. I was also editing a text file in a USB drive and listening to an internet radio station (in other words: nothing required disk access). The CPU fan cycled on and off, there was no halting whatsoever, and the list scrolled smoothly the entire time.

And I am often able to work even when disk halting is occurring. The times when I can't and the display freezes probably can be attributed to swapping slowed by the disk halting.


**IDE controller halting?**

However, it never occurred to me to consider thermal issues, and you've got me thinking: thermal halting in the IDE controller *would* seem to be consistent with all of my observations.

Heck, maybe WinXP is so slow here because the drivers deliberately slow down disk access to prevent overheating! :p


**The chipset**

According to the Acer specifications ([http://www.acer.co.in/products/notebooks/tm2300.html#spec)](http://www.acer.co.in/products/notebooks/tm2300.html#spec)), this laptop has an Intel® 852GM chipset.

From your post, it sounds like you're assuming that a popular and well-documented hardware should have solid Linux drivers. I should say that my experience is rather different. I'm also wary of the fact that Ubuntu's IDE subsystem has undergone recent, fundamental, and some say ill-advised ([http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)) changes (as reflected by hda -> sda).


**Other users report success on this laptop**

[http://hardware.newsforge.com/hardware/05/07/16/0053210.shtml?tid=61:](http://hardware.newsforge.com/hardware/05/07/16/0053210.shtml?tid=61:) An article on NewsForge where someone managed to get Linux to run on this exact same model laptop. He didn't report any disk halting and considered it usable under Linux.

[http://technophobe.net/Acer_TravelMate_2304WLMi_notes.html:](http://technophobe.net/Acer_TravelMate_2304WLMi_notes.html:) an older Ubuntu version on a very similar laptop. Also no mention of halting.


**My plan:**

I guess this all leaves a faulty IDE controller or buggy kernel drivers as the likely causes.

I'm going to investigate how to test the IDE controller. I'll report back tomorrow.


My god, that was long. Sorry!

---

### Post by tgalati4 on 2007-05-13
Is there a reason that you need to run Feisty?  How much importance do you place on reliability, uptime, and dependability?  

Why don't you install plain-vanilla Dapper?  Unless you can't stand the Gnome desktop, it should run well on your machine.  

You made a good point about architecture changes in Feisty.  This is necessary to support all of the new hardware coming down the pipe.  It is quite possible that something broke.

The other possibility is that your controller chip is marginal and Ubuntu causes it to flair up while Windows does not.

Your hardware testing script was a neat idea.  I'm sure others can use it.  It quickly heated my Celeron 1 GHz processor from 42C to 48C while running at 100%.

Of course I have no idea what I am talking about.

---

### Post by PersistentLurker on 2007-05-15
Wow, 1 day with no post and the thread is pushed down over 15 pages. Dang things move fast here!

I've done some googling , and I haven't found any useful diagnostic utilities for IDE controllers. What little relevant literature I have found seems to suggest that I should look for software issues if hard drives perform poorly.

You bring up a very good point re: using an older Ubuntu version. For a traditional setup, I agree that using an older version is a very good idea when regular bugfix updates are available (fixes for bugs are more liley to have been found for older releases).

However, using Dapper isn't a great option on this unusual setup because Wubi doesn't support Dapper, and Wubi is mandatory on this borrowed laptop. Plus, I think I may be on the verge of finding a bug here that I can report. The F/OSS community has given me much, but it has much to go. I think it's about time I give back. I'm willing to work though and report the bugs - heck, I *want* to do that!

Regarding GNOME, yes, I don't care for it. As a former VectorLinux user, I'm used to minimalist desktop environments, and I find GNOME and KDE to be overwhelming. Plus, I expect to use older systems in the future, so I'm best off getting familiar with minimalist environments now.

Some other observations I've made that I want to throw out there:
[list][*]This is an Acer TravelMate 2303WLci
[*]To get a qualitative measure of the mangitude of this problem, I measured the time it takes to start OpenOffice Writer on Xubuntu and WinXP. WinXP required about 32 seconds, Xubuntu required about 3 minutes and 10 seconds.
[*][http://ubuntuforums.org/showthread.php?t=232795:](http://ubuntuforums.org/showthread.php?t=232795:) Somone else who has a somewhat similar problem, also with an Intel chipset (but not the same model as in this laptop), and seemed to feel that timer interrupts were to blame.[/list]

I think I'll install Topologix (sp?) on this system and see if it also suffers from disk halting. (I installed it before, but I didn't run it long enough to see if it had the halting problem.) I'll take me a little while, though, as I need to clear some space for it. And I've got a few ideas of some more tests to run and some BIOS variations to try. I'll report back later in the week.

---

### Post by tgalati4 on 2007-05-16
I have not used the Wubi disk architecture, but it could be the bottleneck.  It sounds like your install is running in an emulation mode (speedwise that is).  Have you searched on Wubi speed benchmarks to see if there are differences between using Wubi versus a plain intall?  It could be the difference between using a true Linux ext3 partition speed versus an NTFS partition.   I assume your installation is sitting on an NTFS Windows partition.

---

### Post by PersistentLurker on 2007-05-17
I posted a thread on the Wubi forum asking about this problem ([http://ubuntuforums.org/showthread.php?t=446013](http://ubuntuforums.org/showthread.php?t=446013)). One of the Wubi devs (ago) suggested that I check for disk compression and fragmentation.

I found that the files in which Xubuntu reside were indeed heavily fragmented. Defragmenting them has improved performance significantly - Openoffice start time is down to 1 minute 50 seconds. But that's still much worse than WinXP, and I am still getting the halting behavior. According to what I've read, the disk performance difference between a Wubi install and a standard install should be too small to notice.

More interesting news: I have installed Topologilinux on this same system to compare disk performance (to oversimplify, Topologilinux is to Slackware what Wubi is to Ubuntu). *Under Topologilinux, I experience no halting whatsoever.*

Apparently, some Linux kernel devs somewhere figured out how to get good disk performance out of this laptop, and that capability was lost somewhere between there and the Fiesty Ubuntu Kernel. I think I'd like to ask the devs to put that capability back in.

BTW, I know why you'd assume that I'm on NTFS - I'd make that assumption too. But for some reason, these partitions were formatted as FAT32.

---

### Post by PersistentLurker on 2007-05-18
Bad news - moving and defragmenting Xubuntu's disk images initially seemed to improve matters, but now, after some uptime, the halting is worse than ever. Openoffice start time has more than doubled to 6 minutes 50 seconds.

*SIGH* 
This is making me nuts. This behavior defies all logical pattern!

Anyway, ago came up with some more suggestions. From now on I think I'll just post in the thread on the Wubi forums.

---

### Post by PersistentLurker on 2007-05-18
I've just made another, potentially useful observation. If I'm interpreting this right, the halting only affects disk writing. Disk reading is smooth.

I ran these commands under both Topologilinux and Xubuntu:
```
dd bs=1024 count=819200 if=/dev/zero of=/path/to/test/file
dd bs=1024 if=/path/to/test/file of=/dev/null
```
Where /path/to/test/file was a valid path to a file on the partition seen as C: by windows, outside of the images on which Xubuntu/Topologilinux reside.
Basically, this wrote 839 MB of empty file and then read it back. Each time, dd reported the amount of time it took.

Here were the results:
On Topologilinux, 49.4194 seconds were required to write and 49.1285 seconds were required to read. No halting.
On Xubuntu, writing took 82.3074 seconds and had considerable halting. But it then read the same file in 48.1192 seconds, with no halting.

---

### Post by tgalati4 on 2007-05-20
Well, the kernels are open source.  You could look at the difference between kernels (if you can narrow it down to a subversion between the two kernels) and see what changed.  Newer kernels tend to support newer hardware, and sometimes things break with older hardware, leaving you stuck with a fixed kernel as other packages are compiled against the latest kernel.

If that is indeed the problem, then you would have to recompile  your favorate packages against the working kernel to stay current.

For all of that effort, you could buy a decent, used Thinkpad and just install Ubuntu on it and have most things work out of the box.

With all of the used hardware out there, it just doesn't make sense to knock your head against trying to get Linux to work in some oddball hardware/software configuration.

But if you do get it to work, post your workarounds, for some future Ubuntu user.

---

### Post by PersistentLurker on 2007-05-20
For the benefit of others encountering or pursuing this issue: I notice that the magnitude of the halting problem is directly related to memory usage. The more memory used, the worse the problem. When almost no memory was used (i.e. running in single-user mode), Xubuntu disk access was just as good as that observed under Topologilinux under any memory load.

I think you're right. The only reason I would want to pursue this issue would be to get the bug fixed for the benefit of other Ubuntu users. My goal of getting Linux to run well on this system has already been accomplished with Topologilinux. Until I can reproduce this problem on other systems, I am unlikely to attract developer interest. So I would have to go in a fix the bug myself

Between my very little programming knowledge, my complete lack of knowledge of kernel internals, the danger of messing around with untested stuff on a production laptop I don't even own, and the fact that the next month or two are the last months I will ever see this laptop, further work on this problem is fruitless.

I was hoping others would chime in and report similar problems on other systems, but that hasn't happened.

If I see this same problem on other systems, then I will pursue it again. If other users experience this problem on other systems, I encourage them to pursue the issue with the developers.

Until then, TTFN, thank you tgalati4 for your generous help and advice.

---

### Post by marco12 on 2007-05-21
Hi,

I am not sure that my problem is related to the described issue.

Since upgrading to feisty my acer laptop became extremely slow. Starting and switching programs takes longer. When the memory usage is high it can take 30 seconds to switch between open programs. Most of the time the CPU spends with iowait.

I learned that the disk driver was changed in the feisty kernel. And there were complains about that hdparam does not work anymore. I think my issue is related to this. hdparam shows that my disk is in 16 bit mode.

I have to boot regularly because there also seems to be a memory leakage most probably with firefox which leads to high swap usage and an almost irresponsive system.

Is this related?

Do you know where I can find help?

Regards,
Marco

---

### Post by tgalati4 on 2007-05-21
Don't discount your ability to program or fix problems yourself in Linux.  If you can read, then you can share your observations with others.  Then others can suggest patches that you can try.  Since I'm a Dapper user, I can't comment on disk architecture changes, but 16-bit vs 32-bit mode would make a speed difference.  Also DMA vs non-DMA disk access can greatly affect speed.  Since you have the problem in front of you, only you can help the rest of the community narrow down the possible causes--and eventually a fix.

---

### Post by PersistentLurker on 2007-05-23
> **marco12 said:**
> Since upgrading to feisty my acer laptop became extremely slow. Starting and switching programs takes longer. When the memory usage is high it can take 30 seconds to switch between open programs. Most of the time the CPU spends with iowait.

I learned that the disk driver was changed in the feisty kernel. And there were complains about that hdparam does not work anymore. I think my issue is related to this. hdparam shows that my disk is in 16 bit mode.

I have to boot regularly because there also seems to be a memory leakage most probably with firefox which leads to high swap usage and an almost irresponsive system.

Is this related?

This could be the same problem that I've experienced, or it could be plain old fashioned disk thrashing. It's possible that Fiesty is much more memory hungry than past versions for some reason (which would be unfortunate).

When the system is sluggish, is there constant disk activity? Or does disk activity come in bursts, with virtually nothing happening in between?

If it's the former, it's probably disk thrashing. If it's the latter, then you are experiencing the same problem as I have, in which case we should pursue this issue with the developers.

---

### Post by mairabc on 2007-05-24
One more Acer laptop with  the slow hard drive access. Started after installing Feisty as well.

I haven't started to seriously pursue the reasons yet, I am just stating that this doesn't seem to be an isolated case.

If I find out something new, I'll post it back here.

Best regards,
Maira Carvalho

---

### Post by colanderman on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/119730](https://bugs.launchpad.net/ubuntu/+bug/119730) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **PersistentLurker said:**
> **Note:** This issue is **abandoned** until I see this problem occur on other systems. If you encounter the problem described in this thread, do please chime up to get the bug fixed.

Don't abandon it just yet... I think you are seeing exactly [this bug](https://bugs.launchpad.net/ubuntu/+bug/119730), which was created after discussion in [this thread](http://ubuntuforums.org/showthread.php?t=447474).

---

### Post by PersistentLurker on 2007-11-23
> **colanderman said:**
> Don't abandon it just yet... I think you are seeing exactly [this bug](https://bugs.launchpad.net/ubuntu/+bug/119730), which was created after discussion in [this thread](http://ubuntuforums.org/showthread.php?t=447474).

Ah, good to see that people are aware of this now.

Anyway, I gave back the TravelMate nearly 5 months ago and I'm not using Ubuntu anymore, so this is not of concern to me now. However, I'll change the first post to reflect the progress that's been made.

Thanks much for letting me know about this.

---

