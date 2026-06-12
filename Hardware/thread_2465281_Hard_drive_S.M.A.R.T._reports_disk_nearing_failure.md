---
title: "Hard drive S.M.A.R.T. reports disk nearing failure ... but"
date: 2021-07-28
forum: Hardware
---

### Post by michael351 on 2021-07-28
I use 'gsmartcontrol' to monitor my disks. One drive is reporting near failure (see output below).

I backed up the drive, reformatted it and then put back in service curious how long it will last.
The drive reported 2,071 reallocated sectors which is roughly a megabyte in size.

After a month, the drive is still running fine - I have even used it as a running drive (data duplicated) with no issue.

Given that only a megabyte of drive space out of 2 TB is bad, perhaps S.M.A.R.T is too conservative?

Of course I won't rely on this drive, just curious if others have had drives report as "failed", but continue to work just fine.

I decided to wipe the drive by writing to all sectors to see what happens (i.e. dd if=/dev/zero of=/dev/sdb oflag=seek_bytes seek=400000 status=progress &) by forcing it to read/write 
to all sectors. It's running now.



=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Re
Device Model:     WDC WD2000FYYZ-01UL1B0
Serial Number:    WD-WMC1P0155372
LU WWN Device Id: 5 0014ee 0039b2d16
Firmware Version: 01.01K01
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Jul 28 08:08:05 2021 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM level is:     128 (minimum power consumption without standby)
Rd look-ahead is: Enabled
Write cache is:   Disabled
ATA Security is:  Disabled, NOT FROZEN [SEC1]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

---

### Post by rsteinmetz70112 on 2021-07-28
Is the number of reallocated sectors increasing? I have a drive that has been reporting the same number of reallocated sectors for over a year.

---

### Post by michael351 on 2021-07-28
No. Not at all. It is the same number for a month now....2,071.
I am trying to force the issue (using dd) to see if I either break the drive or it is stable at this state.

Is the drive useful in this state? In the past before S.M.A.R.T., a bad drive usually started to make noises (clicking, etc.). This one is silent and is running great.

---

### Post by QIII on 2021-07-28
"That right front tire has a slow leak.  I wonder if it'll make it to Toledo."

I'd buy a new right front tire rather than waiting to see.  I would recommend the same for a disk with bad sectors.

---

### Post by TheFu on 2021-07-28
All storage fails. We just want it to fail AFTER we are done using it.  SMART is telling you that the drive isn't safe to use. Of course, you are free to ignore those warnings and may or may not experience data loss by doing that.

How much is your data worth?  If you don't care, keep using it.

Whenever any storage has more than 10 bad sectors/blocks, I remove it from use.  My data is more important than anything else.

Plus, if a program that alters data happens to use one of those bad blocks, what do you think could happen to all data written by that program? 
Hint: it wouldn't be good.

But it is your system. Do whatever you like.  There are lots of times when programs and system checks don't actually see problems, so all we really know is that there are at least X,YZA issues on that device.  Could be many more.

---

