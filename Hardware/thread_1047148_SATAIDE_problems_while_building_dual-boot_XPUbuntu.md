---
title: "SATA/IDE problems while building dual-boot XP/Ubuntu system"
date: 2009-01-22
forum: Hardware
---

### Post by papalaz on 2009-01-22
I have a problem which I'm curious if anyone else has come across. Until a few days ago I was running Ubuntu on an old 80 Gb IDE HD with an MSI SATA-equipped motherboard; it ran nice and smooth and fast. Then I bought a new SATA HD and decided to play about seeing which configuration was best. Things I wanted to try are:

Install OSs (Ubuntu & XP) on IDE drive, using SATA drive as data storage, and compare performance to installing the OSs on the SATA drive and using the old IDE drive as, for instance, a temporary drive or something (if at all).

Last night I messed about with jumper settings on the IDE HD but no matter what I did I could not successfully get either Windows or Ubuntu installed on that drive. I'm aware of Windows need to be installed first, so I pre-partitioned the drive so that I have a 100 MB boot partition, a 30 Gb ext3 Linux partition (currently empty) then a 30 Gb NTFS partition for XP with a couple of smaller partitions on the end of the drive. I tried to install Windows first but could not get the installation to complete. It gets to reboot time (not exactly sure which one) and then goes into a permanent cycle of rebooting. Obviously I tried the system with only the SATA drive and it installed fine. So it seems to me there's some kind of compatibility issue with IDE & SATA drives when installing OSs. 

I tried the IDE HD as Master & Slave; with both of these jumper settings I could not get a WinXP install CD to load beyond "checking your computer's hardware config". Then I set the jumper to CSEL; whilst I could then apparently read from the install CD ok I could not complete the installation. 

Then out of curiosity I tried to install Ubuntu but even from the Live CD I had trouble getting GParted to recognise the second partition on the IDE HD (Linux partition). 

Anyone had similar compatibility issues with IDE & SATA, and how did you solve them?

Thanks in advance. PL.

---

### Post by papalaz on 2009-01-22
Bump...

---

### Post by stdPikachu on 2009-01-22
Have you tried installing windows on the second partition (currently ext3)? The windows bootloader generally doesn't like having to boot from past the 1024 cylinder boundary.

---

### Post by dabl on 2009-01-22
Yep, I've got an IDE drive and the rest are SATA.  It's a known issue to have problems when you mix them, but it's not exactly the same for every motherboard and BIOS.

On mine, the IDE drive is a "grub magnet" -- the several Linux installers that I have used will absolutely refuse to install grub anywhere other than the MBR of the IDE drive, unless I disconnect it.  I spent a full day one time trying to get Kubuntu to do otherwise, and failed.  Of course after installation, I can always use grub to set up grub on another MBR.

Another thing I noticed when I recently built a dual boot system on an Asus P5Q Pro motherboard, with only a single SATA drive, was that Windows XP would not install (couldn't see the hdd) unless I set the SATA mode to "Legacy IDE".  Linux was happy with AHCI mode or Legacy IDE.

Usually, for IDE channels in BIOS, you want the channel set to "Primary Master", and you want the hdd jumpered as "CS".

HTH.

---

### Post by papalaz on 2009-01-23
stdPikachu:

Last night I disconnected the IDA drive, erased the SATA and installed Windows into a 5Gb NTFS partition (sda1). Then (and this is part of the overall experiment - I have read that Linux performs best as close to the start of the disk as possible) I moved the NTFS partition to the right, inserted a 30 Gb ext3 partition (sda3) and a 100 Mb ext2 boot partition (sda2) (not used as yet). I installed Ubuntu into sda3, also specifying sda3 for the bootloader (as I say I haven't yet used the separate boot partition). When I rebooted it went straight into Windows - no Grub boot menu. I guess there's an incorrect entry in Grub, although I'm a bit surprised that the install process doesn't automatically take care of that itself. I played around with the Windows entry in Grub for a while but couldn't get it to do anything except boot straight into Windows. (Again, IDE HD is disconnected). 

I'm just in the process of printing off a load of Grub documentation so I can play around with that too (you know how it is; you start one thing and before you know it you're doing a dozen!)

So it seems that Windows works fine after its partition has been resized, moved and otherwise bashed about by GParted, which is good to know. And wouldn't this also suggest that the 1024 cylinder boundary thing also doesn't affect the operation of Windows?

dabl:

Thanks for the info, I'll take another dig around my BIOS because I don't recall seeing anywhere the option to change Primary/Seconday Master/Slave. I'm pretty sure I can use the IDE drive as a secondary storage drive without a problem but that's kind of admitting defeat - I've never been a fan of that... 

I also noticed last night, after disconnecting the IDE drive but before erasing the SATA HD, that the Windows installer saw only unallocated space despite there being a number of ext3 & NTFS partitions in existence on the SATA HD. Not sure if that was because of the SATA mode being set incorrectly, that's something else I can look at. It was ok after I allowed the Windows installer to create its own partition after erasing the whole drive with a GParted LiveCD.

---

### Post by stdPikachu on 2009-01-23
> **papalaz said:**
> When I rebooted it went straight into Windows - no Grub boot menu. I guess there's an incorrect entry in Grub... (Again, IDE HD is disconnected).

If the GRUB prompt isn't coming up (or any other errors for that matter), chances are your GRUB boot block is missing from the hard drive - either because your previous boot block was on the PATA drive or because a windows install overwrote it.

My usual partitioning scheme for a dual boot has a 32 to 128MB sda1 boot partition, then the windows partition, then any linux ones. I stick with it because it's the only layout I've never had problems with when I shift discs between computers :)

In reality, discs usually perform best at random access when they're in the middle, and best at sequential data access at the start. IMHO the difference is negligible and it's not worth the headache of juggling partitions in order to make up for windows' shortcomings in this regard. If IO really is important, it deserves at least its own hard drive.

> **papalaz said:**
> So it seems that Windows works fine after its partition has been resized, moved and otherwise bashed about by GParted, which is good to know. And wouldn't this also suggest that the 1024 cylinder boundary thing also doesn't affect the operation of Windows?

Possibly, but I gave up fighting it years ago. But I think GRUB does something clever with the chainloader to help windows these days, Maybe I'm just too much of a dinosaur (had to stop using Debian as I didn't want to grow a beard), but thought it might be worth a shot ;)

---

