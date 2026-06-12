---
title: "SSD Desktop Install"
date: 2013-03-24
forum: Hardware
---

### Post by ianp5a on 2013-03-24
I'm still not clear where the SSD performance should be used for a home PC. Mine has: 
  -  Boot/OS HD (~27Gb used) 
  -  Data (home) HD (~300Gb used) . 
  -  No (known) separate temp? Whatever that is.
I'm prepared to shift everything around if necessary. I'm ready to buy any SSD. I had thought 64Gb SSD for the boot disk. But from reading above it seems not.

Where should one use an SSD to the best effect and what size? Thanks.

---

### Post by oldfred on 2013-03-24
@ianp5a
The OP is just using another data partition as temp to copy files into and out of.
How are you using 27GB in / with a separate /home? Lots of stuff in .wine? Years of log files?
I have 9GB used in my install on my SSD in a 27GB partition and that includes /home, but all data is on my rotating drive.

---

### Post by ianp5a on 2013-03-25
> **oldfred said:**
> @ianp5a
How are you using 27GB in / with a separate /home? Lots of stuff in .wine? Years of log files?

I put / and /home on separate physical spinning disks. The OS is **new** and the only thing on there. 
If putting the OS on an SSD is recommended, then I will install it from scratch. I don't know of any log files. Nothing in .wine.

So, just imagine you were setting up a new simple home user PC from scratch, where should the SSD ideally go? 
On /? 
On /home?
Should the SSD go where all the action taking place? Or should I avoid writing to it too much?

---

### Post by oldfred on 2013-03-25
Moved to your own thread as your issue is Desktop and old thread was server. 
While some of the issues may be similar better to be in own thread.

Many suggest having / (root) on SSD and /home on rotating drive so that data you access less often is not on SSD and the parts you use the most are on the fastest drive. I go one step further as I want each drive to be fully bootable, and data then can be anywhere. So I split /home and only keep the mostly hidden user settings in /home and keep that on SSD inside my /. But then I create data partitions on hard drive(s) and mount those and link folders from data partitions into my /home so it looks like a normal install.

         I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by ianp5a on 2013-03-25
Thanks for moving the thread. 

I like the idea of splitting the data from /home. I hate all the junk in home, which is not invisible when using some applications "open" and "save as". I wish the installer offered that. 

Moving /home was tricky enough. And your instructions for moving /data appear scarier. I'm not going to attempt it unless there is an easy way.

I'm reading all the links now and have yet to find a definitive answer about SSD performance.  Many threads concentrate on reducing writes to the SSD to prolong it's life. Some say boot from the SSD.

There really should be a tweak application containing all that knowledge for the increasing number of people buying SSDs these day.

---

### Post by oldfred on 2013-03-25
Some info on SSD:
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)


 You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.
Info on trim and ext4 without journel 
[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)

I think this was what I did:

 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

   [http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)

   fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

   noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

---

### Post by ianp5a on 2013-03-25
Thanks. Your link [***Your precious Solid State Drive***]("http://ubuntuforums.org/showthread.php?t=2003022") covers it exactly.
I got so many hits on SSD performance tuning, it drowned out what I was asking: **"Planning" the purchase and installation of an SSD**.

After reading the link above I believe the optimum for performance and life of the SSD is like this:
Buy a small 64Gb SSD and put:
 - SSD= boot / and /home on it. For fast boot etc.
 - HD  = All my data on a big HD.
Then carry out the tuning as recommended by the other links.

---

