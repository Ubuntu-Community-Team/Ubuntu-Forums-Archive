---
title: "Huge Computer Mess: Need a lot of help"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Liliitha on 2008-12-20
Lot of issues, long story.  A long time ago I partitioned my computer to use windows 98 and Ubuntu simultaneously.  Things worked, no issues.  I ran Windows 98 on my own C: partition and Ubuntu on my own D: partition even though Ubuntu still wanted to perform further partitioning, I let it.  The computer basically sat in my bedroom unused as I used another new computer in it's place.  It sat for one year.  

I finally came back to the good old computer in hopes to use it in my lab.  The year before I had connection errors with Ubuntu due to damaged files but after a few hours of hard work I got the internet to work.  I decided to completely remove windows 98 from the computer by formatting C: and leaving it to be just an Ubuntu machine.  

I moved the computer from my room to my workshop in hopes of it being an all around work computer.  I upgraded the said Gutsy Gibbon operating system to Hardy Heron and to my dismay realized that after this transition the computer completely ceased to run the internet.  I came online and failed to find a fix this time, I gave up a little early and decided to completely remove Ubuntu and reinstall the newest Ubuntu onto one whole drive instead of a tiny partition.  

I got to work and formated the C: drive, and the D: drive using a bootable floppy disk DOS.  The operating system was still on my computer even after the formatting of the drives it should have been on.  The last drive that I did not make was drive E: and we could not do anything to the E: drive with the Floppy Disk.  I decide to FDISK the computer and delete the partitions.  

Everything goes well until... the D: drive says it is a logical drive and for that we cannot remove it.  When I go to remove the logical drive out of the D: drive it says there is no logical drive.  No big deal, I manage to salvage 14 gigs out of the original 30 gigs, I can live with that I suppose, the D: drive only had 5gigs anyway I have no idea what happend to the other 10...  

So I go to install the latest version of Ubuntu when, uh-oh.  GRUB or the boot-up program for Ubuntu says it cannot boot up from the CDROM because of error 22.  I do some detective work (google...) and find that I need to insert my Windows disk and fix mbr.  Ok, I am going to insert my Windows 98 disk in to save the day when, uh-oh, I get the SAME freaking error message, "GRUB loading, please wait... Error 22".  Horrified that GRUB is still loading even though the disk is not even Ubuntu I come here for answers as to why my computer is behaving so irregularly.  I have thought of a few reasons/solutions.  

#1 I cannot un-partition Drive D: because the logical partitions are part of the Ubuntu partition and I need some method of seeing them with another disket.  

#2 GRUB used to be what would load either Windows 98 or Ubuntu 8.04 on my computer back when I used them simultaneously.  Now that the Ubuntu files are no longer there it is freaking out because they are completely absent.

#3 Find some type of bootdisk for Ubuntu

#4 My Hard Drive is completely screwed and I should just go out and get another one...

Any other solutions would be greatly appreciated.

---

### Post by infamous-online on 2008-12-20
When I got this error, I simply completely overwritten everything on the drive. I either re-installed Ubuntu on it or Windows and that always did the trick. I know this might not be what you're looking for, but a fresh install will cure this. Hopefully, there aren't any critical files left on the machine, as you maybe forced to lose them. 

So have you tried a fresh re-install? If so, did this error reappear?

---

### Post by Liliitha on 2008-12-21
> **infamous-online said:**
> When I got this error, I simply completely overwritten everything on the drive. I either re-installed Ubuntu on it or Windows and that always did the trick. I know this might not be what you're looking for, but a fresh install will cure this. Hopefully, there aren't any critical files left on the machine, as you maybe forced to lose them. 

So have you tried a fresh re-install? If so, did this error reappear?

I don't know how to reinstall since I cant do anything on the computer.  Everything on the hard drive has been cleaned off.  I tried to install from a boot-able CD and I get the error even though everything should have been cleared off.  It is like the files are stuck on there and I have no way to get them off.

---

### Post by Aearenda on 2008-12-21
Sounds like the computer booted from the hard drive even when you had a CD in the drive. Check the BIOS settings to make sure the CD drive will be started before the Hard Drive, or use the function key at boot time that allows you to select which drive to boot from. That key varies a lot - watch the screen closely as it starts, it should tell you.

When you clear partitions, it doesn't clear the Master Boot Record (MBR), which is where the computer goes to first to begin to understand the partition structure on the disk as well as to start loading the operating system. If there is nothing present in the MBR, the drive will be skipped and the next in order is tried; but if there is anything bootable in the MBR (like the GRUB remaining from before) then it will try to boot that. But GRUB looks next for the partition it was told to use, which isn't there any more.

I wouldn't mess about with Windows 98 CDs or boot diskettes. The Ubuntu setup is quite capable of doing all the partitioning and formatting it needs. Now that you have wiped the drives, you can use the Desktop CD and choose to use the whole disk - it will do the rest for you.

---

### Post by infamous-online on 2008-12-21
> **Liliitha said:**
> I don't know how to reinstall since I cant do anything on the computer.  Everything on the hard drive has been cleaned off.  I tried to install from a boot-able CD and I get the error even though everything should have been cleared off.  It is like the files are stuck on there and I have no way to get them off.


Hmm, in your bios is the cd-rom set to be the first thing that the pc looks for before booting to any particular harddrive?

---

### Post by Liliitha on 2008-12-21
> **Aearenda said:**
> Sounds like the computer booted from the hard drive even when you had a CD in the drive. Check the BIOS settings to make sure the CD drive will be started before the Hard Drive, or use the function key at boot time that allows you to select which drive to boot from. That key varies a lot - watch the screen closely as it starts, it should tell you.

When you clear partitions, it doesn't clear the Master Boot Record (MBR), which is where the computer goes to first to begin to understand the partition structure on the disk as well as to start loading the operating system. If there is nothing present in the MBR, the drive will be skipped and the next in order is tried; but if there is anything bootable in the MBR (like the GRUB remaining from before) then it will try to boot that. But GRUB looks next for the partition it was told to use, which isn't there any more.

I wouldn't mess about with Windows 98 CDs or boot diskettes. The Ubuntu setup is quite capable of doing all the partitioning and formatting it needs. Now that you have wiped the drives, you can use the Desktop CD and choose to use the whole disk - it will do the rest for you.

Ok thanks guys, that does make sense.  You see the primary boot up is the CDROM but it would always skip that and go to the floppy anyway.  So now that the Floppy isn't in it is skipping straight to the Hard Drive.  This probably means my BIOS is incapable of booting the computer with the CDROM but I think I saw a fix for that in the installation instructions.  Thanks for the help.  
[B]
So, is there a remedy for the inability to delete the D: partition?[/B]

---

### Post by Aearenda on 2008-12-21
You'll probably find the D: problem is caused by the presence of an extended partition, though I find your description a bit confusing. A modern partitioning utility will be able to sort it out, just don't use MS-DOS's FDISK for it!

---

### Post by Liliitha on 2008-12-21
> **Aearenda said:**
> You'll probably find the D: problem is caused by the presence of an extended partition, though I find your description a bit confusing. A modern partitioning utility will be able to sort it out, just don't use MS-DOS's FDISK for it!

It is an extended partition but it says I cant get rid of the extended partition because there is a logical partition in it.  Then I go to delete the logical partition and it says there is no logical partition.  X(

---

### Post by Aearenda on 2008-12-21
I suggest you fix the CD booting first, after that there is a host of different ways to fix the partitioning.

---

