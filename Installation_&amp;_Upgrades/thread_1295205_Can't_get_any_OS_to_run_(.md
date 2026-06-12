---
title: "Can't get any OS to run :("
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Boris-- on 2009-10-19
Hello people,

I will describe my problem in-depth in hope somebody can help. 

I have recently installed Windows 7 RC. Since I didn't like it I tried to uninstall it by formatting the drive it resided on (c:). I have then tried to reinstall windows XP with no success (error loading OS). I tried deleting all partitions, installing it on another disk (I have 2) and it's always the same error. I've tried everything that is possible in the XP recovery console (fixmbr, fixboot), but nothing worked. 

After giving up on XP I tried ubuntu. Tried the installation 2 times, both times it seems to install well but I get GRUB error 25 at startup.

Did I screw up both of my disks by formattiong one partition? I have figured out that the issue must be in the Master Boot Record (MBR) and that I need to purge it somehow. One of the solutions seems to be a low level hdd format, but I have no clue how to do it since there's no such option in BIOS.

Sorry for the Windows talk, but I'm really desperate here.

Any help/effort will be greatly appreciated.

Have a nice day and thanks for reading!

---

### Post by Bartender on 2009-10-19
Since you seem to be having trouble across 3 different operating systems, first thing I'd try is a different optical drive.  If this is a desktop, it's very simple to swap the existing optical drive out.  Well, there might be complications.  Any geek worth his salt probly has several PATA optical drives laying around.  If your optical drive is SATA, you might have to borrow an old-school IDE data ribbon, check the jumpers on the spare drive, plug into the IDE port on your motherboard, maybe check in BIOS.

Anyway, it sounds to me like the first thing to do is try a different optical drive, via USB port or PATA or SATA.

---

### Post by earthpigg on 2009-10-19
hi,

at the end of the 'manual partitioning' part of the installer (you ***are*** using 'manually partition', ***_right_***?) you will see an 'advanced' button just prior to comitting the changes to disk.

click it.

put grub on the mbr of your hard drive... probablay sda.

---

### Post by pasti on 2009-10-19
Can you get the "live" cd to run without installing it. 
If you can't I would say that this is a hdd problem, or the mbr or grub is broken,perhaps the hard drive is failing.
if it runs fine from the cd try, installing again, sorry I couldn't be much help

---

### Post by Boris-- on 2009-10-19
Hey everybody,

thanks for all the help and effort.

Live CD does load and works normally.

I will try earthpigg's method now, hope it works! Will report what happened afterward.

---

### Post by Boris-- on 2009-10-19
> **Boris-- said:**
> Hey everybody,

thanks for all the help and effort.

Live CD does load and works normally.

I will try earthpigg's method now, hope it works! Will report what happened afterward.

Ubuntu is up and running!!! Thanks a lot earthpigg! You made my week :popcorn:

---

### Post by Boris-- on 2009-10-20
Hello again,

I got greedy and tried to install xp today. Same error (error loading OS), even afer using DBAN. Any ideas?

---

### Post by Boris-- on 2009-10-20
Thank you for your replies, alot!

The problem is really that I can't install wins xp (need for work) on this computer after formating win7 partiton. I know this doesn't belong to this forum but I am trying to fix my computer for a week now with no success.

Here is the problem:

I have used dd to erase my disk, and ubuntu to make a ntfs partition on it. I have tried three different windows xp CDs (one original and 2 backups) and none detect my partition before setup (unknown partition (raw)) or something like that. I didn't go through with making a new one but when I make a new partition in the setup i usually get "error loading os".

Also I can't make a new partiton in setup on my SATA 300gig disk (I have 2 disks, 300 - master and 120 gig -slave). I can only install wins on the 120g IDE disk.

Since I'm not really the most knowledgeable guy in computer history I hope that this makes sense. 

Thanks for your time and have a nice day!

Thank you again for your time!

---

### Post by dhavalbbhatt on 2009-10-20
Windows needs an empty C drive to install. If Ubuntu is the only OS installed on your HDD right now, then you will have to re-format your HDD and then first install XP and then Ubuntu.

---

### Post by Boris-- on 2009-10-20
i dont have any os installed - live cd

---

### Post by earthpigg on 2009-10-20
> **Boris-- said:**
> i dont have any os installed - live cd

boot from an ubuntu live cd. remove all partitions from the hard drive. make a single FAT32 or NTFS partition.

then try the windows cd.

