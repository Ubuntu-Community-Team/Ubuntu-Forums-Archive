---
title: "hdd failing... best way to 'ghost' partitions+mbr?"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by graysky on 2009-03-19
My current HDD is beginning to click when idle and I'm fearing that it will no longer work so I want to backup the drive to a brand-new HDD of the same size.  It has three partitions on it currently:

/dev/sda1 is NTFS and contains Windows XP
/dev/sda2 is NTFS and contains a large data partition
/dev/sda3 is ext3 and contains my /boot for Intrepid

(LINUX stuff resides on a 2nd smaller HDD).

Anyway, can gparted do this and retain the MBR on the disk so that I can literally swap the "bad" one for the new one once I'm finished?  I don't want to reinstall either Windows or Intrepid.

---

### Post by Herman on 2009-03-19
I think GParted can copy one partition to another location on the same hard disk, but I don't think it can copy from one hard disk to a different hard disk.

Partimage is a good safe program we can install in Ubuntu or install temporarily in the Ubuntu 'Desktop' Live CD. 
Partimage is also in [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") and in most other Linux rescue CDs, including GParted Live CD and Parted Magic.
Partimage is a little bit confusing for new users.  The best how-to on using Partimage was written by one of the Ubuntu Web Forum moderators, aysiu, here's the link, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")
Partimage can copy one partition at a time.

Otherwise, the 'dd' command is much simpler and that's the best way to copy the entire contents of the original hard drive to the replacement hard drive, however, it will do exactly what you tell it to do, so it is potentially dangerous to use it unless you're careful. You should give the 'dd' command the same respect you would a loaded gun. Be careful where you aim it. 
```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```**[COLOR=Red]CAUTION: Be very careful with the 'dd' command and double and triple and quadruple checked that you will be copying the drive with the data to the blank drive and not the other way around. If you use the 'dd' command the wrong way you can wipe out all of your data![/COLOR]**

---

### Post by Herman on 2009-03-19
If the hard drive has a damaged area that's hard for programs to read, you may have trouble getting Partimage or the dd command to get a good copy.

I just finished copying the contents from an old hard disk to new replacement hard disk for someone. (The computer is a laptop. It had Windows Vista in it and the user had become so angry with it that they slammed the lid so hard it caused the hard disc to be damaged).

First I tried Partimage, but that couldn't copy all of the partitions, it returned errors and failed in the operating system partition. I was trying to copy to a USB external hard disk drive.

After buying a new hard drive which is larger than the old one, I removed the laptop's hard drive and plugged in into a desktop computer with a new hard drive also plugged into the desktop PC. 
Then booted up the desktop PC with Ubuntu Live CD and used a 'dd' command to copy the entire contents of the original hard drive to the replacement hard drive. 
The 'dd' command threw errors but continued anyway when it ran into the damaged area of the hard disk, and slowed down to a crawl. It took all night to copy the damaged area, which was between 72 GB and 81 GB.

The 'dd' command should have worked, but the system wouldn't boot.
I don't want to bore everyone with all the things I tried that didn't work, but what eventually solved my problem was shrinking the partition which was affected by the damaged area with GParted in Parted Magic Live CD.
For some reason GParted was able to resize the partition away from the damaged area without any errors and after that the dd command worked. :D

---

### Post by graysky on 2009-03-19
Cool... are you sure that gparted cannot do a partition copy from one drive to another?  I would settle for copying over just the windows partition (20 gig) and my boot partition (75 meg) from within the gparted UI.  Oh, and the MBR's of course!

I can copy over the NTFS data partition from within windows or linux via robocopy or rsync respectively.

---

### Post by Herman on 2009-03-19
> are you sure that gparted cannot do a partition copy from one drive to another? The last time I tried it, GParted didn't support that, (unless they have added something new that I haven't discovered yet - which always a possibility and does happen fairly often with software).

GParted Live CD comes with Clonzilla, for making a backup of an entire hard disk, and Parted Magic also contains some other software that I haven't investigated yet that might help you. You may want to look into those programs further.

I like the 'dd' command myself, at least for this particular purpose, I don't need an extra backup copy (of someone else's data) taking up room on my hard drives, and for me it would be a waste of time making a backup and then restoring when I can just copy from one disk to the other.  The old hard disk will be saved, both for security reasons and also it isn't likely to deteriorate any further now that it is taken out of service, so it can be used to copy from again. Therefore, it is already a backup.
In your case since it's your own data and if you don't already have a backup then maybe one of those programs would be best for your purposes.

> I would settle for copying over just the windows partition (20 gig) and my boot partition (75 meg) from within the gparted UI. Oh, and the MBR's of course!
If you want to use the dd command, you can copy the MBR from one hard disk to an equal or larger sized hard disc like this,
```
sudo dd if=/dev/sda of=/dev/sdb bs=512 count=1
```
You can copy one partition at a time from one hard disk to another like this,
```
sudo dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror
```
Where: '/dev/sda2' is the partition you want to copy, and '/dev/sdb2' will be the new copy.

Just make sure you check which hard disk is called '/dev/sda', and which one is '/dev/sdb' before you do anything.
You can check by opening GParted Partition Editor and taking a peek, or you can use the 'sudo fdisk -lu' or blkid commands.

---

### Post by wkulecz on 2009-03-19
While you can easily clone Linux to a new drive with rsync and the "Super Grub Boot CD" I hate to say it, but the best way to "ghost" your Windows partitions to a new hard drive is with Ghost.

Went through all this in a big way prior to hurricane Ike, good thing too!

--wally.

---

### Post by graysky on 2009-03-19
That sucks, I don't want to pay a dime for ghost.  Honestly, I have a 20 gig partition w/ XP on it that I want to move to the new drive.  I can rsync the large partition and gparted the 75 meg /boot I think.

Maybe I should just use dd...?

---

### Post by adzik on 2009-03-19
Have you had a look at Clonezilla yet? It is essentially a Symantec Ghost type of utility. I have personally used it once a while ago to clone partitions to different disks.
It runs from a livecd, or I suppose USB if you install it onto a usb stick with unetbootin.
You could try cloning your drive with it and see out it pans out. Just be sure to read up on the basics of using it though. It's not Ghost after all.
Link:  [**http://clonezilla.org**]("http://clonezilla.org")

---

### Post by Mark Phelps on 2009-03-21
> **graysky said:**
> That sucks, I don't want to pay a dime for ghost.  Honestly, I have a 20 gig partition w/ XP on it that I want to move to the new drive.  I can rsync the large partition and gparted the 75 meg /boot I think.

Maybe I should just use dd...?

Take a look at P.I.N.G -- it's a front-end for PartImage.  Their website is windowsdream.com.

They also have a forum where you can ask your questions.

---

