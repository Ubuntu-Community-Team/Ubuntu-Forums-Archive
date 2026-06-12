---
title: "Software raid strange behavior."
date: 2012-12-07
forum: Hardware
---

### Post by georgesgiralt on 2012-12-07
Hello !
First, the context :
Ubuntu LTS 12.04.1 current (with all upgrades made).
Disk layout is as such :
3 Serial Ata drives each hosting two partitions defined exactly the same : 
First primary partition around 250 Mb tagged raid auto detect
Second primary partition with all remaining space also tagged raid auto detect. 
Grub installed on each drive's MBR.

Two raid 1 device created using these 3 disks : md0 and md1.
md0 consists of sda1, sdb1, sdc1 forming a raid 1 (mirror)
md1 consists of sda2, sdb2and sdc2, forming a raid 1 (mirror).
md0  is formatted with an ext4 file system and holds /boot. 
md1 is an LVM2 PV. 
On this  PV all the lvm layout is set and the system is installed. 

One of the 3 disks failed. So far, so good. I unplugged it because it was making a lot of noise trying to move the heads outside the parking zone.

At each boot of the system with a failed disk, I got a message asking if I want to run the degraded arrays. I CAN'T answer as the USB keyboard is not working at this stage  ! 
So when the timeout triggers, a shell is dropped  at the (initramfs) level. 
Here I can say "exit" and the boot process takes place with the two degraded arrays. 

I was unable to remove the failed disk from array, mdadm complaining there was no /dev/sdc1 (resp. /dev/sdc2) device. 

Yesterday, I got the new disk to replace the failed disk (which was sdc by the way). 

After plugging it in, the system was unable to detect the two arrays anymore. And refused to boot. 

So I was forced to unplug the power cord of the new disk, boot the system, then plug the power cord on the new disk in order to partition it. I was fearing this could cause problems... But worked like a charm !  

Once fdisk exited, I was able to add each partition to it's respective array and watch the system synchronize the data back. 
Then I was able to install grub on the MBR of the new disk (grub-install complaining that there are extra drives on arrays...)

Questions : 

1) why could I not answer the Yes/No question at md detection ? 
2) why was it impossible to remove the failed disk from array ? 
3) why was md detection failed when the new unformatted disk was plugged in ? 
4) why grub complains during installation about extra mirror devices (but do the job finally... ) 

Many thanks in advance for your enlightenment and help... As I HAVE to keep this system running at whatever costs, it would be highly appreciated !

---

### Post by TheFu on 2012-12-07
Thanks for providing lots of data.  However, running a few commands and showing that output might have been easier. I know that I'd tend to believe the output from **sudo mdadm --detail /dev/md1** more than any description.  I'm not saying that your description is not accurate, but sometimes we don't have the level of understanding that we think we have .... does that make sense?  I know I've not noticed details and someone here did.

Are you monitoring the SMART data for each disk?  How does it look?

I've never seen anyone use RAID1 across 3 disks without using RAID0 too. just 2. Perhaps that is not a standard use-case for mdadm and unsupported/undefined? I dunno.

For a system that cannot be down, you'll have great, versioned, backups and a failover machine.  Can you failover to the other box?  How is the RAID configured on it? Any issues there?  On your test machine, you can try out all sorts of RAID settings too.  For really critical systems, we usually have at least 4 separate environments - dev, pre-prod, prod-A and prod-B.  Dev can be small, but the others are sized the same as production.  For **really, really critical systems**, add in a few more environments for QA and different development work areas.  If you don't have these different environments, it is time to provide a written report and estimate to the decision makers so you can get them. If there isn't money for these, then the systems really aren't that important.

Are all the HDDs identical, from the same manufacture run?  Sometimes disks with the same part number are not the same internally - I've heard of some disks changing from 512b sectors to 4k and still having the same model number. Unlikely in your situation, but you never know.

Are you using RAID designed/enterprise disks, not cheap consumer level drives that don't have the same instruction set?  These are known to fail when placed into a RAID config.

Sorry that I didn't have any real answers, just questions.  I've been running mdadm for  RAID on systems here for about 6 years.  I've lost a few HDDs, but never any data.  I've never needed to restore from a backup, but still have backups created nightly.

