---
title: "Alright, I'm installing ubuntu..."
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by V-oblvion-V on 2006-01-16
I'm finally going to install Ubuntu; but I need to keep my windows operating system for some stuff... namely games. I just have a few questions about the installation progress.

Firstly, partioning. From what I understand, linux uses a different file system to windows, and so the disk needs to be split into 2 parts - one for linux, one for windows. Is this right? If so, how do I do this when installing, without destroying the windows files that are already there?

My friend said that Linux can read the windows file system. This means I can give my windows partion the majority of the  disk space, and store all my music and videos etc on there, and Ubuntu will be able to access them. Is that right?

Finally, how do I choose which operation system to boot on start up?

Many thanks,
 - V-Oblvion-V

---

### Post by Lord Illidan on 2006-01-16
You are using FAT 32 or NTFS as your windows partition?

It is actually quite simple.
During installation, choose manual mode, and resize your ntfs/fat32 partition. Important : Do a defragment beforehand, and don't exaggerate in resizing, i.e. give it 2 gigs at least of extra space.

Then you need a partition for Linux, either reiserfs or ext3. And a swap partition, which should be twice your RAM.

Important.

Linux can read and write to FAT, but not NTFS. It can read the data, but not write to it.
At bootup, a menu will be presented, and you choose which OS to boot from.

Goodluck, and have fun

---

### Post by Sef on 2006-01-16
Here'a tutorial on how to dual boot:

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

I used it when I first installed Ubuntu, and it helped me a lot.

---

### Post by DirtDawg on 2006-01-16
[QUOTE=Lord Illidan]You are using FAT 32 or NTFS as your windows partition?

It is actually quite simple.
During installation, choose manual mode, and resize your ntfs/fat32 partition. Important : Do a defragment beforehand, and don't exaggerate in resizing, i.e. give it 2 gigs at least of extra space.

Then you need a partition for Linux, either reiserfs or ext3. And a swap partition, which should be twice your RAM.

Important.

Linux can read and write to FAT, but not NTFS. It can read the data, but not write to it.
At bootup, a menu will be presented, and you choose which OS to boot from.

Goodluck, and have fun[/QUOTE]


So is Windows XP automatically set to NTFS? I kind of figured it was, but if Linux can't write to the my Windows partition, I may be screwed. The drive I put Linux on is only 4.1 Gigs, which I figured was fine because I could save files on the Windows drive. Am I understanding correctly that this isn't possible?

---

### Post by newuser111 on 2006-01-16
[QUOTE=DirtDawg]So is Windows XP automatically set to NTFS? I kind of figured it was, but if Linux can't write to the my Windows partition, I may be screwed. The drive I put Linux on is only 4.1 Gigs, which I figured was fine because I could save files on the Windows drive. Am I understanding correctly that this isn't possible?[/QUOTE]

you could use captive ntfs if you are willing to take the risk, some people can use it without any problems

---

### Post by DirtDawg on 2006-01-17
I can take absolutely no risks. I'm probably screwed, but I suppose I can still fit a fair amount on 2 gigs or so. Anyways, at least I get to use Linux whilst hooked to the internet now.

---

### Post by goatflyer on 2006-01-17
What I did was create an additional FAT partition which both Windows and Linux can both read/write.  I am sharing files between my dualboot win2k / ubuntu system.

---

### Post by tmahmood on 2006-01-17
@DirtDawg If you have Powerquest Partition Magic then you can convert a NTFS partition to Fat32. or there is a tool named "convert" in Windows you can use that too. I am not sure about its parameter guess you'll have to find that your self. 
@goatflyer how do you set a fat32 to write. I want to write to a fat32 as a normal user. How can I do that?

---

