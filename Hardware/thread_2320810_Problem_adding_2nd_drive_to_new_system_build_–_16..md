---
title: "Problem adding 2nd drive to new system build – 16.04 LTS (final beta)"
date: 2016-04-17
forum: Hardware
---

### Post by Chris_Read on 2016-04-17
I am trying to re-use a retired but lightly used 3TB HDD as a second drive on my desktop.  The boot drive is a small SSD,  The 3TB disk is visible to the BIOS but does not appear in /dev.  

Here is the history:

 
 
 1. I installed the disk drive into the system and booted.  The drive was visible in the BIOS and appeared as /dev/sdb.
 
 
 2. I removed all of the old partitions and made a single partition using fdisk.  That created /dev/sdb1
 
 
 3. I zeroed out all of the data using “dd if=/dev/zero of=/dev/sdb1”  The job ran for about an hour and finished without error.
 
 
 4.  I tried to build a file system using mkfs.ext4, but got an error saying the file system was in use. After checking for any processes that might be using /dev/sdb and not finding any, I restarted the system.
 
 
 5.  Again, the drive showed up in the BIOS, but this time, after a very long boot sequence, it did not appear in /dev at all.
 
 
 6.  Looking in dmesg, I saw the following:
 
 
 [    6.043807] ata3: link is slow to respond, please be patient (ready=0)
 [   10.691768] ata3: COMRESET failed (errno=-16)
 [   16.051731] ata3: link is slow to respond, please be patient (ready=0)
 [   20.699669] ata3: COMRESET failed (errno=-16)
 [   26.059654] ata3: link is slow to respond, please be patient (ready=0)
 [   55.739425] ata3: COMRESET failed (errno=-16)
 [   55.739429] ata3: limiting SATA link speed to 3.0 Gbps
 [   60.763387] ata3: COMRESET failed (errno=-16)
 [   60.763392] ata3: reset failed, giving up
 
 
 So that explains the very long boot time and the absence of /dev/sdb after the system started.   
 
 
 My attempts to find similar problems on these forums and elsewhere have come up dry.  Can anyone suggest a way forward?
 
 
 Thanks in advance,
 
 
 Chris

---

### Post by weatherman2 on 2016-04-17
Because 16.04 is technically still beta, there's a tiny chance you are seeing a bug that will be fixed before release.

So it's worth trying to setup the disk first using a released version and see if it works any better there.  If not, then it's presumably not a bug in the 16.04 beta.   If it is, I think there is a separate section for posting bugs for the unreleased beta versions.

---

### Post by oldfred on 2016-04-17
3TB and any fdisk before the one in 16.04 do not mix.
You converted you 3TB drive to 2TiB.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You need to use gpt partitioning and can use gdisk or gparted.
       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

           
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Chris_Read on 2016-04-17
Thanks Weatherman and especially Fred.

Fred-  

I did use the fdisk in 16.04 to create the 3TB partition.  I suspect it worked because the "dd" instruction reported just over 3 trillion bytes written.

In any case, I can't try alternate ways to partition the drive because, while the BIOS sees the drive, Ubuntu does not create an entry in /dev for it.

Do you know of a way to overcome the "ata3: COMRESET failed (errno=-16)" error and get Ubuntu to create a /dev/sdb again?

Thanks,

Chris

---

### Post by oldfred on 2016-04-17
This really old bug has a possible work around, by changing BIOS settings for drive.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259/comments/27)

Change to compatiblity then back to AHCI. New larger drives and SSDs need to be AHCI.

---

### Post by Chris_Read on 2016-04-18
Thanks again, Fred.

My motherboard offers two alternatives to AHCI:  IDE and RAID.  I restarted using IDE and the drive appears, this time on /dev/sda.  (The boot SSD came up on /dev/sdb this time and boot time was very long.)

When I revert to AHCI as you recommend, the drive again disappears with the "COMRESET failed (errno=-16)" in dmesg.
[B]
Is there something I should be doing while I have the drive available in IDE mode (perhaps the mkfs)  that might make it accessible when I go back to AHCI?[/B]

Many thanks for all the help.

-Chris

---

### Post by oldfred on 2016-04-18
I thought IDE was only for compatibility with very old IDE drives.

I changed to AHCI back in 2011 with my first small SSD. AHCI was required for trim to work. But XP did not have drivers for AHCI without leaping thru hoops, so I retired XP. But Ubuntu did work in either IDE or AHCI mode.

What system or brand motherboard? Is UEFI/BIOS most current version from vendor?

---

