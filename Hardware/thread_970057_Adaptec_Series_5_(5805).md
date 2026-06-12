---
title: "Adaptec Series 5 (5805)?"
date: 2008-11-03
forum: Hardware
---

### Post by McLogic on 2008-11-03
I'm looking for anyone who is running one of the newer "series-5" (since march 2008) high-end Adaptec cards, to find out about their experience. I'm considering running the 5805 on my desktop machine.

Is the card working? 
Do you boot from it?
How did you install the Adaptec Storage Manager software (only RPM's)?

The series 5 cards are:
52445
51645
51245  
5805
5085  
5445  
5405

A nice way to spend $650:
[http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/performance/SAS-5805/](http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/performance/SAS-5805/)

Their "support" page is insulting; their "strong Linux commitment" means RPM-only and officially for just the big corporate distros (RHEL, SEL).

[http://www.adaptec.com/en-us/_common/linux](http://www.adaptec.com/en-us/_common/linux)

---

### Post by btiefert on 2008-11-04
I have the 5805 running on my system with 8.10, and it works like a champ right out of the box.   The 8.04 Live CD installer recognized the device and served up the logical drives just fine, so I was able to install Ubuntu, boot partition and all, right on the raid array.

I've had this setup running for a little more than a week.  Unfortunately I have not yet tackled installing the management software, so I'm stuck with old school BIOS array management for now.   I tested throughput using HD Tune on my old Windows install and sustain 480 megaBytes / sec, just as predicted in the excellent TomsHardware review.   This is with 5 Western Digital 1TB RE3's.    I have three more drives on order and will play with the live raid expansion features.

I'll try to post back with my experiences with the management software once I get it running on Ubuntu.  My fallback plan is to install CentOS for binary compatibility, as this box is little more than a NAS.   Let's hope it doesn't have to come with that.

---

### Post by voodooless on 2008-11-05
Well, we are currently struggeling with an Adaptec RAID 51645 on 8.10 (also had 8.04LTS) server, and previously with an ICP5165BR (older model), using 16 15K SAS disks.

Performance is just not what is expected, not at all. random writes with small blocksizes don't go beyond 20 MB/sec, and the array (raid 50 with 12 disks) is currently dooing a sequentual read of 70 MB/sec. And if I'm lucky, it will read 350 MB/sec (seq). Performance of the ICP was about the same. I would expect a sequential read of more than 1GB/sec..

This is just ridiculous..

We previously had Opensolaris installed, and it rocked in IO speed. To bad the file system and OS ware terribly unstable.

So not I'm looking to a reason for this terrible performance, because this can't not normal.

---

### Post by btiefert on 2008-11-05
Voodooless:  Sorry to hear that things aren't working out with your 51645 - it looks like a nice card on paper.   I think the difference between my experience and your experience is that you have higher expectations of your card, (and probably rightly so!)

For those considering a purchase - please realize that although I am very pleased with my 5805 (same card, fewer ports), I don't have a lot of modern RAID experience to compare it with so what blew me away might not be that impressive anymore.   It is, however, a HUGE step up from on-board SATA JBOD.

Voodoo, can you tell me which testing suite you used for your random write testing?   I'd like to compare apples to apples, even though I have slower drives, and see how my 5805 lines up, quantitatively.

Thanks!

---

### Post by voodooless on 2008-11-06
> **btiefert said:**
> 
Voodoo, can you tell me which testing suite you used for your random write testing?   I'd like to compare apples to apples, even though I have slower drives, and see how my 5805 lines up, quantitatively.

I used IOmeter for testing. Also did some simple test using HDparam. It gives about 380 MB/sec. I just put in a Gentoo live CD, and it already gives me 580 MB/sec. Still not what I expect, but much better.

---

### Post by voodooless on 2008-11-06
Testes some more with Gentoo. Turns out that it is not a lot better.

Random read with 8K blocksize: two disks in mirror are exactly as fast as 12 disks in RAID10... This just can't be right..

Same goes for sequential read with 8K blocksize, the mirror is exactly as fast as the 10 disk raid10

---

### Post by voodooless on 2008-11-10
Now testes Ubuntu 8.04, 8.10, Gentoo, CentOS5 and SLES10SP2.

All of them give about the same performance, and it's rubbish..

So I installed an eval version of Server 2008 Enterprise 64-bit and also ran the same tests on this machine. Guess what: these results are what you would expect from such a system. Most results with small request sizes were of a magnitude of 10 better than the Linux systems!

So clearly there is something wrong with the Adaptec linux drivers...

So, my advice: Stay away from this for a while, at least upto the moment they fix this.

---

### Post by Madman666 on 2008-11-20
> **btiefert said:**
> I have the 5805 running on my system with 8.10, and it works like a champ right out of the box.   The 8.04 Live CD installer recognized the device and served up the logical drives just fine, so I was able to install Ubuntu, boot partition and all, right on the raid array.

I've had this setup running for a little more than a week.  Unfortunately I have not yet tackled installing the management software, so I'm stuck with old school BIOS array management for now.   I tested throughput using HD Tune on my old Windows install and sustain 480 megaBytes / sec, just as predicted in the excellent TomsHardware review.   This is with 5 Western Digital 1TB RE3's.    I have three more drives on order and will play with the live raid expansion features.

I'll try to post back with my experiences with the management software once I get it running on Ubuntu.  My fallback plan is to install CentOS for binary compatibility, as this box is little more than a NAS.   Let's hope it doesn't have to come with that.

Hello, I have a question on the 5805 as I have one myself connected to 2x Samsung 750Gb in RAID0 and 5x WD RE3 1TB in RAID5.
They are all 3.0 Gb/s SATA2 disks. Sometimes however the controller sees 1 HDD as 1.5GB/s ? 
This happens at random, sometimes it's a Samsung, sometimes a WD.
Rebooting solves and triggers the issue.
So out of 10 reboots it happens 1 time.
I have 2 Adaptecs 5805, both have the same issue. Tried another PCI-E slot, tried other cables, tried other HDD. NO change. Issue  keeps occuring. Could anyone verify this ? To see the speed negotitaion on boot (pre-post) you can turn this on in the controller settings(CTRL-A). Default=disabled ;-0
Of course it's a random issue, so rebooting once or twice will probably not be enough. 10-20 reboots will more reliable.
Strange, isn't it ?:confused: Although this issue the speeds are impressive.

---

### Post by McLogic on 2008-11-25
> **btiefert said:**
> I have the 5805 running on my system with 8.10, and it works like a champ right out of the box.

It is good to know that the board works with the regular install CD.

> **btiefert said:**
> I've had this setup running for a little more than a week.  Unfortunately I have not yet tackled installing the management software, so I'm stuck with old school BIOS array management for now.

That is really sad. If I pay $550 for a card, I don't want to have to use the BIOS to set up my RAID. I need to be able to get array status w/o rebooting, etc.


> **btiefert said:**
> I have three more drives on order and will play with the live raid expansion features.

I'm really interested in your expansion feature experience.

> **btiefert said:**
> I'll try to post back with my experiences with the management software once I get it running on Ubuntu.  My fallback plan is to install CentOS for binary compatibility, as this box is little more than a NAS.   Let's hope it doesn't have to come to that.

Let us know if the management software is working for you. The fact that people were having trouble with the Java management software is what made me put the purchase on hold and buy a cheap-o Silicone Image card as a temporary solution.

---

### Post by ma10 on 2008-11-28
I bought a brand new Adaptec 5405 and it's been running since June (approx $140~) Also, recently just picked up a refurbished version of it's predecessor, the ICP 5165 (approx $300).

Both are using the same brand/model of hard drives. The Adaptec 5405 always picks up the drives as SATA 3Gb/s whereas the ICP 5165 is showing the same drives as 1.5Gb/s. Not sure if that is because the ICP 5165 hasn't been configured properly, due to it's used condition or simply of it's older model status...

I'll do some more testing with the ICP 5165 and see if I can get it to change transfer mode to 3Gb/s like it should do.



Anyways, to get the Adaptec Storage Manager working on ubuntu:

1. Download the required/latest rpm from Adaptec downloads page e.g.


[INDENT][ Adaptec Storage Manager v6.00.17922 for 32-bit Linux and VMware]("http://www.adaptec.com/en-US/speed/raid/storage_manager/asm_linux_x86_v6_00_17922_rpm.htm")[/INDENT]


2. Install the "alien" package from the repository e.g. in a terminal run:

[INDENT]sudo apt-get install alien[/INDENT]


3. in a terminal cd to the location you downloaded the storage manager rpm and run:

[INDENT]sudo alien --scripts asm_linux_x86_v6_00_17922.rpm[/INDENT]


This will convert the rpm to a brand new deb package in the same location that you can then install in the usual manner... ;)

4. Finally, in a terminal, the command to launch storage manager is:

[INDENT]sudo /usr/StorMan/StorMan.sh[/INDENT]


Have fun!! :KS

---

