---
title: "New Machine - recommendations for partitions? Dual disks?"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by nmsmith on 2009-08-13
I'm building a brand new, speedy machine. I want it for desktop use (photography, general nerding), backup from other machines in the house, and some games, and will be running Ubuntu and Windows. What's the best way (given that I have a blank canvas) of setting up my disks? I would need partitions (or discrete disks) for each of the two OS's, and plenty space to store media and backups.

I already have a single 1 TB disk, but could buy another if it seemed like a good idea.

I propose:
[LIST=1]
[*]1 TB disk, partitioned as Windows 200GB, Ubuntu 800GB. Games on Windows, media and backup up Ubuntu.
[*]1 TB disk for Ubuntu, separate 3-500 GB disk for Windows.
[*]1 TB disk with 200 GB partitions for each OS, with 600 GB as FAT32 for storage.
[/LIST]

Obviously there are many more solutions. I just don't have an idea of what would be the best, as I've always been constrained to one disj in the past.

The only thing I have found to be a problem is when I installed a 10 GB root partition with the rest of the disk used for media, I found that enormous log files and other files/programmes eventually meant the root partition was quite short of space.

---

### Post by raymondh on 2009-08-13
So nice to start from fresh ;)

With the ability to do 2 disks, I would put both OS' in disk 1 and use disk 2 as a storage with a format readable by both OS' (NTFS).  On disk 1, it does not matter which OS is installed first as you have the ability to tweak the menu.lst. 

With a new system, better test out the liveCD and see how it reacts to your hardware.

My test machine has this set-up.

Disk 1 - Ubuntu 9.04 and win 7 (minimum, and just to see the hoopla about it).  Ubuntu also has virtualized XP.
Disk 2 - Ubuntu Karmic (which I am now testing and tweaking) + XP (in dual boot, not virtualized)
External - Media and storage.

Grub is installed in both HD's and my selection is from BIOS (which I don't mind doing).  When I am happy with Karmic and it is released, I plan to set disk 2 as default and use the other HD to install 9.10 and start tweaking.  That way, I always have a working, tweaked ubuntu. I can also edit my menu.lst to boot either jaunty or karmic.  Am just lazy to do so as I tend to use jaunty (disk 1) often and only get to tweak Karmic when motivated .... hence the BIOS selection. I also virtualize a lot, using windows, etc.  My use of other OS' in my ubuntu machine is limited to a few apps.

Good luck.  Have fun.  happy Ubuntu-ing.

Raymond

---

### Post by Mark Phelps on 2009-08-14
Everyone has different opinions, and in my case, if you're going with two drives, I would recommend the following:
1) One drive for MS Windows with a boot/OS volume and a shared NTFS volume.  The shared NTFS volume will be shared with Ubuntu.
2) Second (smaller) drive for Ubuntu, with also a shared NTFS volume.  The NTFS volume will be shared with MS Windows.
3) Install each OS to it's own drive with the other drive disconnected at the time.
4) When done, boot from the Ubuntu drive and add a stanza for MS Windows manually to the menu.lst file.
5) Continue to boot from the Ubuntu drive.

You didn't say which Windows OS, but I'm guessing it's Windows 7, and unless you're going to wait until Oct 22 to do this, or you have access to an MSDN-distro of the genuine RTM, you'll probably install the RC or one of the later leaked builds.  When you then get the RTM or the commercial release, you'll want to upgrade.

Doing it this way (upgrading to the Windows OS drive with the Ubuntu drive disconnected) will prevent Seven from overwriting the Ubuntu drive MBR and wiping out GRUB.  It will also make any subsequent upgrades/repairs to the MS Windows OS easier as it will retain the Seven-written MBR.  Also, MS has changed the OS installation with Seven such that, on a blank drive, it now write two partitions -- a boot partition and an OS partition.  So, don't be surprised when you're done installing Seven to see two partitions.

---

### Post by nmsmith on 2009-08-14
Raymond, thanks for the tip about the live CD. Everything seems fine, except that the GPU fan is horribly loud, even though my case has sound-deadening panels. Maybe I got over-excited about buying the latest and greatest.

> **Mark Phelps said:**
> You didn't say which Windows OS, but I'm guessing it's Windows 7, and unless you're going to wait until Oct 22 ... you'll probably install the RC ...

You are dead right about Windows: RC right now, with the real thing on preorder. Thanks about the warning for the extra partitions.

I guess it's reassuring to hear that there's no 'right' way to do this. I decided (wisely or not) to repurpose some old drives, so I'm going with:

300 GB IDE Windows 7
160 GB IDE Ubuntu (all ext4, I don't think I'll have much need to get files from there to Windows)
1 TB SATA NTFS storage

Thanks for reminding me about the fact that NTFS 3G works fine these days. I had almost forgot, and formatted the big drive as FAT32.

Now to get my head around the ridiculous file navigation (folders, libraries etc.) I saw in the beta ...

---

