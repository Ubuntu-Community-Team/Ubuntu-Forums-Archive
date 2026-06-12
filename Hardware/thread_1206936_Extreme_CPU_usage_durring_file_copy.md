---
title: "Extreme CPU usage durring file copy"
date: 2009-07-07
forum: Hardware
---

### Post by X-Kent on 2009-07-07
Hi.
I have toshiba m750 m7202 tablet pc. I installed jaunty on it as soon as it arrived. My system is fully updated running kernel 2.6.28-13.

I have a strange CPU usage during a file copy. For example if I copy big (couple of gb) file, system starts copying and everything is fine for about 3-5seconds, then CPU usage begins to rise and after about 10 seconds I have 100% CPU usage. After another 5-10 seconds system becomes much less reposive (CPU is busy) and it's almost useless until file copy finishes. 

There is no matter if it's from ntfs to ext3, from fat32(flash card) to ext3 or vice versa.

I may have found something about this bug here (about a month ago):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775)
The status of this is bug report is "new" and it's still in undecided state.

This is a pretty critical bug as file copy is pretty common operation and therefore it should had get some priority in fixing but it's not seems the case as the bug is present since the release of jaunty.

Anyone have this problem ? Is there any workarounds available ?

---

### Post by shatterblast on 2009-07-07
In my experience with Windows, file-copying related to NTFS or any of the FAT structures puts a huge drain on my system resources.  With EXT3 and EXT4, I have not had this issue.   Since I also occasionally will copy files from M$ related to FAT32, I have the issue as well.  For some reasons, my system doesn't cope well with NTFS conversions, but it can deal decently with FAT32 at least.  Still, I can only run one moderately intensive thing at a time with no high-end graphics creativity or gaming.  With EXT3 to EXT3 or EXT4, I have not had this issue.

What processor type do you use and how much RAM does your system run?

---

### Post by X-Kent on 2009-07-07
It is 2.4ghz core2duo with 2gb of ram (actually 1.8gb due to onboard video)
I have 100% CPU even if I copy file form ext3 to ext3 (on the same filesystem)

---

### Post by shatterblast on 2009-07-08
Is your version of Ubuntu the x64 kind?  I think a few processor types will try to run full speed even if they shouldn't on x32 systems.

---

### Post by X-Kent on 2009-07-10
Yes I have 64bit version as my CPU is 64bit.
What do you mean few processors will run it full speed? File operations are not CPU kind of job so I see no reason for CPU on both cores get 100% busy while copying.

As I see in gnome applet CPU meter, CPU is used by system(kernel?) as I can't see any process that is consuming cpu.

---

### Post by shatterblast on 2009-07-10
> **X-Kent said:**
> Yes I have 64bit version as my CPU is 64bit.
What do you mean few processors will run it full speed? File operations are not CPU kind of job so I see no reason for CPU on both cores get 100% busy while copying.

Actually, they are CPU-related, especially during a conversion process, but the greater majority of resources tend to require RAM memory and to a lesser extent the on-board firmware of your computer things.

While it appears the issue may not affect you, over-heating on a x32 system occurs I think mostly from the "Hyper-threading" capability of a x64 Intel processor.  The Linux kernel sends a message requesting the expected processor speed, but the software environment of a x32 system lacks the tools to efficiently meet the demands of the x64 CPU.  It can affect a few AMD models.

> **X-Kent said:**
> 
As I see in gnome applet CPU meter, CPU is used by system(kernel?) as I can't see any process that is consuming cpu.

I think I read about a compatibility issue between EXT4 and certain types of x64 processors.  The best solution usually involved upgrading the Linux kernel.

Does your operating system use an EXT4 partition?

---

### Post by X-Kent on 2009-07-14
No, I use ext3 filesystem. 
Should I consider downloading a kernel from kernel.org and compiling it ? I done it sometime but I would prefer a binary package if I could find one for my system. For now there is no kernel updates at  update manager...

---

### Post by shatterblast on 2009-07-15
Updating the Linux kernel alone can cause conflicts with other software in different ways.  I suggest trying a Live CD of the Karmic test version.  While in the Live CD's environment, it might do well to run tests from two physical medias.  This could include copying files from a hard drive to a USB device and then copying them back to a blank folder maybe.

Since the Karmic test version has the Linux kernel updated with the correct dependencies, you could potentially update to that version.  I would express caution with updating your system after that point.  A new update could break your operating system's functionality, especially considering how new Linux kernels may come down the stream to cause unknown issues.  Updates can be controlled through the Software Sources window found under Administration.

Here is a link to the latest Alpha version of Karmic:  (Probably should try this.)

[http://cdimage.ubuntu.com/releases/karmic/alpha-2/](http://cdimage.ubuntu.com/releases/karmic/alpha-2/)

And a link for the most recent:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by adamitj on 2009-08-01
I have a HP Pavilion DV6636NR with Turion X2 processor and still facing the same problem. From the first time I thought it was an Ultra-DMA error, but it wasn't (as described on [1]).

By now my laptop is running Ubuntu 9.04 64-bit version in a XFS partition. I tried EXT3, EXT2 and XFS in the past but doesn't make difference.

This issue is really giving me nuts since there is no way to use the computer while my weekly backup script is running (rsyncing at least 20 GB of files from my server).

I desperately need to solve this problem...

[1] [http://ubuntuforums.org/showthread.php?t=1151314](http://ubuntuforums.org/showthread.php?t=1151314)

---

### Post by forlau on 2009-08-03
Same problem here: 
Installed yesterday 9.04 Kubuntu 64 bit. I copied files from Sata drive (/dev/sda) to Sata drive (/dev/sdb), both ext3 formated. CPU Load is 100% during copy process. 

When using 8.04 32 bit before, i never had any trouble with cpu load during copy process.

Any idea?

---

### Post by idude on 2009-08-24
I'm running 32bit Ubuntu 9.04 and seem to have low CPU use but high system load when copying from a second EXT4 drive to an EXT3 primary drive.  CPU is 0-15% but load is at ~10.70 until the copy completes, which in my case takes a little while since it is usually around 124GB total with a few multi-GB size files.

I did not have this load problem when copying from EXT3 to EXT3 on two separate drives.

---

### Post by brillytsang on 2009-10-04
I have the same problem of having 100% CPU usage with Dell latitude D820 with Intel T2500 and 3G of ram.  I'm running Jaunty with the latest update on 32bit.

---

### Post by X-Kent on 2009-10-27
I have replaced my laptop with the same machine but now it's 2.53ghz cpu, still, same CPU problem in jaunty.
Karmic comes out in 2 days, hope it will fix this issue. I didn't find any patch for jaunty to solve the problem :-(. (tried compiling new kernel, didn't help).

I am not sure that I am right here but I think it's the RT processes (kernel/system) that take the CPU during the file copy, leaving no CPU time for a normal processes. No meter is it interactive or not-interactive.

---

### Post by niksakl on 2009-11-13
I am having very high cpu usage myself when i transfer files. running kubuntu 9,10 64bit on a q9550, 2gb ram system, which is ridiculous, this needs to be fixed.

---

### Post by TheThek on 2010-01-15
There is already a bug for this problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775")
but sadly still no solution.

---

