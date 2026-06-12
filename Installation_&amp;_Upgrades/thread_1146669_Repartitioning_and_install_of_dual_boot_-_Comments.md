---
title: "Repartitioning and install of dual boot - Comments please!"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by ee19921 on 2009-05-02
Right now I have clumsy partitions(attachment). I am planning start from scratch to install a dual boot windows and Ubuntu with just 2 partitions. One 30 GB fat32 for windows and the rest for Ubuntu ext3. I have these assumptions and before I proceed I just want to make sure that I am right. 

- Use live CD to partition the disc into 2 and install ubuntu on first partition
- Install windows on the second. 
- I need not have a swap parition and I can create a swap file later to enable hibernation
- I can bring back all my user settings, firefox addons, plugins (flash), by copying back home directory from my backup.

---

### Post by Herman on 2009-05-02
> - Use live CD to partition the disc into 2 and install ubuntu on first partition:) That's okay.
> - Install windows on the second. That's okay too. There's a popular myth in circulation that Windows can only be installed in partition number one at the start of the hard disk, but that's not true at all.
You will find though, that Windows will overwrite your MBR with the boot code for their boot loader. There's nothing you can do to stop it. You can make a backup of your MBR, (just the boot loader area), with a dd command and restore it later the same way, or you can just re-install GRUB using your Ubuntu Live CD after you install Windows XP.
There are a lot of ways to re-install GRUB to MBR. Then you'll just need to edit your GRUB boot menu, (/boot/grub/menu.lst) by hand to add an entry for chainloading Windows from GRUB.
If that seems like too much work, then install Windows first and Ubuntu second. Ubuntu will set GRUB up automatically if Windows is already there.
> - I need not have a swap parition and I can create a swap file later to enable hibernationYes, I like that idea myself, here's my favorite link on the subject, -  [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k.
> - I can bring back all my user settings, firefox addons, plugins (flash), by copying back home directory from my backup.Well the way I always do it is to only copy the files I recognize, such as my normal files, plus certain files that a kept in hidden files and directories. These include such files as .evolution/addressbook, calendar, email, memos and tasks, plus other hidden folders for certain other programs.
I don't just copy anything and everything, I'm selective about what I overwrite when I'm restoring. Some of the files from the old system may have had improvements made since the older operating system came out, that have now been superceded and may not completely suit the new system's programs. This could especially happen when moving from an older version of Ubuntu to the latest version. The developers do keep things backwards compatible, but there are certain files we can overwrite and others they might not expect us to overwrite, I'm not sure, so I stick to the safe way of doing things and just overwrite the files I understand or recognize.
When making a backup it's a good idea to include everything, but be careful what to restore, that's what I think.

Regards, Herman :)

---

### Post by ee19921 on 2009-05-02
> **Herman said:**
> 
Well the way I always do it is to only copy the files I recognize, such as my normal files, plus certain files that a kept in hidden files and directories. These include such files as .evolution/addressbook, calendar, email, memos and tasks, plus other hidden folders for certain other programs.
I don't just copy anything and everything, I'm selective about what I overwrite when I'm restoring. Some of the files from the old system may have had improvements made since the older operating system came out, that have now been superceded and may not completely suit the new system's programs. This could especially happen when moving from an older version of Ubuntu to the latest version. The developers do keep things backwards compatible, but there are certain files we can overwrite and others they might not expect us to overwrite, I'm not sure, so I stick to the safe way of doing things and just overwrite the files I understand or recognize.
When making a backup it's a good idea to include everything, but be careful what to restore, that's what I think.

Regards, Herman :)

That is some good advice. I am only going to restore only those in which I will have problems. Thanks Herman!!!

---

### Post by ee19921 on 2009-05-02
> **Herman said:**
> 
There are a lot of ways to re-install GRUB to MBR. Then you'll just need to edit your GRUB boot menu, (/boot/grub/menu.lst) by hand to add an entry for chainloading Windows from GRUB.



This is what I have currently. I am going to reuse it. root (hd0,1) - means to load from 2nd partition. Am I right? I guess I should be able to get it done by trial and error once grub is ready.

```
title Microsoft Windows XP Home Edition
root (hd0,1)
chainloader +1
savedefault
makeactive

```

