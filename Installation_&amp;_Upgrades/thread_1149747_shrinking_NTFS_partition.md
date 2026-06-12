---
title: "shrinking NTFS partition"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by idiota on 2009-05-05
Hi everyone,

I'm a newbie to unbuntu, although not to computers in general. I'm trying to dual-boot on a 5 year old IBM PC, and my problem is exactly the same as in an old thread:

[http://ubuntuforums.org/showthread.php?t=212985](http://ubuntuforums.org/showthread.php?t=212985)

I tried to post to that thread but wasn't allowed. I want to shrink an NTFS partition - it has files in the _**middle**_ of the disk, and is thoroughly defragmented - but defragmenting won't MOVE the files to the BEGINNING of the partition. Obviously the Windoze defrag prog can't be bother to move files if they are not fragmented. I've tried to find freeware to sort this without success. Any help would be most appreciated.

I'd much rather not have Windoze, but I share this computer with people who want it. :(

I've also tried running defrag in safe mode with no paging file. There are still files in the middle of the partition I want to shrink.

---

### Post by Bartender on 2009-05-05
iota -
Do you have the ability to back up all personal data and reinstall Windows?
You'd need 
1) an external HDD (unless the personal files would fit on a coupla DVD's) 
2) a Windows install CD or the recovery discs
3) make yourself a copy of GParted LiveCD.  This can be done on a Windows PC if you know how to make an image.  IsoBurn is a free program that has a good reputation for burning images easily, but most any aftermarket burn software will do it if you know how.

If the Windows install has never been wiped and reinstalled, you're due anyway.

After backing up, boot from the GPartedLiveCD and wipe the drive clean.  Create an NTFS primary partition at the "front" (left-hand side) of the drive for Windows.  Then create an extended partition out of the rest of the drive.  Or just create a primary partition, formatted as ext3 or 4, out of the rest of the drive.  With Gparted, you want to "Apply" each change as you go.  Don't let several tasks stack up!

I don't want to get all complicated on you, but with GPrted you can set up partitions for /, swap, and /home if you want.  Maybe save that for next time...

When you're all done, close out of GParted.  Sometimes the disc won't eject.  As long as you applied all your changes, you can just kill the PC with the power button.

Boot to the Windows install CD or the recovery disc.  It should only recognize the NTFS partition.  This way you're installing Windows without letting it sprawl all over the disc.  When Windows is installed, install anti-malware, get updates, get the latest drivers, etc.

Then boot from the Ubuntu disc.  The Ubuntu installer, unlike the dumb Windows disc, will see all the partitions.  You could use the Guided as long as it sees the non-NTFS partition and wants to use it, or go into manual and make sure you're pointing the installation at the right partition.

There are other methods, maybe easier methods, but that's what I've been doing lately and it's worked well for me.

---

### Post by idiota on 2009-05-07
Hello Bartender,

I don't need to save any data on this PC. I've done all that and got into more strife.

I started another thread about this:
[http://ubuntuforums.org/showthread.php?t=1149747](http://ubuntuforums.org/showthread.php?t=1149747)

Thanks.

---

