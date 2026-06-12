---
title: "How do I fix grub?"
date: 2005-12-06
forum: General Help
---

### Post by frost_ad on 2005-12-06
Ok, I won't go into the details, but, like an idiot, I deleted the ubuntu partition using qtparted running knoppix live cd. Now grub gives me an error and I can't boot into windows xp. How can I fix this so I can get into windows, backup and move some stuff and then reinstall ubuntu?

Thanks for the help,
Moronic Noob

---

### Post by Joe_CoT on 2005-12-06
Well, if you just need to get into windows, and you're going to reinstall ubuntu later, you can just pop in the windows xp cd, goto the recovery console, and use fixmbr to put the windows bootloader back on.

Alternatively, you could just reinstall ubuntu straight off, which will reinstall grub, and not mess up your windows partition at all.

If neither of those appeal to you, let me know, because there's ways to install grub manually, but i don't feel like explaining them

---

### Post by frost_ad on 2005-12-06
will the xp cd option work if all I have is a stupid system restore cd from the manufacturer? If so, I'll just do that. I guess I could reinstall ubuntu, but I wanted to get rid of it a bit to make room for a fat32 partition to share some folders between windows and ubuntu, then reinstall windows (it's been 10 months and it's screwed up) and then finally make a partition for ubuntu and reinstall it. This would be all so much easier if I could just install ubuntu and get rid of windows. But unfortunately there is some software that I have to run for some of my college classes and I need to have windows available.

---

### Post by Joe_CoT on 2005-12-06
what you could do is this: start with the knoppix cd. in fdisk (fdisk /dev/hda), delete the linux partition, create the partition for the fat32 drive, create the partition for the linux drive. then use mkdosfs to create the fat32 drive
```
mkdosfs -F 32 -v stuff /dev/hda2
```

assuming hda2 is the partition for your fat32 drive. then, mount the windows partition
```
mkdir/media/windows
mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
copy all your files to the fat32 drive (or, copy them to whatever medium you'd like).
then reinstall ubuntu, it'll install grub, and you'll be able to get into windows

---

### Post by aysiu on 2005-12-06
You obviously have access to another computer (from which you're now posting). Does this other computer have a broadband internet connection and a CD burner? If so, you can use a live recovery CD like Knoppix to recover your Windows files *and* create a FAT32 partition before doing whatever you want to do.

---

### Post by aysiu on 2005-12-06
[QUOTE=bobfnordman]
assuming hda2 is the partition for your fat32 drive. then, mount the windows partition
```
mkdir/media/windows
mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```[/QUOTE] I believe you don't have to manually mount partitions with Knoppix--they appear on your desktop, and when you click on them, they mount and open automatically.

---

### Post by frost_ad on 2005-12-06
Hey guys:
Thanks to both of you for your quick responses and help. I think I'll be able to pull it off now. The only problem I have is that I don't really have enough freespace right now to have an ubuntu partition, the windows partition as it is, and a fat32 partition to share. If I could get into windows to uninstall some programs and such I could make more room. 

But, I'll get it worked out. I may just have to back up some things to dvd until I get it all worked out.

One last question: Assuming I get everything worked out with the 3 partitions. Will I be able to do a fresh install of windows from the system recovery cd without disturbing the Ubuntu and Fat32 partitions?

Thanks again for your help.
The only thing better than Ubuntu itself is the community around it.

---

### Post by bunty on 2005-12-06
Before you go steaming off and reformatting anything , you should realise that deleting a partition alone does not affect the files and data stored there.

I you have not done anything more than deleting a partition entry with parted then you have not lost anything permanently.:D 

I have just recovered a complete dual-boot xp-suse system where the mbr got screwed up. Luck for the owner who had no backups at all !

look at this thread for more details:
[http://forums.gentoo.org/viewtopic.php?p=2916272#2916272](http://forums.gentoo.org/viewtopic.php?p=2916272#2916272)

disktest was the key tool I used , also the free version of partition recovery was invaluable for locating the start of the lost vfat.

You need to set parted to display sectors and set the partitions to start exactly where they were before else you get zilch.

HTH :cool:

---

### Post by Joe_CoT on 2005-12-06
your best bet is probably this:
1) back up your data in knoppix to dvd, or to another computer
2) delete all the partitions on the drive
3) in fdisk, make the partition for your windows install. make it only large enough to fit programs. your data you'll put on your fat32 drive.
4) pop in the windows xp disk, install onto the partition
5) in windows xp, in control panel : administrator tools: computer management: disk management, make the partitions for the fat32 drive and the linux drive, but leave them unformatted.
6) install ubuntu
7) format the fat32 drive in ubuntu
8) move your data back over

the reason you'd want to create the fat32 partition in windows and then format it in linux is simple: windows doesn't play well with others. I remembered later on while i was in class that if you create the partition in linux instead of windows, windows will refuse to recognize it. **However**, if you create the partition in windows, but format it in linux, it'll work. That will also get around the unnecessary max size that microsoft has imposed on fat32 partitions.

As for whether you'll be able to do this with your rescue disk, i'm not sure. your rescue disk may allow you to only put windows xp on a single partition; or, it may force you to wipe the whole drive. In the latter case, you'd have to use partition magic (partition *tragic*) to modify the partition size afterwards and make the fat32 and linux partition. And get a computer vendor that doesn't suck.


You can try recovering the partition table if you want, but if you're going to reinstall windows later anyway it's probably not even worth it. Plus anything that has to be linked from gentoo.org is generally surrounded with an aura of despair

---

### Post by KermitJr on 2005-12-07
[QUOTE=bobfnordman]
As for whether you'll be able to do this with your rescue disk, i'm not sure. your rescue disk may allow you to only put windows xp on a single partition; or, it may force you to wipe the whole drive. In the latter case, you'd have to use partition magic (partition *tragic*) to modify the partition size afterwards and make the fat32 and linux partition. And get a computer vendor that doesn't suck.[/QUOTE]

QTParted works well.  I've never lost data with it (unlike PQ Magic)

KJ

---

### Post by frost_ad on 2005-12-07
I like the sounds of your plan. I was hoping to avoid burning all the data to DVD, but I think you are right, and that it is the best bet I have now. Thanks again for everyone's help.

---

