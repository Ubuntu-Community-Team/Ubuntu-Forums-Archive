---
title: "&quot;No Root File System Defined&quot; on automated install w/ RAID"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Kareeser on 2009-04-30
Hey all,

Just for fun, I'm trying to get a system installed using kickstart. It works, so I tried it with a software RAID setup. Here's the section of my kickstart file which deals with the drive partitioning:

```
#Disk partitioning information
part /home --fstype ext3 --size 11264 --ondisk sda 
part swap --size 1024 --ondisk sda 
part raid.01 --size 8192 --ondisk sdb 
part raid.02 --size 8192 --ondisk sdc 
raid / --level=1 --device=md0 --fstype ext3 raid.01 raid.02 
```

I've made sure my virtual drives are big enough. sda is 12 GB, and sdb ad sbc are both 8 GB in size.

Unfortunately, when I ran the install, it stalled at the drive partitioning step with the error "No Root File System Defined", even though it's defined right there in the kickstart file.

I figure I'm probably doing something wrong.. but what?

---

### Post by krowa on 2009-06-25
Hello,

I am trying install Ubuntu with kickstart too, but I have problem with boot. Can you tell me how you tell ubuntu installer to use kickstart file?

Now I make it like this:
kernel /casper/vmlinuz
append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ks=cdrom:ubuntu.ks.cfg quiet splash --

But it is not work.

regards

---

### Post by supernovus on 2010-04-08
Nobody knew the answer to this? I am trying to install Ubuntu 10.04 with RAID 1, following the instructions from [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) and it seems to work right until I try to "write changes" at which point it tells me "No root file system defined" and the installation will not continue.

Highly annoying, and not very intuitive. I hope the installer gets reworked to be easier to use with common setups such as RAID.

---

### Post by Stormran on 2010-04-09
I am also having this issue trying to install Ubuntu Server 10.04 beta 2. No root file system is defined. Anyone have any suggestions?

---

### Post by Stormran on 2010-04-09
After you create the partitions and the Software RAID you have to go back and set the RAID partition to mount to root. After I did this I had no trouble installing Ubuntu 10.04 beta 2.

---

### Post by RJARRRPCGP on 2010-04-09
> **Kareeser said:**
> 

Unfortunately, when I ran the install, it stalled at the drive partitioning step with the error "No Root File System Defined", even though it's defined right there in the kickstart file.


Lately, the regular graphical installer (Ubiquity) sucks! I had a problem with the live CD not coming up, not too long ago. But, I cannot recall getting that error with the alternate installer. 

(I just assumed you were running Ubiquity, but realized that it don't support RAID. O_O) 
(must use the alternate installer for RAID)

---

### Post by soveryapt on 2010-05-25
> **Stormran said:**
> After you create the partitions and the Software RAID you have to go back and set the RAID partition to mount to root. After I did this I had no trouble installing Ubuntu 10.04 beta 2.

Been looking for an answer to this issue since the release of 10.04 and just wanted to say thanks!

---

### Post by mikebravo on 2010-05-27
> **Stormran said:**
> After you create the partitions and the Software RAID you have to go back and set the RAID partition to mount to root. After I did this I had no trouble installing Ubuntu 10.04 beta 2.

Please point me to something that will tell a noob how to do this.

---

### Post by ykanello on 2010-07-13
This first post is 1 year old, but I haven't seen the answer to it.
I do have exactly the same error.

My ks.cfg reads exactly the same 
> raid / --level=1 --device=md0 --fstype ext3 raid.01 raid.02

but I get the same error during kickstart.
Is there any suggestion by anyone?
Any help will be highly appreciated :)

---

### Post by asaturn on 2010-09-06
> **mikebravo said:**
> Please point me to something that will tell a noob how to do this.

go back, on the partitions list, choose raid#1 (main partition on both drives) and hit enter, select / as the mount point and ext4 (or 3) as the fs, then bootable flag to yes (if it asks)

then go to raid#2 (swap partition on both drives) and set it to "swap space"

pretty simple

FINALLY someone figured this out though

---

### Post by sinj on 2011-09-16
> **asaturn said:**
> go back, on the partitions list, choose raid#1 (main partition on both drives) and hit enter, select / as the mount point and ext4 (or 3) as the fs, then bootable flag to yes (if it asks)

then go to raid#2 (swap partition on both drives) and set it to "swap space"

pretty simple

FINALLY someone figured this out though

...1 year has past I know

..so yes the above works when manually create a RAID device but with automated kickstart install RAID partitioning fails. Me too the same error  "No Root File System Defined" error occurs with a red background and a simple continue button on it which gives back the same error. I can`t go back to make any changes! (And I don`t want to thats why I`d like to do automated partitioning.)
Here is the partitioning part of my kickstart file:

part raid.01 --size 1024 --ondisk sda
part raid.02 --size 1 --grow --ondisk sda
part raid.03 --size 1024 --ondisk sdb
part raid.04 --size 1 --grow --ondisk sdb
raid swap --level=1 --device=md0 --fstype swap raid.01 raid.03
raid / --level=1 --device=md1 --fstype ext3 raid.02 raid.04

whats wrong with it?

---

### Post by ykanello on 2011-09-19
it seems that the issue after a year (I really haven't tried for a year) is still there...

---

### Post by peetaur on 2011-11-25
I had this problem, but maybe not the same as you. And I have the solution that worked for me.

**My specific problem symptoms:**
If I used kickstart without preseed, it would prompt me for an iSCSI target server. :(

If I used preseed to force skipping of the iSCSI menu, I would instead get the same error as you (no root file system defined). :confused:

Then I tried manually formatting a partition, and it would not let me, saying it was in use. 

Based on that, I found a page saying I might have an lvm volume I need to remove. But I had no such thing.

The command
pvdisplay
Showed no physical volumes.

Next I found this page, which suggested I might have a software raid superblock. 
[http://www.overclockers.com/forums/showthread.php?t=667317](http://www.overclockers.com/forums/showthread.php?t=667317)

**My specific problem cause:**
It was true... I had raid some software raid devices.

Probably my disks were used in a RAID test before I got them. 7 out of 22 servers had this problem.

**My specific problem solution:**
Hit alt+f2 while the install is failed, hit enter to get a prompt.

ls /dev/md*
would show 3 raid devices.

So I removed them:
mdadm --stop /dev/md125
mdadm --stop /dev/md126
mdadm --stop /dev/md127

Then I zeroed the superblock on all my disks using dd. Apparently you can also do this:
mdadm --zero-superblock ${disk}
where ${disk} is the whole disk device. (eg. /dev/sda)

Then I rebooted, triggered PXE again, and kickstart + preseed finished installing. :)

---

### Post by schulze-tue on 2012-01-18
peetaur, that's interesting and encouraging to hear. 

I am having exactly the same problem (no root file system defined when trying to configure a software raid in kickstart). I am using Ubuntu 10.04. However, your suggestions regarding the raid superblocks did not help in my situation.

What strikes me, is that I can not use the **--fstype** argument with the **raid **command. S.th. like 

```
 raid / --level=1 --device=md0 --fstype ext3 raid.01 raid.02
```

results in a warning like fstype argument not recognized. I can use the **--fstype** argument with the **part **command without a warning or error message, however.

This makes me wonder, if there is a general problem with my kickstart syntax. Would it be possible for you to share the kickstart file, with which it was actually working (after removing the raid superblocks on your disks)?

---

