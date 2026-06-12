---
title: "Ubuntu install causes blue screen in Windows on Toshiba NB200"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by sdcmunich on 2009-08-17
Dear all,

I have read about a possible problem when installing Ubuntu Netbook Remix on a Toshiba NB200 (aka NB205 in the US), causing a blue screen when booting into Windows after the installation.
But I haven't been able to understand what was the cause of the problem - is it due to repartitioning, to GRUB, or to something else?

Any explanation about that issue would be appreciated.

As background: the NB200 comes with a (nearly) 80 GB XP partition, a (nearly) 80 GB so-called media partition, also containing recover data, and a hidden partition which I assume is used to restore data.

What I was planning to do was to use gparted/Partition Magic/whatever works to decrease the size of the NTFS partitions and free some space for Ubuntu. Then, install UNR as dual-boot.
If installing GRUB on the main disk turns out to be a problem, a possibility could also be to install GRUB on a USB stick/SD card.

/sdc

---

### Post by Mark Phelps on 2009-08-17
You didn't say, but if your netbook came with Vista, do NOT use GParted or the Ubuntu installer to shrink the Vista OS partition.  Doing so runs the risk of corrupting the OS, rendering it unbootable after that.  That is typically fixed by booting from a Vista DVD and running Startup Repair a few times, but since you have a netbook and (I presume) no DVD drive, that won't help you.

Use the Vista Disk Management utility to shrink the OS volume.

---

### Post by sdcmunich on 2009-08-17
Hi Mark,

Thanks for your answer.
The netbook comes with XP, not Vista - fortunately.

But in any case: is the problem only with the OS partition, or with any partition on the disk? I was actually thinking about shrinking the data partition, not the XP system partition.

Which software is able to shrink the partition without breaking anything? I have Partition Magic 8, but this is probably too old to be able to do anything specific for Vista. I have no copy of Vista around, so I can't use Vista Disk Management - unless there is a way to run it using an evaluation CD for example.

/sdc

---

### Post by sdcmunich on 2009-08-18
In fact, I can see that the recovery partition is considered by gparted as a Vista partition.

The question for me is: will resizing the data partition (NTFS, non-bootable) break anything?
I always have the option to install GRUB on a USB stick to be on the safe side.

Thanks for your help!
/sdc

---

### Post by andrew2145 on 2009-08-18
I did not get any error while installing this  in my desktop and laptop. Hope you can also install it without any problem. Please follow all instruction. Thanks

---

### Post by bazmonkey on 2009-08-25
FWIW, this is a legitimate problem.

I just bought an NB205 (in the States), did nothing in XP except connect to a wifi network, installed Netbook Remix, and bam!  Trying to boot XP gives about 6 seconds of splash screen, a split-second BSOD, and a restart.

No idea why.  I left nearly 1GB of free space on the XP partition.  It's no biggie to me b/c it's only there in case of some firmware update or something.

I'll report back if I find something...

---

### Post by The Beanless One on 2009-08-27
Call me weird but I like my XP partition(if only so i can run StarCraft native and diskless). I was very sad :cry: when all atempts to boot it ended in spits second BSOD followed by a restart. Does anyone know how to fix the boot on the the XP partition w/o a external disk drive? I realize this is not an XP help forum but it would be good to find a way to duel boot Toshiba-205.

---

### Post by Mark Phelps on 2009-08-28
> **The Beanless One said:**
> ...I realize this is not an XP help forum but it would be good to find a way to duel boot Toshiba-205.
Please don't hijack existing threads for other problems.  This thread is about problems with an Ubuntu install not about fixing XP boot problems.

Please start a new thread regarding your problem.

---

### Post by fiddler616 on 2010-06-07
> **Mark Phelps said:**
> Please don't hijack existing threads for other problems.  This thread is about problems with an Ubuntu install not about fixing XP boot problems.

Please start a new thread regarding your problem.

The Beanless One's problem is directly related to an Ubuntu install: an Ubuntu install has rendered has gone awry and hosed his XP partition, and is therefore markedly relevant to this discussion. And here I am with the same problem (but with an NB305), reading through the thread, saying, "Yes, this is it!" And then the forum police came out and effectively ended the thread before a solution was posted.

---

### Post by m0nstersnatch on 2010-09-18
> **sdcmunich said:**
> Dear all,

I have read about a possible problem when installing Ubuntu Netbook Remix on a Toshiba NB200 (aka NB205 in the US), causing a blue screen when booting into Windows after the installation.
But I haven't been able to understand what was the cause of the problem - is it due to repartitioning, to GRUB, or to something else?

Any explanation about that issue would be appreciated.

Hello, I had the same experience with the Toshiba Satellite M70 and now I am looking for a hint on how to boot the XP installation AND the Ubuntu Netbook Edition without the BSoD. 

Has anyone a clue how to do so ?

---