if different Operating Systems and filesystems and partitions where different people speaking different languages:

Linux speaks Windows-language fairly well.

Windows demands that everyone speak Windows, or they are not seen as "real" people.

soo....
Windows is refusing to acknowledge that anyone speaking ext3 is a person.

---

### Post by UndefinedMind on 2009-10-20
Since Ubuntu can be installed using eathpigg's method, have you tried Wine?

---

### Post by xiehuipiaofeng on 2009-10-20
wine isn't as good as winxp or else windows os, at least some applications or hardware like pc cinema running on winxp can not be running well in linux. So you'd better install winxp in the first drive of the master HDD, and this drive must be primary type.

And then, if you are inerest in ubuntu, you could install it in the other drives, select the manual partition during the installation.

---

### Post by RJARRRPCGP on 2009-10-20
> **Boris-- said:**
> Hello again,

I got greedy and tried to install xp today. Same error (error loading OS), even afer using DBAN. Any ideas?

Sounds like a bad HDD.

---

### Post by Boris-- on 2009-10-21
I will try to unplug the larger disk and install xp. I have always loved ubuntu and will install it, but i need xp. 

Thanks for all of your help&time!

---

### Post by Bartender on 2009-10-21
Wherever this space is that you want to install xp - try pre-formatting it again as NTFS with some other partitioning tool.  Maybe try making a GParted LiveCD.  There are other free partitioning tools.

---

### Post by presence1960 on 2009-10-21
> **dhavalbbhatt said:**
> Windows needs an empty C drive to install. If Ubuntu is the only OS installed on your HDD right now, then you will have to re-format your HDD and then first install XP and then Ubuntu.

windows does not need an empty hard disk. I installed XP on my disk with 3 other Linux OSs on the same hard disk.

Windows needs an NTFS or FAT partition or unallocated space. Windows needs to be on a primary partition. **PERIOD...END OF STORY!**

Why do we keep propagating the fallacy that you must install windows before Linux? Here are a couple links to prove that is a fallacy:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Now why on earth are we telling people windows must be installed first, and to remove a perfectly good Linux installation to install windows. Thank God I didn't listen to that advice for I would have removed 3 linux installs, then installed windows and then reinstall the other 3 linux OSs. Shhheeesshh!

The only scenario I can envision where windows must be installed first is the case where a user has a recovery partition/CD/DVD which restores the factory image to the hard disk. In this scenario if one only has a single hard disk then that disk will be restored to the state it was when it left the factory. But if one has a second hard disk and installs Ubuntu onto that, then when they restore windows only the original hard disk will be touched and the second disk will remain as it is.

---

### Post by presence1960 on 2009-10-21
If formatting the space does not work, try leaving it as unallocated space and see if the windows installer recognizes that unallocated space.

---

### Post by dhavalbbhatt on 2009-10-21
> **presence1960 said:**
> windows does not need an empty hard disk. I installed XP on my disk with 3 other Linux OSs on the same hard disk.

Windows needs an NTFS or FAT partition or unallocated space. Windows needs to be on a primary partition. **PERIOD...END OF STORY!**

Why do we keep propagating the fallacy that you must install windows before Linux? Here are a couple links to prove that is a fallacy:

Presence - My bad for not doing the full research on this. I have had multiple issues in the past when I tried installing XP on an existing Ubuntu install. I have lost data and a lot of crap - but that should not be an excuse for not doing the full research.

---

### Post by presence1960 on 2009-10-21
> **dhavalbbhatt said:**
> Presence - My bad for not doing the full research on this. I have had multiple issues in the past when I tried installing XP on an existing Ubuntu install. I have lost data and a lot of crap - but that should not be an excuse for not doing the full research.

I have to apologize. I didn't mean to take it out on you. It is the fact that there are so many people in here telling others that Windows must be installed first- it is becoming almost like a mantra. Then those people tell others and just because they did it that way the belief is that is the only way to do it. If someone wants to uninstall a perfectly good OS or 2 or 3 to install windows be my guest. But that is a lot of work. You can install windows to a primary partition after Linux. The only thing that happens is windows overwrites GRUB on MBR and you will boot right into windows. But that is an easy fix- just restore GRUB to MBR with the LIVE CD/USB. It takes all of 1 minute to restore GRUB., versus how long installing the OSs that were removed needlessly.

With that being said I could have used a more pleasant tone to state the facts. For that I am sorry.

---