I'm a little confused that the system wouldn't boot based on any RAID configuration.  You didn't put the /boot onto RAID. That is definitely not a best practice.  I also think that having the OS on RAID is not a best practice, but that is open to debate. I just know that I do not.

I'll take a stab at your questions.  

I've never had mdadm "automatically recognize" a **new disk** should be used in a RAID set. I've always had to manually tell it which partition to use for a specific RAID device. After told and the disk gets marked, it does become automatically recognized.

In a degraded array, a failed disk is automatically removed. I must not understand the question. Sorry, I'm a little slow this morning.

grub has changed over the years and I'm hardly an expert. For this question, you probably need to specify to 3-4 levels the exact version of grub involved. It is likely that asking this question on the grub support forums will be necessary.

Anyway, I hope I haven't shown my ignorance too much today and some others will add and correct what is wrong.

If the system needs to keep running *at whatever costs*, then you should have at least 2 production servers running it located in different physical data centers at least 500 miles apart.  Time to get the budget to make that happen to reduce the outage risk. This design can handle both failover and disaster recovery, so in the long term, it is cheaper.

---

### Post by georgesgiralt on 2012-12-07
Hello !
Thank you for your answer. 

> **TheFu said:**
> Thanks for providing lots of data.  However, running a few commands and showing that output might have been easier. I know that I'd tend to believe the output from **sudo mdadm --detail /dev/md1** more than any description.  I'm not saying that your description is not accurate, but sometimes we don't have the level of understanding that we think we have .... does that make sense?  I know I've not noticed details and someone here did.
Here is the output of mdadm --detail :
```

/dev/md1:
        Version : 0.90
  Creation Time : Sat Jan 23 07:21:01 2010
     Raid Level : raid1
     Array Size : 312359700 (297.89 GiB 319.86 GB)
  Used Dev Size : 312359700 (297.89 GiB 319.86 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Dec  7 18:01:48 2012
          State : active 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : 4c3bb137:2bdc695c:96cc1437:75f9bf00
         Events : 0.5505786

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       18        1      active sync   /dev/sdb2
       2       8        2        2      active sync   /dev/sda2


mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat Jan 23 07:20:30 2010
     Raid Level : raid1
     Array Size : 208704 (203.85 MiB 213.71 MB)
  Used Dev Size : 208704 (203.85 MiB 213.71 MB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Dec  7 14:59:13 2012
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : 0a2b61ee:7f007d6b:d9488f2a:913cc964
         Events : 0.2928

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1

```
Here, md1 has it's first disk as sdc (which was the failed one) but this does not explain why both, md0 and md1, did not come up with the non initialized  sdc ....
> 
Are you monitoring the SMART data for each disk?  How does it look?

No  absolutely not. I rely on the third disk. And on the BIOS which is SMART enabled. And with the keen eye of my wife which write down every unusual message she gets when booting up the computer or using it... So far, it worked. She was the one which spotted the failed disk. 
> 
I've never seen anyone use RAID1 across 3 disks without using RAID0 too. just 2. Perhaps that is not a standard use-case for mdadm and unsupported/undefined? I dunno.

Actually I used 3 disks when I set up the machine because I used the LVM2 mirror which, as you may know, needs 3 devices for raid 1 : two to hold the data, one for the logs and indexes. I gave up on LVM2 mirror and replaced it by md mirror, using the 3 disk I had on hand. 
> 
For a system that cannot be down, you'll have great, versioned, backups and a failover machine.  Can you failover to the other box?  How is the RAID configured on it? Any issues there?  On your test machine, you can try out all sorts of RAID settings too.  For really critical systems, we usually have at least 4 separate environments - dev, pre-prod, prod-A and prod-B.  Dev can be small, but the others are sized the same as production.  For **really, really critical systems**, add in a few more environments for QA and different development work areas.  If you don't have these different environments, it is time to provide a written report and estimate to the decision makers so you can get them. If there isn't money for these, then the systems really aren't that important.