Thanks!

---

### Post by Racecar56 on 2009-05-02
what is that 7.84 megs of blank space at the bottom for?

---

### Post by Herman on 2009-05-02
```
title Microsoft Windows XP Home Edition
root (hd0,1)
chainloader +1
savedefault
makeactive
``` That looks good. :)

---

### Post by ee19921 on 2009-05-03
> **Racecar56 said:**
> what is that 7.84 megs of blank space at the bottom for?

I created these partitions a long time back. I think it had to do with a partition manager, which wouldn't let me add that chuck.

---

### Post by ee19921 on 2009-05-03
I installed Ubuntu on the first partition. But while installing XP if I select the second partition, it won't let me install as it has to write some startup files and it can't(attachment). In short, I think it is not recognizing the ext3 partition. 

Do we have a way around this? Or do I have to install Windows on the first partition?

---

### Post by Herman on 2009-05-04
I don't know, I've never come across that problem before, sorry if I've given you bad information. As far a I know (or thought I knew), it should install happily wherever we tell it. After all, people are able to dual boot more than one version of Windows in the same computer. :confused:

---

### Post by ee19921 on 2009-05-04
> **Herman said:**
> I don't know, I've never come across that problem before, sorry if I've given you bad information. As far a I know (or thought I knew), it should install happily wherever we tell it. After all, people are able to dual boot more than one version of Windows in the same computer. :confused:

This is an earlier version of XP. I am not sure if that is the reason. Anyways, yesterday night I reformatted and installed Windows first and then Ubuntu. I also had a problem with Ubuntu booting time, even that is gone. 

Thanks Herman!

---

### Post by daftbeaker on 2009-05-12
This seemed like an appropriate thread for my question.

I recently upgraded from Intrepid to Jaunty and had a few niggles (odd shutdown screen and other similar stuff, nothing serious).  I have two hard drives, one with Vista and one with Ubuntu.  The Ubuntu one was set up with two partitions, one Ext3 taking up almost all the drive and a swap partition.

I just repartitioned so I now have a large partition for all my data, 2 small Ext3 partitions and a reduced swap partition.  I've just installed a vanilla copy of Jaunty on one small partition and will try Fedora 10 on the other soon.

Basically what I want to know is whether it's possible to delete the old Ubuntu OS from the large partition and then use that as a separate Home partition.  Will I be able to do that from within Jaunty or do I need to set it up at the install?  
If it needs doing during the install, will choosing the current data partition as Home do anything to the data already on it?  
Finally, if I do set up a separate Home partition, do I set it to /Home and the OS partition to / or the OS to /boot and the data to /?

Thanks

---

