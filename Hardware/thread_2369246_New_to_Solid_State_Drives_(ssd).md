---
title: "New to Solid State Drives (ssd)"
date: 2017-08-20
forum: Hardware
---

### Post by Liamdale on 2017-08-20
Had a new computer built with kubuntu installed.  My conversations with the tech gave me a strong impression that he did not know Linux systems.  My research previous to ordering my new computer indicated that the ssd must be aligned correctly.  A text I read on Lifehacker stated:
> if you've already migrated to an SSD, you might not have realized that you're sacrificing performance with misaligned partitions. A regular hard drive usually starts its first partition after 63 empty blocks, while SSDs require 64 blocks of data for optimal performance. This means that sometimes, if your SSD was formatted by something other than Windows' installer, it can be aligned incorrectly and will transfer data much slower than intended

Using Gparted I reviewed the device information and got the following:
Partition table: gpt
Heads:            255
Sectors/track: 63
Cylinders:       58369
Total Sectors:  937703088
Sector Size:    512

Question: Does the indication Sectors/track:  63  indicate that the ssd is mis-aligned ?

---

### Post by vocx on 2017-08-20
> **Liamdale said:**
> Had a new computer built with kubuntu installed.  My conversations with the tech gave me a strong impression that he did not know Linux systems.  My research previous to ordering my new computer indicated that the ssd must be aligned correctly.  A text I read on Lifehacker stated:


Using Gparted I reviewed the device information and got the following:
Partition table: gpt
Heads:            255
Sectors/track: 63
Cylinders:       58369
Total Sectors:  937703088
Sector Size:    512

Question: Does the indication Sectors/track:  63  indicate that the ssd is mis-aligned ?
Honestly, this is the first time I hear about this. «Sigh». Don't believe everything you read on the Internet. Where did you find this information exactly? Where is the link?

To me this just sounds like information that has no basis, trying to sound cryptic, and appealing to "wannabe hackers". I wouldn't worry. My device also says 63.
```

Partition table: msdos
Heads: 255
Sectors/tracks: 63
Cylinders: 1946
Total sectors: 31277232
Sector size: 512

```

---

### Post by oldfred on 2017-08-20
Its true, but now very old.
Windows 7, I think was first to change. XP used sector 63 as first sector. But 7 used 2048. 
Soon after gparted & Linux changed to use sector 2048 as first sector.
You would have to use very old partition tools to get a mis-aligned system.

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
sudo parted /dev/sda unit s print 

With new SSD, very little is actually required now.

but you can review these now older threads.

 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4, and if on flash drive turn off journal. Some formats do not support trim which is required for SSD. 
 I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by Liamdale on 2017-08-21
Thank-you oldfred for the information.  It has been a learning  process since I switched to linux in 2014.  vocx is right, there is a great deal of incorrect or outdated information out there.  The information you have written will help me better understand my linux computer.  I started to question the ssd alignment when my new Kubuntu 17.04 installation didn't perform correctly, namely the software center crashing occasionally.  My old computer was a dual boot ubuntu/win xp setup (2 hard disks) causing no problems.  The ssd is a new experience and I am trying to better understand the differences between the hdd and the ssd.  My current projet is how to modify the traditional linux partitions (root-swap-home).  Swap on the ssd  can (according to some documentation) cause the premature wear on the ssd.  A ssd-hdd combo approach is recommended (again according to some documentation).  Still have a lot to learn.

Thank-you for the input.  I will designate this thread as solved

---

### Post by oldfred on 2017-08-21
If you have 4GB or more of RAM, you may never use swap. Only something like editing videos or a few other apps may use all of RAM.
So if never using swap, you cannot wear out the SSD.  I normally do put swap on HDD as system seems to work better with some swap, but only assign 2GB as will never hibernate. With SSD it boots very fast.

New versions of Ubuntu do not create a swap partition. They now use a swap file.
 [http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)
Starting from 17.04 Zesty Zapus release, instead of creating swap partitions, swapfiles will be used by default for non-lvm based installations.
no more than 5% of free disk space or 2GiB, whichever is lower. 


