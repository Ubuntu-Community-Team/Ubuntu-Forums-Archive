---
title: "Looking for opinions on setting up dual drives (SSD + HHD)"
date: 2018-02-09
forum: Hardware
---

### Post by cruzer001 on 2018-02-09
I got me a new (used) laptop.  The SSD has windows10, the HDD is empty.  Both internally mounted.

I wish to move the windows install (currently on the ssd) to the hhd.  Leaving the ssd for linux only.  I think this is simple, just use clonezilla and move it.  But I wonder if afterwards will windows know and complain about being moved.

Reason:
I run linux 95% of the time and I do not want window updates messing with my system.  I plan on using the bios boot screen to switch between the two drives and this way avoid any window update conflicts as only the windows drive will be mounted when updating it.

So is this a workable plan?  I need a pat on the back before diving in :D

---

### Post by oldfred on 2018-02-09
UEFI or BIOS?

And if cloning to another drive, you must be careful to repartition old drive as you cannot have duplicate UUIDs (and GUIDs if gpt).

If UEFI Windows updates still can cause issues.
It will make itself first in UEFI boot order (Ubuntu/grub does that also). If BIOS, it reinstalls its boot loader to MBR. Not sure with 2 drives, as some with Windows on a second drive have had the Windows boot partition on first drive.
And Windows 10 will still turn on fast start up or hibernation, so all NTFS partitions remain mounted. You then cannot use a shared NTFS data partition unless you turn fast start up off again.

---

### Post by Yellow Pasque on 2018-02-09
> I run linux 95% of the time and I do not want window updates messing with my system. I plan on using the bios boot screen to switch between the two drives and this way avoid any window update conflicts as only the windows drive will be mounted when updating it.

That doesn't make sense to me. Windows can't even read ext4 without an external program. How is Windows Update going to mess with your Linux install?

---

### Post by cruzer001 on 2018-02-10
Hi oldfred

> UEFI or BIOS?
If I set it to BIOS, this would allow the ssd (linux) to boot and not detect the second (windows10) drive.  This is how I will run 95% of the time anyhow.  When windows is required I will have to reset to uefi and boot the windows hdd which in turn should not be able to detect the ssd (linux) drive.  This should give me the total isolation that I want between the two drives.

Another possibility is a standalone boot manager to choose between the two.  Something I need to research this weekend.

> you must be careful to repartition old drive as you cannot have duplicate UUID (and GUIDs if gpt).
The ssd (drive#1) with the original windows install will be wiped clean.  Only the hdd (drive#2) will have windows.  This should not be a problem.  I think I will physically remove the ssd and make sure windows is working before I wipe the ssd.

> It will make itself first in UEFI boot order (Ubuntu/grub does that also). If BIOS, it reinstalls its boot loader to MBR. Not sure with 2 drives, as some with Windows on a second drive have had the Windows boot partition on first drive.
BIOS will be on drive#1 and windows boot loader will be on hdd (drive#2)  I think this will keep me out of trouble.

> And Windows 10 will still turn on fast start up or hibernation, so all NTFS partitions remain mounted. You then cannot use a shared NTFS data partition unless you turn fast start up off again.
Going to have to watch out for this.

Thanks Fred

---

### Post by cruzer001 on 2018-02-10
> **Temüjin said:**
> That doesn't make sense to me. Windows can't even read ext4 without an external program. How is Windows Update going to mess with your Linux install?
Hello Temüjin

No its not going to mess with ext4.  But I have read that windows upgrades can make linux unbootable or not show in the boot options.  Something I just don't want to deal with.  My windows install will spend most of its life collecting dust.  On those occasions that I use it and upgrade it I just don't want it giving me any grief.  So I want my windows10 set up just like I have windows7 on my desktop, in total isolation :)

---

### Post by xviravenivx on 2018-02-10
If you downloaded the windows 10 boot image formatted both disks ( if possible, not sure if they had programs you want to keep) yet you could just install windows to the hdd (in a 100gb partition if storage is a necessary thing, and do the rest as fat32) then run the ubuntu installer second and install it to the SSD giving ubuntu a quick boot and windows enough space to blow lol. At least that is what i would do in your situation as its the same as i did on my useless desktop... 


PS 
quick thought came to mind hiren's 10.5 has ghost and you should be able to use that to transfer the windows ssd partiton to the HDD

---

### Post by cruzer001 on 2018-02-10
Thanks xviravenivx

---

### Post by oldfred on 2018-02-10
Many seem to like rEFInd as a boot manager. It only works with UEFI systems but may be able to boot another system in BIOS mode.
       Alternative efi boot manager for UEFI systems with graphical menu:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Note that UEFI is now a boot manager (menu), grub is both a boot manager and boot loader.
 
I would use gpt partitioning for your Ubuntu drive. And  make first two partitions the ESP & bios_grub.
Then you can convert from UEFI to BIOS or vice-versa with just reinstalling the correct version of grub.
The grub-pc is for BIOS boot and grub-efi-amd64 is for UEFI on 64 bit systems.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by cruzer001 on 2018-02-10
> Many seem to like rEFInd as a boot manager
Thats exactly the one I been looking at. Rodsmith.com has several articles out about bios/efi and I have been slowly reading through them.

> Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.
The ssd is small (128G) the hdd is 1TB.  Just going to let the ubuntu install (18.04) use the entire ssd.  Installing virtual machines on that will eat it up the space.  I realize 18.04 is still under development, I'll keep a box of bandages handy.  I will rsync my home directory to the hdd and thats it for data and backup.

Will leave the 2G swap file in place maybe, really don't need it.  I have 12G of ram and won't be using hibernate.

Thanks Fred

---

### Post by oldfred on 2018-02-10
On my 128GB SSD, I have two / (root) partitions, one current LTS and one another. The other was last 14.04LTS and will be next 18.04LTS.
I assign about 25 to 30GB for / including /home, but have all data on HDD in /mnt/data partition with all folders linked into /home in all installs. (more installs on HDD for tests).
I also backup list of installed apps, and any edits I manually do in /etc, I copy file like 40_custom to /home so that gets backed up also.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by cruzer001 on 2018-02-11
"Oldfred's list of stuff" was added to my Zotero collection quite a while ago :)  An excellent reference, thank you.

I have figured out what I'm going to do.

[ATTACH=CONFIG]278494[/ATTACH]

---

### Post by cruzer001 on 2018-02-13
Update

Still doing some reading

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

When I make it to the end of this post, I should be ready for anything efi :)

---