### Post by Herman on 2009-05-13
> Basically what I want to know is whether it's possible to delete the old Ubuntu OS from the large partition and then use that as a separate Home partition.Yes, you can do that.
>  Will I be able to do that from within Jaunty or do I need to set it up at the install? You can do it from within Jaunty, there's no need to re-install, although it would have also been easy to do it at installation time instead.
Just delete all the operating system directories from the partition, then copy everything out of the /home/username directory and paste it into the root of the partition, (so everything that was inside the /home/username directory is now outside. Don't forget all the hidden files, those are most important.
While you're at it, make a backup to some other media.
Then delete the now-empty directory.
Edit your /etc/fstab file in Jaunty and register your old partition as /home and reboot.
> If it needs doing during the install, will choosing the current data partition as Home do anything to the data already on it?  
If you chose to do it that way, you would still need to make a complete backup of it to some other media first, then you would install and choose that as /home, but do not allow the installer to format it.
> Finally, if I do set up a separate Home partition, do I set it to /Home and the OS partition to / or the OS to /boot and the data to /?/home and / (root).

I have been a little brief but I'm willing to elaborate if required. Don't be shy to ask more questions if you need more details.

---

### Post by daftbeaker on 2009-05-13
Thanks for all the help, I've got a few issues to work out.
> **Herman said:**
> Yes, you can do that.
You can do it from within Jaunty, there's no need to re-install, although it would have also been easy to do it at installation time instead.
Just delete all the operating system directories from the partition, then copy everything out of the /home/username directory and paste it into the root of the partition, (so everything that was inside the /home/username directory is now outside. Don't forget all the hidden files, those are most important.
Then delete the now-empty directory.
I've deleted everything off the old partition except what was in /home which has been moved, the partition now just contains home stuff outside of the home folder eg. /partition/Music, not /partition/home/daftbeaker/Music

> **Herman said:**
> 
Edit your /etc/fstab file in Jaunty and register your old partition as /home and reboot.
Here's where I'm having trouble, I put in the partition in /etc/fstab as "/dev/sdb1 - /home - ext3" but wasn't sure what options, dump or pass I needed and Google wasn't very specific.
I tried using the settings from the current / directory (relatime,errors=remount-ro - 0 - 1) but when I booted in like that I got a message saying "User's $HOME/.dmrc file is being ignored".  Is that likely to be due to me messing up fstab or not deleting my current /home directory?
With the fstab file, should I be setting the mountpoint as /home or /home/daftbeaker?

Thanks again.

---

### Post by Herman on 2009-05-13
> I put in the partition in /etc/fstab as "/dev/sdb1 - /home - ext3" but wasn't sure what options, dump or pass I needed and Google wasn't very specific.The 'dump' column is not used as far as I know, I think it's an old relic from a bygone era when there was some kind of a backup utility called 'dump'. Anyway, I haven't seen it with anything other than a zero in it in Ubuntu.
The 'Pass' column is used, and that controls whether the file system will be checked at boot-up. Ubuntu runs fsck -C -R -A -a which means fsck will 'walk through' the /etc/fstab file and check the superblock of each file system that has an '1' or a '2' in the 'pass' column in /etc/fstab, and it will run a quick, safe type of file system check on any file system whose superblock is marked as due for a fsck.
If there's a '1' in the 'pass' column, the file system will be checked first, and individually, If there's a '2', it will be checked second and also simultaneously with others that also show a '2', to reduce boot time. 
Also see [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131"), by bodhi.zazen
[*Fstab*]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=4&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FFstab&ei=Hg8LSt-WL5PEtAP569TYCA&usg=AFQjCNH-3NOY8Q8ruaMm3iV3JXVNrlTMAQ&sig2=JhS42LrG8uz8qulJwo2wEA") - Community Ubuntu Documentation
                         [How to Edit and Understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")[**]("http://www.tuxfiles.org/linuxhelp/fstab.html") -tuxfiles.
> I tried using the settings from the current / directory (relatime,errors=remount-ro - 0 - 1) but when I booted in like that I got a message saying "User's $HOME/.dmrc file is being ignored". Is that likely to be due to me messing up fstab or not deleting my current /home directory?
With the fstab file, should I be setting the mountpoint as /home or /home/daftbeaker?
If you look at bodhi.zazen's fstab tutorial, you'll see there an example in blue of hwo to mount a separate /home.
Also see these two links, [Create a *separate home* partition in *Ubuntu*]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.psychocats.net%2Fubuntu%2Fseparatehome&ei=Hg8LSt-WL5PEtAP569TYCA&usg=AFQjCNEgtQIp0sc6F_WAqYNPUU0gWq8PXg&sig2=1ZV8UuSuXl03z-Nsio4Fiw") - psychocats[ubuntu] [Separate home partition in Ubuntu  Made Simple]("http://ubuntuforums.org/showthread.php?t=789272")  - Ubuntu Web Forums - criskat777
The interesting thing about those two links is, they both say you should chmod your .dmrc file and your /home directory, and they give you examples of the commands for doing so. That should fix your '.dmrc file is being ignored' problem.

Let me know if I can be any more help,
Regards, Herman :)

---

### Post by daftbeaker on 2009-05-13
I got frustrated trying to work around the problem and just re-installed after backing everything up.  Worked fine, my /home directory is now over 100Gb compared to less that 15Gb :D

I still need to copy the files back over and organise everything properly but it's well along the right track.

Thanks for the help, if nothing else I learned a load of terminal commands ;)

Edit- Just in case it helps anyone else, the way Ubuntu set up a separate partition /home folder in fstab was:
(Partition UUID=) ~ /home ~ ext3 ~ relatime ~ 0 ~ 2

---