I never use software center. But they changed from one version to another based on gnome's.
I use synaptic as it tells you actual package name and has available more details of package or just command line(but you have to know package name).
sudo apt install synaptic

---

### Post by vocx on 2017-08-21
> **oldfred said:**
> If you have 4GB or more of RAM, you may never use swap. Only something like editing videos or a few other apps may use all of RAM.
...

This is correct. Swap is basically a relic of the time when computers had less than 512 MB RAM. Now, with computers typically coming out with 4 GB and expandable to 64 GB, it's not a big issue. If you are a regular user, and not a virtualization server guy, then you probably don't need to worry about swap.

> **Liamdale said:**
> ...
Swap on the ssd  can (according to some documentation) cause the premature wear on the ssd.  A ssd-hdd combo approach is recommended (again according to some documentation).  Still have a lot to learn.

Beware of overcomplicating things. Your computer hardware is meant to be used. If you are constantly thinking about preventing wear you are going to be too picky in making decisions. Learn to use your system without worries. To me an SSD is nothing but just another box of technology which works the same way as a common HDD. This is the intention of the manufacturers, that you use a device that intrinsically is different, but works the same, and you don't have to worry about the details.

---

### Post by Liamdale on 2017-08-21
I use the Software center occasionally but most of my installation to date have been from the terminal (apt-get).  I am using more and more synaptic as I begin to understand better the package components.  I find synaptic very useful to manage repositories and check if an un-install is complete.  Even if the software center is little used the fact that it crashes must be noted.  I am using kubuntu because I like the plasma GUI and wanted to try it out on a daily bases.  My first dislike is Discover (software center).  I have tried out software centers from unbuntu, mint and now, kubuntu.  I find that the ubuntu software center is my preferred choice.

Thanks for the heads up on the swap file (partition).  I want to eventually integrate at least one of my two hard disk to my new system. This why I am learning how to set up my system onto two drives; root - part of /home on ssd  and swap and rest /home on hdd.    As vocx has just mentioned maybe I'm over-thinking it.  But the fun is in experimenting and learning.

---

### Post by oldfred on 2017-08-21
Whether you have a SSD or HDD, it may fail tomorrow or last a very long time. Failure of drive is why you should have backups.

But SSD now have comparable lives to HDDs.

 [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb) 

My very first SSD was only 60GB and I had two installs of Ubuntu on it. And now my new SSD is 120GB and I do not know what to do with all the space, still had two 30GB installs and left over room. Many say you should over provision or have some unused space, which I seem to have a lot of.
And I like to have a full install on every drive, even larger flash drives for data, just as an emergeny boot hopefully never needed, only occasionally updated and not a lot of extra apps installed. perhaps a few for repair or maintenance like gparted.

---

### Post by Liamdale on 2017-08-21
Yes I realize that,  my ssd is 500G.  Space for the operation system is not a problem.  I noticed that there is only one Linux partition for Root-Swap-Home.  You told me that 17.04 uses a swap file by default which takes care of that partition.  Does Kubuntu manage the available space for both the system files and the /home files, I do not know.  

I will eventually integrate one of my hard disks but at this point in time it not clear on which approach I will take.  I am still in my first week of my new computer purchase.  Still installing software...  The partition software also shows a fat32 partition of 512Mb with 4Mb used, why it's there I have no idea.

---

### Post by oldfred on 2017-08-21
If you have a FAT32 formatted partition typically first or second, that is the ESP - efi system partition used for UEFI boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

Each user is supposed to manage their own space. 
You should regularly check system sizes, but I use 25GB for / and currently use about 8GB in my 16.04 install. Less in my other test installs. But I houseclean periodically, so backups are not as large.


 # check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null 

      
 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 
   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by Liamdale on 2017-08-21
This has been very enlightening.  Lots of study ahead.  
Never thought that my misinterpretation of partition information would bring me so far. 
Thank-you for the information. 

The thread has already been change to [Solved]

---