### Post by cryptearth on 2021-07-30
> **michael351 said:**
> [...] just curious if others have had drives report as "failed", but continue to work just fine. [...]
Yup, happened to me.
I run a 5 disk raid5 on my onboard fakeraid - and already had 3 disks failed. I pretty much did the same just out of pure curiosity: Connected them to a 2nd system and ran dd if=/dev/zero of=/dev/sdN over them. Two of the three did just fine - but the third failed for good (it had about only half the speed and made some audible clicking noises during the run.
They were reported as failed by the raid utility - and before zeroing them windows reported them as only about 700gb useable space out of 3tb. But after a full zero run they magically became good again. Of course I don'T "trust" these drives and don't really rely on them - but as I run them in a 8 disk dual-redundancy array it doesn't even matter if both fail at the same time as the array would still work - although in a extreme risky state.
SMART wasn't really updated as for some reason the fakeraid didn't bothered to care about it - so it seem to that all the issues were recorded in meta data cleared by the zeroing run.

So - yea, SMART is designed to report some basic data to indicate about upcomming failure - but also rely on the drive's firmware and controller correctly updating it. If some weird fakeraid stores some metadata on the disk itself instead of the small chip on the controller board which can be cleared/reset by a simple wipe ... it's pretty much useless. All it's telling you is: The drive seem to fail in the near future - don't rely on it anymore. But if you use it in a (multi-)parity raid anyway with a good filesystem like ZFS which is able to detect and repair bad blocks I would only start to worry about if you start to hear some noises from the drive indicating physical failure.

---

### Post by TheFu on 2021-07-30
FakeRAID has only 1 use. Use either SW-RAID or HW-RAID if you need it on Linux systems.  FakeRAID has all the negatives of SW-RAID and all the negatives of HW-RAID. Avoid FakeRAID unless you absolutely must have RAID on a dual-boot system with Windows and Linux.

SMART was added after the USGovt mandated it.  No standards were mandated, just that SMART exist.
One huge customer of typical consumer HDDs found in their use of 500K HDDs over decades of use that SMART data was useful in predicting HDD failures about 78% of the time.  22% of the time, SMART data wasn't useful.

If slamming /dev/zero into a block corrects it, then it wasn't really a failed block.  Badblocks can be used to target specific blocks in a HDD to exercise bit flipping.  A little math is necessary if you can't hit the entire physical HDD with x0000 and xFFFF patterns.  The math involved changes based on the model, block size, number and location of partitions and if advanced volume management is used or not.  There are articles which explain the math.

I've never had any drive recover any blocks by flipping the bit patterns. Not one in about 20 attempts.

People seem to not understand SMART.  The tools we have require 2 steps.
1) Run either a long or short test using smartclt (part of smartmontools package).  Wait until those tests are complete. That could be 2 minutes or 10 hours.
2) Run a report to pull the data created by the last test run using smartclt.

The summary report saying "PASSED" just means that the smart program finished, not that the HDD is fine.  Run the tests and look at the huge table of attribute values returned.  Every GUI tool I've see on Linux has dumbed down the numbers as to be next to useless, IMHO.

---

### Post by cryptearth on 2021-07-31
> **TheFu said:**
> FakeRAID has only 1 use. Use either SW-RAID or HW-RAID if you need it on Linux systems.  FakeRAID has all the negatives of SW-RAID and all the negatives of HW-RAID. Avoid FakeRAID unless you absolutely must have RAID on a dual-boot system with Windows and Linux.
Yea, had to learn that the hard way. Back then I wasn't even aware of differences between hardware-level raid, software raid, fakeraid, and multi-partition/-disk volume FS like ZFS or BtrFS.
Today, as I'm aware of all that stuff, I kind of question: Why this not-so-useful-stuff was put on even the most basic consumer-grade boards ... and why it's still some marketing-BS still used today?
Yes, as I just recently learned: It's still hard to deal with local attached storage in a dual-boot environment. Sure, one could go with single-drive exFAT - but a multi-disk spanning volume? That's another story. Although both Linux and Windows do offer some solutions I haven't found one that can be used on both yet. And even commercial products are rather scarce.
As for the history of smart and what's it all about - I honestly know only very little about it. I just know from personal experience: When smart indicates some issues it's either wrong and just some values are out of some ranges set by some developer of the software used to analyze it - or is pretty much on spot that you get that final warning to get your data off of the drive - as it will fail within short timespan.

---

### Post by TheFu on 2021-07-31
exFAT should only be used for flash storage and only for devices that offer it and FAT32.  It should not be used on Linux except for data that doesn't need any permissions AND which must be physically connected to a Windows computer.  If the data is only connected to Linux, exFAT is useless.

Flash storage for Linux-only should use f2fs.  SSD or spinning disks for Linux should use xfs or ext4 with few exceptions.

I'm not a fan of dual/triple/quad booting.  There are some many issues with it that the hassles are too great to bother.  I use virtual machines all the time, however.

Seems the OP has left this discussion.

---

### Post by michael351 on 2021-08-05
I'm still here - fascinated by the conversation and learning.

The drive in question is running fine. No increase in errors. The disk just works. Failure was predicted in "24 hours" - did not happen. I don't trust the disk and all data on it is backed up so no worries. I will keep using it to see how long it goes. I'm not writing to the disk, just reading from it. We'll see.

---

