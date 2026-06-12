---
title: "Captive NTFS"
date: 2005-11-28
forum: General Help
---

### Post by Killerah on 2005-11-28
Hey guys, new Ubuntu user here, and I'm loving it to death. For the most part I'm a pretty big linux n00b, but I've tried a few different distros (Debian, Knoppix, etc.) and so far this one is the only one that has worked perfectly with everything I've tried to do so far (and that's about a days worth of setting stuff up). So I'd like to say, thanks to the team behind this great distro, and thanks to the community for that helpful wiki. I will certianly be sticking with Ubuntu for a good while.

Anyway, all praise aside, I'm here to ask if it's safe to use the Captive NTFS wrapper (or whatever it's clasified as) because acording to [this](http://www.jankratochvil.net/project/captive/#download) page you have to unmount it in a certian way (by using the "unmount(8)" command) or I might end up losing data and stuff. What does this mean, and is there any way I can edit the shutdown script to include this command or something? Also, does anyone else have any captive experiences to share? Is it possible I'll experience any data loss using this if I unmount it that certian way?

Thanks alot guys,
Nate

---

### Post by djselbeck on 2005-11-28
Hi,

if used it but it was a really bad solution for the NTFS problem. If you copy or read big files it became slower every second and pump your ram up with garbage. the only good solution is the paragon NTFS driver but it is commercial so you must consider what you want a very slow driver or a really fast near to 1:1 driver or the third only read access.

;)
DJSelbeck

---

### Post by Killerah on 2005-11-28
Hmm, ok well, my dad has a copy of partition magic, would you recommend that I just convert my NTFS to FAT32? Would that screw things up in Windows? Also, do you know if partition magic supports converting ext3 to ReiserFS? I've heard ReiserFS is better.

---

### Post by almahtar on 2005-11-28
I've been wondering about Reiser myself.  As far as the NTFS stuff, sorry to jump into the topic without any useful info, I guess I'm just encouraging anyone with EXT3 vs. Reiser info to speak up :-)

I'm pretty much keeping my NTFS access from Linux to a minimum to avoid having to deal with the potential data loss.  There's nothing I care about on my Windows partitions anyway other than games that currently won't run in Linux because I fail misserably at chrooting and there's no amd64 wine port yet.

I'd recommend you install the freeware ext2 drivers for Windows (there are many drivers, but most are open source.  I've found the freeware closed source ones rock!), and just store everything of importance on your ext2 partition.  It's working great for me.

---

### Post by Killerah on 2005-11-28
Yeah, well, I think I'm just going to convert the partition to FAT32 using partition magic. Anyway, I did some googling, and I couldn't find anything that would help me convert from ext3 to reiserfs but an experimental method which I don't want to mess with. So, I guess now I would like to ask this: I have another partition with plenty of space, could I copy everything to that partition, format the partition ubuntu is currently on to reiserfs and then move everything back without any more configuration? Would I need to redo grub and stuff?

---

### Post by chaumurky on 2005-11-28
Remember that FAT32 has no journalling and permissions support.

---

### Post by jonny on 2005-11-29
[QUOTE=chaumurky]Remember that FAT32 has no journalling and permissions support.[/QUOTE]...and can't handle large files, either.  This may well be a very bad idea.

---

### Post by chaumurky on 2005-11-29
I know theres a great piece of (non free) software by Paragon called "Mount Everything" for Windows. My mum uses it for her dual boot system. You make an ext3 partition in Linux, install "Mount Everything" in Windows and it lets you mount the partition as a drive letter. It works flawlessly and is quite fast too. Best of both worlds.

---

### Post by Killerah on 2005-11-30
Well, I've never had any problems with FAT32 before, I think I'll go ahead and convert it anyway, and keep it that way until vista and WinFS come out. Anyway, I'm really loving my Linux experience with Ubuntu, about 3 days in and everything that hasn't been too terribly adventurous has worked flawlessly. It's so impressive that this level of an operating system can be put together by just a bunch of people on the internet and then distributed for free! 

Anyway, I was just thinking, is there some way that I could "remaster" an install cd like you can do with knoppix for live cds? Because I have downloaded a whole bunch of cool packages and everything's set up nice, and I was hoping that there could be some way to perhaps just put those packages on a self installing disc or something. That would be very nice because I don't want to have to download all that stuff every time I install Ubuntu on a new computer.

So, either way, thanks a ton for your help guys! Ubuntu owns!

-Nate

---

### Post by aysiu on 2005-11-30
[QUOTE=jonny]...and can't handle large files, either.[/QUOTE] My guess is the most people won't mind not being able to have files bigger than 4 GB (unless they also have DVD burners). My biggest file is about 8 MB.

---