In fact, I was not clear enough. This is the computer my wife use... And it has to run 365/24... Otherwise..... 
As at work we use the same software RAId and LVM style of machines, I used it for the home PC... (the array was initially constructed with 160 Gb disks and was later expanded to 320 GB disks when space was becoming scarce. This was done without "downtime" and without any backups. this just to show how confident I am with this kind of setup...)
> 
Are all the HDDs identical, from the same manufacture run?  Sometimes disks with the same part number are not the same internally - I've heard of some disks changing from 512b sectors to 4k and still having the same model number. Unlikely in your situation, but you never know.

Are you using RAID designed/enterprise disks, not cheap consumer level drives that don't have the same instruction set?  These are known to fail when placed into a RAID config.

Actually, in my experience, having a set of same make/model/manufacture batch of disks is a very bad idea. They often fail simultaneously or in close time interval... For this I initially had a Seagate, a Maxtor and a Samsung. I sized the arrays on the smallest of the 3.  The disk are cheap disks as per RAID definition ... Now that I've repalced the Samsung, I've a Seagate with 4k sectors, a maxtor with 512 sectors and the new seagate with 4K sectors. The 4k disks are Fdisk labelled with 512 size sectors and seems to run fine. (the starting cylinder is not the number 1 but the 2048 one... otherwise transparent) As I set up the machine (converted from LVM mirror to md mirror ) in 2010, 4 K disk support was not so common in Linux kernels in Ubuntu long term support software... 
> 
Sorry that I didn't have any real answers, just questions.  I've been running mdadm for  RAID on systems here for about 6 years.  I've lost a few HDDs, but never any data.  I've never needed to restore from a backup, but still have backups created nightly.

I'm a little confused that the system wouldn't boot based on any RAID configuration.  You didn't put the /boot onto RAID. That is definitely not a best practice.  I also think that having the OS on RAID is not a best practice, but that is open to debate. I just know that I do not.

Actually, the /boot *is* on /dev/md0. As it is an ext4 which is laid above md0, I am able to access with grub the /boot event if the array is totally broken. We use it all the time at work and it has been proven successful many many times.. This is also the reason why I've put the GRUB mbr on every disk. The system should be able to boot whatever disk is left functioning. 
Frankly, I've run systems with system disk on RAID since,say, 1989 or so. Whatever software the OS is. HP-UX, Aix, Solaris or *BSD*,  Linuxes.... you name it.  
How come this is a bad idea ? And for what reasons ? The goal here is to be able to boot no matter what. And fix the flaw with a working system (or delay the fix for a few days 'til the parts show on the mailbox).
I have a separate LV for /home which is replicated on the laptop we have once in a while and I make dump every month. 
> 
I'll take a stab at your questions.  

I've never had mdadm "automatically recognize" a **new disk** should be used in a RAID set. I've always had to manually tell it which partition to use for a specific RAID device. After told and the disk gets marked, it does become automatically recognized.

Yes, you're right. It was a shortcut I used as I tired myself typing... 
I Fdisk the new disk, then mdamd added it partition by partition onto corresponding arrays with my nice little hands :D
> 

In a degraded array, a failed disk is automatically removed. I must not understand the question. Sorry, I'm a little slow this morning.
 
This behavior seems to have changed. A few years ago I had to do a  mdadm -r <failed disk> then an mdadm -a <new disk>. This is what I attempted yesterday. 
> 
grub has changed over the years and I'm hardly an expert. For this question, you probably need to specify to 3-4 levels the exact version of grub involved. It is likely that asking this question on the grub support forums will be necessary.

Anyway, I hope I haven't shown my ignorance too much today and some others will add and correct what is wrong.

If the system needs to keep running *at whatever costs*, then you should have at least 2 production servers running it located in different physical data centers at least 500 miles apart.  Time to get the budget to make that happen to reduce the outage risk. This design can handle both failover and disaster recovery, so in the long term, it is cheaper.
Well my wife will complain... She likes our home a lot and buying/renting another one 500 miles from here wont please her, I guess ... 
Here I use a really solid and field proven technology to maximize as much as I can the sturdiness of her machine. But I've to keep the costs and means to a home level... Not an enterprise level ;-) 
Thanks a lot for having answered me. 
Have a nice day.

---

