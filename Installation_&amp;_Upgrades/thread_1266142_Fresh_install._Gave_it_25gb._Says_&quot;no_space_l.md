---
title: "Fresh install. Gave it 25gb. Says &quot;no space left on drive&quot;. How can I fix this?"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Ozey on 2009-09-14
I'm very new to ubuntu and very bad with coding and whatnot so please tell me how to fix this in the most newbieish, descriptive, simple way possible.

The title pretty much says it all. I installed Ubuntu on a laptop that had Windows XP and partitioned it. I gave Ubuntu 25gb to work with (a friend of mine said that would be more than enough for programs, files, etc). When I first booted up Ubuntu (after the restart) I was asked to install some updates. I clicked "Install updates" with them all checked and was told I had to clear out all the space that the updates were going to take up. I thought this was very strange, as it was a fresh install, and confused because to my knowledge there's nothing to delete. 

I've looked everywhere for help and I'm completely lost. Please help me out!

---

### Post by Ozey on 2009-09-14
In addition, whenever I open a program (dictionary, gimp, etc) I get a message saying "No space left on drive."

---

### Post by v1nsai on 2009-09-14
Can you post the results of the following so we can get a better look at your system?

First, this will show us how you have your HDD partitioned:
```
sudo fdisk -lu
```

This is a little more complicated to explain, it will show us how folders are mounted
```
cat /etc/fstab
```

---

### Post by Ozey on 2009-09-14
Where do I type the code in?

---

### Post by -=hazard=- on 2009-09-14
> **Ozey said:**
> Where do I type the code in?

Applications > Accessories > Terminal

In terminal type this too:

sudo rm -v /var/cache/apt/archives/*.deb

---

### Post by Ozey on 2009-09-14
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   181968254    90984096    7  HPFS/NTFS
/dev/sda2       181968255   234436544    26234145    5  Extended
/dev/sda5       181968318   232171379    25101531   83  Linux
/dev/sda6       232171443   234436544     1132551   82  Linux swap / Solaris



cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9b0cdc45-8f46-4676-b99c-67455c2fe14c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b039788f-ac93-4708-a11c-a16fa517343c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



ozey@Junko:~$ sudo rm -v /var/cache/apt/archives/*.deb
rm: cannot remove `/var/cache/apt/archives/*.deb': No such file or directory

---

### Post by v1nsai on 2009-09-14
****....there goes my first theory lol

Try going into Applications > Accesories > Disk Usage Analyzer and have it scan your filesystem.  This is a tool that analyzes all the files and things on your HDD and shows it in a graph.  Take a look at that and see if you can find where all your space is going.

Unfortunately it's kind of hard for you to post results from that back here.  Tell us which folders or files are taking up the most space and how much they're using.

---

### Post by Ozey on 2009-09-14
It says: Total system capacity: 23.6GB (Used: 22.4GB available 1.2GB)

Total file system usage 94.9%

---

### Post by Ozey on 2009-09-14
Okay, I think that the problem is almost fixed.

When I installed Ubuntu it copied all my files and folders from Windows (Including a butt-load of videos which I didn't intend to copy).

So now I deleted them, and Ubuntu says they're in the trash, but it also says the trash is empty and even if I say empty it doesn't delete them.

So! New problem. All this space is being taken up by the trash bin by files that I'm trying to delete. Disk Usage Analyzer says that they're there, but my trash bin says its empty.

---

### Post by Ozey on 2009-09-14
Okay! After looking at other threads/forums for this sort of problem what happened was Ubuntu moved the files to a different trash bin (I didn't know there was more than one). I opened up the file, manually deleted them, and now I have all the space that I should have had in the first place! Yay! 

Thank you so much for your help! I feel like such a blonde lol. I would have never figured it out without your help :D

---

### Post by -=hazard=- on 2009-09-14
Tip* If you want to delete something without wanting it to go on trash, so we presume to permanently delete, select the file, press Shift+Delete then Ok. It will be deleted without going on trash first.
Cheers.

---

### Post by v1nsai on 2009-09-15
No problem, hope your stay in Linux gets easier.  It's not that Linux is error proof and completely stable, but it gives you the control to make it work just like you want and fix your own problems.

And FYI if that 'other trash bin' you were talking about is located at ~/.local/share/trash/files then that's the same trash can, that's just where it's located in the actual filesystem.  I had that problem before too, files that are owned by root can be tricky to deal with sometimes.  Everything you access is mounted somewhere in the filesystem though.

---

