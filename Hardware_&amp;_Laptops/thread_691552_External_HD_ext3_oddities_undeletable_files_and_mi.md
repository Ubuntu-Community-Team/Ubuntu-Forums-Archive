---
title: "External HD ext3 oddities: undeletable files and missing space"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by iamajd on 2008-02-08
Hello my helpful friends!

I'll give you the standard disclaimer: I am no pro, but I am not new to this.  Ubuntu is the only distro I have ever used for any length of time.  I've played with other distros and other OSes.  I think Ubuntu has been my primary OS for around 3 years now.

And now for the background to my problem:  I have a "250" gig external USB harddrive.  All but the last 10gb are formatted as ext3 (the last 10 being a NTFS partition labeled "Vestige" so I can more easily swap files with Window's users).  I was experiencing some oddness so I unmounted it and ran e2fsck with the force, assume yes, and verbose options.  After nearly forever, it finished.  A lot of stuff ended up in "lost+found" and I sorted it all back out.

Most important problem:  The "lost+found" directory has four garbage files (well, two think they're directories) in it that I cannot delete.  Root (via sudo) cannot delete them either.  Neither can they be chown'ed or chmod'ed.  A quick "ln -s" revealed why.  They have absurd owners, groups, creation dates, and permissions.  For example, one file named #10242960 is of size 36864, is owned by 4031306275, in the group 1677925202, was created on 1972-03-24 at 01:55 (more than 9 years before my birth), and has permissions --wsr-Sr--.  I tried to create user 4031306275 so I could remove the file... but the user number is above the cap.  The other files have similarly berserk attributes. One was created in 2088.  So, any clues how to get rid of them?

Secondary problem:  A folder with about 60gb of someone else's music disappeared.  It was completely unimportant so I don't mind it being gone.  However, it is now a phantom taking up space somehow.  The partition size is 222.89GB with 149.14GB used but, for some reason, only 21.8GB free.  Perhaps ext3 does math differently than I do, but that doesn't add up.  I know there is some filesystem overhead, but 5%* of 222.89GB does not make up for the difference.  Yes, I checked EVERYWHERE for the missing data.  The ONLY thing hidden on the drive is the .trash directory and it is empty.  Any guidance on recovering this much needed space?

*Since it is not a root drive and has no /tmp or /var, I long ago used tune2fs to decrease this quite a bit.  Does anyone disagree with that being acceptable?

Solution I want to avoid:  So, I could resize the screwy partition to create room for a new partition and little by little move everything to it until I could delete the screwy partition.  That will take millenia and I would really hate to do it.  If it comes to that, should I try a different filesystem?  I've never used ReiserFS and am a little curious about it.  JFS has given me problems on external drives (root-only permission on automount... not important now).

Well, there you have it.  I do hope someone can be of assistance here.  I also hope that deleting those 4 garbage files will recoup the missing space.  Who knows?  Thanks in advance!

---

### Post by chrisdeckard on 2008-02-08
First thing, stop using the drive.  It sounds like you have massive filesystem corruption, possibly because the drive is failing.  You need to backup any important stuff off that drive, pull it, put it in a computer, and run a disk analyzer on it.  If you have that much stuff ending up in lost+found, something is going wrong.

You can try and make a complete copy of the disk or each partition.  

```
# dd if=/dev/sdb1 of=/path/to/backup/of/disk
```

Assume the worst, that the disk is dying.  Any motion of the drive is going to destroy data, whether you're reading data off of it or not.  If dd fails on you part way, you most likely are SOL.

After you make your backup, put the disk in a computer and snag Seagate's disk analyzer tool.  [http://www.seagate.com/www/en-us/support/downloads/seatools/]("http://www.seagate.com/www/en-us/support/downloads/seatools/").
It's mostly for Seagate drives, but might work on other disks.  It has some nice disk analyzer stuff on it.

If the disk ends up being just fine, I'd recreate the filesystems on it, and restore your data from the backups.  The filesystem is at the very least in an unstable state and may or may not get worse.  I wouldn't trust it.

Good luck.  Hope you have other backups.

-Chris

---

### Post by chrisdeckard on 2008-02-08
I forgot to mention, once you've made your backup, the disk is "ok", I'm not sure what to tell you about getting files back or finding lost space.  The filesystem is messed up probably, rare for ext2/3, but it can happen.  Sorry I can't be of more help in that area.

-Chris

---

### Post by iamajd on 2008-02-09
Thanks chrisdeckard.

It is in a sealed enclosure, so removing it would be no small feat.  I really believe it is a filesystem problem and not a hardware issue.  The only reason I say that is that it is mostly used on my laptop... which frequently freezes... and the drive has seen plenty of reboots without having been unmounted.  Plus, the drive is fairly new, perhaps even under warranty.  I do have a backup but it is a little dated and not with me.  I'm going to do what I can to transfer the files elsewhere, wipe the partition, and then move them back.  I guess I'm just hoping for the best.

For anyone interested, I kept trying to get rid of those pesky files but with the permission issues, I couldn't.  Maybe there is an ext3 mount option that will ignore permissions, but I don't know it and I couldn't discovering such a trick via Google.  But then I remembered that there IS a way to access an ext3 drive and ignore permissions... using ext2fsd in Windows.  So, I was able to remove the troublesome files.  The free space is still missing.

Can someone more knowledgeable than I recommend a filesystem to use on my external drive?  Does ext3, Reiser3, or another one have any noticeable benefits on external drives?  It is mostly music/audiobooks, videos, and some documents.  Drive speed is 5400rmp.

Thanks again chrisdeckard and thanks in advance to whomever else proves helpful!

---

