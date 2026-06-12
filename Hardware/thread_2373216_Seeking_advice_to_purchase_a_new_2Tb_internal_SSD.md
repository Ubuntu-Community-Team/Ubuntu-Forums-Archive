---
title: "Seeking advice to purchase a new 2Tb internal SSD"
date: 2017-10-04
forum: Hardware
---

### Post by satimis on 2017-10-04
Hi all,

Seeking advice to purchase a new 2Tb internal SSD

Host - Ubuntu 16.04 desktop
Oracle VirtualBox

My 1Tb SSD hard drive, which has been running for more than 6 years without problem, is now nearly full.

$ sudo smartctl -i /dev/sda```

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-59-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SiliconMotion based SSDs
Device Model:     TS1TSSD370
Serial Number:    C077240048
Firmware Version: N1114H
User Capacity:    1,024,209,543,168 bytes [1.02 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Oct  4 12:49:47 2017 HKT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

I assume TS referring to Transcend, the manufacturer.  I'm prepared upgrading it to a 2TB internal SSD.

On Internet searching I found:-

1)
Crucial MX300 2TB CT2050MX300SSD1 2.5" SATA 3 6Gb/s
Crucial MX300 2TB SATA 2.5" 7mm (with 9.5mm adapter) Internal SSD
[http://www.crucial.com/usa/en/ct2050mx300ssd1](http://www.crucial.com/usa/en/ct2050mx300ssd1)

and

2)
SanDisk Ultra 3D SSD 2TB SDSSDH3-2T00-G25 2.5" SATA3 6Gb/s (Solid State Drive, SSD) 
SANDISK ULTRA 3D SSD
[https://www.sandisk.com/home/ssd/ultra-3d-ssd](https://www.sandisk.com/home/ssd/ultra-3d-ssd)


The price of "SanDisk Ultra 3D SSD 2TB SDSSDH3-2T00-G25" is about 10% more expensive than that of "Crucial MX300 2TB CT2050MX300SSD1"

Is the quality of Crucial internal SSD reliable?  Please shed me some light.

I'll install the old Transcend 1Tb SSD on my spare PC which is now running a 120GB SSD for Ubuntu 16.04 as OS.  All data are stored on a 2tb WD black label Hard drive.

Comment and suggestion would be appreciated.  Thanks

Regards
satimis

---

### Post by TheFu on 2017-10-04
Why SSD and not spinning rust at 1/3rd the price?  That's my first question.  None of my servers use SSDs. None.  Only have 1 SSD system - a chromebook.  Linux knows how to cache disk storage pretty well.  Is the result really worth the triple costs?  

From my reading, there is basically 1 type of SSD that people use for enterprise applications where reliability matters.  The Samsung 950/960 models.

---

### Post by efflandt on 2017-10-04
I recently ordered a 1 GB Crucial MX300 which should arrive later this week. I have an older PC, but even an old 80 GB Intel SSD on SATA2 was about twice as fast as my 7200 rpm hard drive. In an old SATA1 laptop that SSD was 4x faster than its 5400 rpm drive or about equal to 7200 rpm drive on SATA2. It quite surprised me that the 5400 rpm drive on SATA1 was no faster than a portable external hard drive on USB 2.0.

I am currently running Ubuntu 16.10 (which I know has reached end of support) from 512 GB Crucial M550 mSATA SSD card from a failed laptop in a SATA adapter (still have Ubuntu 14.04 and Win7 on 1 TB hard drive). I use more space than some people because I play Steam games, one of which was a 26 GB download that required 42 GB disk space, and also recently started recording/editing videos. But I need to figure out if 16.04.3 LTS works for me now (earlier 16.04 would not display any text during boot, so no BIOS splash or grub menu, until something did graphics) or whether to upgrade to 17.04 (with everything backed up in case upgrade fails).

I have had hard drives fail (including after 3 years in current PC), but never had any flash fail (from the time of CF) "yet". But I stick to name brands for any flash memory or SSD's. My current (WD) hard drive chatters like crazy when rarely booting Win7 imaged/cloned from the failed Seagate hard drive (only Linux partition failed at far end of drive) even though smartctl does not show anything wrong. So I may shrink that even more (from Win7 itself) or try Win10 just to have it on the new SSD in case I need it for something.

---

### Post by TheFu on 2017-10-04
I've had an SSD fail.  It just stopped working, period. It was 16 months old. 1 min between the first clue and total failure.  Thankfully, I've had backup religion for years now.  It was a minor inconvenience.

I have had lots of spinning disk failures too, but that's why an 8TB disk is $160 and a 500GB SSD is $160.

I agree that for the running OS, an SSD is useful, but for typical data used by a home user, music, videos, etc, it just doesn't matter.  A 5400rpm cheap disk is more than fast enough for bluray movies.

---

### Post by QIII on 2017-10-04
I won't presume to tell you bow to spend your money, but to give you something to consider...

A smallish SSD is great for running the OS,  but a large one like 2TB is both impractical and potentially dangerous to your data.  Consumer grade SSDs are subject to charge leakdown.  Their internal structure does not provide a lot of insulation, so the charged cells indicating a "1" can have their charge bleed down below the threshold that indicates "1" and become "0".  When that happens enough, data becomes corrupted.  This process can happen in as little as a few weeks.  Commercial grade SSDs take somewhat longer, but it is inevitable.

Data on iron oxide can last decades.  That sbould be where data is stored.

Get an SSD large enough for your OS and some room to spare.  A 2TB spinner is gar cheaper than a 2TB SSD.

---

### Post by satimis on 2017-10-05
Hi all,

Lot of thanks for your valuable advice.

Before turning to SSD I have been running WD black label spinning HD for prolonged time without trouble.  I'm aware that the cost of a 2TB SSD is about 10 times of the cost of a 2TB WD Blue label spinning HD.  Also I'm aware that SSD has life time.

WD Blue WD20EZRZ 2TB SATA3 6Gb/s /64MB HDD
[https://www.newegg.com/Product/Product.aspx?Item=N82E16822235013](https://www.newegg.com/Product/Product.aspx?Item=N82E16822235013)


My interesting turning to SSD is for speed, booting up very fast.  Also I'm running Oracle VirturalBox here.

My daily working PC
================
OS-Ubuntu 16.04 and VMs are running on SSD, both booting up very fast.


My spare PC
==========
OS-Ubuntu 16.04 is running on SSD and VMs on WD 2TB black label spinning HD.  The OS boots very fast but the VMs are relatively slow.


After summing up your advice I have another idea.  

1)
Get a HGST Enterprise SAS Ultrastar 7K6000 2TB 7200rpm, 128MB 12Gb/s HDD HUS726020AL5210 (7x24), spinning HD 

HGST Ultrastar 7K6000 HUS726020AL5210 (0F22799) 2TB 7200 RPM 128MB Cache SAS 12Gb/s 3.5" Enterprise Hard Drive Bare Drive
[https://www.newegg.com/Product/Product.aspx?Item=N82E16822146063](https://www.newegg.com/Product/Product.aspx?Item=N82E16822146063)

OR

2)
a WD Gold WD2005VBYZ 2TB SATA3 6Gb/s /128MB Datacenter 7x24 HDD

WD Gold Enterprise-Class Hard Drive
[https://www.wdc.com/products/internal-storage/wd-gold-enterprise-class-hard-drive.html#WD121KRYZ](https://www.wdc.com/products/internal-storage/wd-gold-enterprise-class-hard-drive.html#WD121KRYZ)


Move all data, daily working and old data, from the SSD to it, only retaining the OS and VMs on SSD.  In such arrangement I could spare about 300GB space on SSD.

I haven't used HGST spinning HD before.  What about its quality?

Comment and advice would be appreciated.

Regards
satimis

---

### Post by QIII on 2017-10-05
"Lifetime" isn't really the issue when it comes to leakdown.  SSDs have service lives nearly as long as hard drives now.  They are just not good for long-term storage of files just yet.

---

### Post by satimis on 2017-10-05
> **QIII said:**
> "Lifetime" isn't really the issue when it comes to leakdown.  SSDs have service lives nearly as long as hard drives now.  They are just not good for long-term storage of files just yet.

Thanks for your advice.

A further consideration if just for storage I could get a "WD Blue WD20EZRZ 2TB SATA3 6Gb/s /64MB HDD, 5400 rpm".  Its price is less than half of a "WD Gold WD2005VBYZ 2TB, 7200 rpm".  The only difference is speed.  For data storage I don't think there is much benefit ?

Regards
satimis

---

### Post by TheFu on 2017-10-05
For faster VMs, dump virtualbox.  Switch to KVM and/or containers.  I limit the amount of storage for each VM to 25G.  If they need more, then NFS is used.

For risk reduction against failing disks, there are 2 things needed.  Clustered storage (use Sheepdog) and versioned backups.

Another option is to use ZFS and setup some smaller SSDs as cache devices.  I've never used this on Linux.

But if you just want this issue to go away as quickly as possible without huge architecture changes, get some SSDs.  It is your money after all.

I really just wanted to ensure you are making decisions with as many alternatives considered.  Sounds like you have some good reasons for any of these options, though my needs would never follow the huge SSD method.  Inside a business, things are completely different.

---

### Post by satimis on 2017-10-05
> **TheFu said:**
> For faster VMs, dump virtualbox.  Switch to KVM and/or containers.  I limit the amount of storage for each VM to 25G.  If they need more, then NFS is used.
Thanks for your advice.

Actually before running virtualbox I was running kvm and kvm qemu.  I started virtualization on the latter.  I may find a chance to come back if having time.

> 
For risk reduction against failing disks, there are 2 things needed.  Clustered storage (use Sheepdog) and versioned backups.

Another option is to use ZFS and setup some smaller SSDs as cache devices.  I've never used this on Linux.

But if you just want this issue to go away as quickly as possible without huge architecture changes, get some SSDs.  It is your money after all.

I really just wanted to ensure you are making decisions with as many alternatives considered.  Sounds like you have some good reasons for any of these options, though my needs would never follow the huge SSD method.  Inside a business, things are completely different.
The configuration of my daily working PC;
Drive A - 1TB SSD running Ubuntu 16.04 desktop, VirtualBox/VMs and data storage
Drive B - 1.5TB WD black label HD - for duplication of the data on Drive A and copy of VM images.

In case one drive broken down I still have the data and VM images.

Periodically I rsync the data to my spare PC but not VM images.

Now my decision will be purchasing a "WD Blue WD20EZRZ 2TB SATA3 6Gb/s /64MB HDD, 5400 rpm" hard disk, just for storing the data on Drive A.  In doing so it'll save lot of cost.


Edit
====
IIRC guests on KVM can be exported and imported to Virtualbox and vice versa ?


Regards
satimis

---

### Post by mastablasta on 2017-10-05
booting matters only if you keep turning off the PC. there is no need for that. WMs can save the state they are in. they do not need to be booted. for WM i think RAM and it's usage is more important than fast drive. add to that a more efficient virtualisation techniques and you should not need SSD.

Blue is meant for home use and as system disk, Black has better & faster access + is supposedly also more reliable than blue (but hard to notice in tests), Red is slower but more reliable, green is for data storage (specifically data that s relatively static (e.g. pictures, videos...).

as with everything, the newer version of an older model is more reliable than the latest new model.

---

### Post by satimis on 2017-10-05
> **mastablasta said:**
> booting matters only if you keep turning off the PC. there is no need for that. WMs can save the state they are in. they do not need to be booted. for WM i think RAM and it's usage is more important than fast drive. add to that a more efficient virtualisation techniques and you should not need SSD.

Blue is meant for home use and as system disk, Black has better & faster access + is supposedly also more reliable than blue (but hard to notice in tests), Red is slower but more reliable, green is for data storage (specifically data that s relatively static (e.g. pictures, videos...).

as with everything, the newer version of an older model is more reliable than the latest new model.
Hi,

Thanks for your advice.

I have 32G RAM onboard for the daily working PC and 8G RAM onboard for the spare PC.

I couldn't find WD Black label 2TB HD here.  Alternatively I can purchase a "WD Gold WD2005VBYZ 2TB SATA3 6Gb/s /128MB Datacenter 7x24 HDD".  Its price is much cheaper than that for a 2TB SSD.

I'm now planning to build a new PC running "AMD Ryzen 7 1700X YD170XBCAEWOF 8 Cores/16 Threads, 3.8GHz,20MB Cache, Socket AM4 CPU" with 64G RAM onboard.

Regards
satims

---

### Post by TheFu on 2017-10-05
There is a reason WD doesn't make huge Black HDDs.  They can't price it in a way to meet the 5 yr warranty costs.  That really should be a hint - don't expect 5 yrs from huge disks.  Of course, lots of people do get lucky.  I have some 320G disk that are over 12 yrs old - still spinning - still working.  I don't use them for anything important and never as primary storage.  Tracking the age and SMART data for disks is a "whole thing" around here.

---

### Post by satimis on 2017-10-05
> **TheFu said:**
> There is a reason WD doesn't make huge Black HDDs.  They can't price it in a way to meet the 5 yr warranty costs.  That really should be a hint - don't expect 5 yrs from huge disks.  Of course, lots of people do get lucky.  I have some 320G disk that are over 12 yrs old - still spinning - still working.  I don't use them for anything important and never as primary storage.  Tracking the age and SMART data for disks is a "whole thing" around here.

Hi,

I'm the lucky folk having WD Black Label HDs 1TB, 1.5TH and 2TB running for prolonged time without problem.

What will be your suggestion on alternative for WD black label HD?

Seagate? HGST? Toshiba?

OR
WD Gold WD2005VBYZ 2TB SATA3 6Gb/s /128MB Datacenter 7x24 HDD ?

I have bitter lesson on Seagate HD, broken down within 1 year.


Re your suggestion swtiching to KVM on #9 above.  I have a spare old 120G SSD on shelves.  After purchasing the new 2TB spinning HD, I'll install the 120G SSD on my daily working PC to test KVM with the guest images stored on the new 2TB HD.  I have several Dockers running on VMs of VirtualBox.  I'll try to export them and re-import their images on KVM.  I have no idea whether it works?  

I'll start another thread on Virtualization Forum later.

Regards
satimis

---

### Post by TheFu on 2017-10-05
Containers are portable across Linux, provided you don't change CPUs drastically.  That's sorta the point.

Use qemu-img to convert from vdi to qcow2 storage.

I'd avoid Seagate too.  Backblaze publishes their quarterly HDD failure reports ... er ... quarterly.  Look those over for the failure rates based on the sizes.  I haven't looked at 2TB disks in some time, but I think HGST was significantly longer lasting than the other choices.  You might have to go back a few years in their data postings to see any 2TB disks.

---

### Post by gordintoronto on 2017-10-05
As a comment, having your backup disk in the same box as your primary disk means that you will have no backup in certain scenarios. What if a burglar steals your computer? What if a small fire destroys it? How about water damage from a broken pipe?

I backup across the network to a netbook with a big drive. At least my data is in more than one room.

---

### Post by QIII on 2017-10-05
I have a couple of HGST drives I bought as "economy" drives a few years ago.  The first time I read the dependability reports I was flabbergasted at their far superior dependability!

---

