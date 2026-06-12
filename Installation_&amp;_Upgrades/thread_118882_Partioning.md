---
title: "Partioning"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by WSTGangsta on 2006-01-17
I hear alot of people saying they can partion their hard disks to run both Windows and ubuntu (or other distro) on the same PC. How do I do that? Because using the live CD annoying because all my settings are erased after I exit, and it saves everything to my small amount of RAM. If this is possible let me know, and tell me any risks involved,

---

### Post by guy_smiley:) on 2006-01-17
Yes it is possible. Using the same hard drive that windows is installed in (if you're only using one hard drive) or by installing Ubuntu on another hard drive. When you install any distro of linux, it comes with a boot loader (can be LILO or GRUB). This boot loader will determine which OS your system will boot to. These setttings can be changed, obviously. A little reading into this may help. (Quite simple really, changing one file, as long as you find out the right commands).

Simply, when you install linux if you are only using one hard drive; or only want to install OS's on one hard drive, then you must repartition your current hard drive. I'm actually looking into this atm, since I don't want to have to reinstall windows. Otherwise you can reinstall windows and when you do, break your hard drive up into two partitions (one for windows, one for linux; or more for linux if you're into that, little more comlpex) when installing (it gives you this option). Basically you should be able to install it with litttle trouble. If this is a little confusing, I'll be back in a minute.

---

### Post by DoorGunner on 2006-01-17
Running windows and linux is refered to as dual booting. This will depend on if you have enough hard drive room free. For instance in my case i have windows and ubuntu on a 200 Gb hard drive. I divided it in to 3 partitons. One for windows about 80Gb, one for Ubuntu about 80 Gb and one for a share file about 40Gb. I decided on a share drive because it could be a space where i can keep files, mp3s photos etc that i use in both Ubuntu and Windows. You can choose how much you use and for what.

If you are getting your feet wet and just trying linux you might want to to just use 30 Gb. This will give you enough room to download some options and be big enough to expand. However, once again it will depend on what you choose. You can certainly do it on less space as well.

I personally used a tool called partition magic to do this. However, Ubuntu has an installation tool that will do it for you as well. 

Grub is a program that handles you boot. In this i mean whether or not you start windows or Ubuntu. Both cannot be started at the same time.

maybe you can let us know what you were thinking you might like to do then we can help you further.

---

### Post by slowlearner on 2006-01-17
first partition your hardrive, using any partitioning tool or you can use 
the one packaged with ubuntu... 

after partitioning, install  windows first on the partition of your choice..
then install ubuntu on the other...after installation ubuntu will install a 
bootloader(grub) which can switch you between your installed os's on boot-up...
thats it!

---

### Post by Sef on 2006-01-18
This is an excellent tutorial on how to Dual Boot:

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

---

### Post by WSTGangsta on 2006-01-18
Wow you guys are very helpful, but is there any way to do this without re-installing windows?

---

### Post by az on 2006-01-18
[QUOTE=WSTGangsta]Wow you guys are very helpful, but is there any way to do this without re-installing windows?[/QUOTE]
By default, the Ubuntu installer will detect your current OS and offer to partition your drive for you to dual boot.  It is very safe.

I would think that most people who are migrating from Windows do this.  Maybe upwards of 90 percent of the people here on the forums do that?

---

### Post by Topsiho on 2006-01-18
I am not sure how safe it is to use the partitioner that the Ubuntu install offers for resizing (here: making smaller) a used windows partition. Anyway I think that before one does this, this partition should be defragmented, as otherwise information is maybe scattered all over this partition and the resizing may not be successful and/or data is lost.

I therefore have used Partition Magic to make room on my disk to receive the Linux installs that I did.

I am not so happy though with PM as I suspect that it does eerie things with the partition tables.

This is my tuppence as I wanted to tell you about defragmenting first, just before the repartitioning :)

Topsiho

---

### Post by az on 2006-01-18
[QUOTE=Topsiho]I am not sure how safe it is to use the partitioner that the Ubuntu install offers for resizing (here: making smaller) a used windows partition. Anyway I think that before one does this, this partition should be defragmented, as otherwise information is maybe scattered all over this partition and the resizing may not be successful and/or data is lost.

[/QUOTE]
The installer is very safe.  It wil refuse to partition a drive if there is the risk of data loss.

If you try to install and it refuses to partition, then go and try to defragment.  Otherwise, parted and libntfstools can defrgament for you.


By and large, the partitioner is the same for all linux distributions and I think it is responsable for the majority of the partitioning of ntfs drives today.  The need to partitoin an NTFS drive is not so large otherwise.  So it is used a lot.

---

### Post by Topsiho on 2006-01-19
Thanks azz,

I'll keep this answer in mind for next time I need it.
I hope that you're right :)

Topsiho

---

### Post by 504harry on 2006-01-19
[QUOTE=Topsiho]I am not sure how safe it is to use the partitioner that the Ubuntu install offers for resizing (here: making smaller) a used windows partition. Anyway I think that before one does this, this partition should be defragmented, as otherwise information is maybe scattered all over this partition and the resizing may not be successful and/or data is lost.

I therefore have used Partition Magic to make room on my disk to receive the Linux installs that I did.

I am not so happy though with PM as I suspect that it does eerie things with the partition tables.

This is my tuppence as I wanted to tell you about defragmenting first, just before the repartitioning :)

Topsiho[/QUOTE]

Good point about Defrag.
The next Q is answered thus: Linux doesn't appear to need Defrag - any housekeeping is done without you noticing.
Linux filesystem is said to be "better"
However, I have read that you should only mix Win?Linux if no other option is available.
So might I suggest before you do anything you COPY your data to CD and have all the program/driver discs for windows, just in case? **Then** Defrag.

---

### Post by az on 2006-01-19
[QUOTE=504harry]Good point about Defrag.
The next Q is answered thus: Linux doesn't appear to need Defrag - any housekeeping is done without you noticing.
[/QUOTE]

Actually, the partitioner's NTFS library can move some data around, AFAIK.  You don't always need to defragment your drive first.  As for linux filesystem, there is no "housekeeping" in the sense of a daemon running in the background which will defragment your filesystem.  It is just how the filesystem works that minimises fragmentation.
 
[QUOTE=504harry]

However, I have read that you should only mix Win?Linux if no other option is available.

[/QUOTE]
Not true at all.  You can easily run both on the same box.  I think this is actually the most common setup for ubuntu users.

[QUOTE=504harry]
So might I suggest before you do anything you COPY your data to CD and have all the program/driver discs for windows, just in case? **Then** Defrag.[/QUOTE]

Whenever someone brings me their box for an ubuntu dual-boot install, I always insist they back up their data first.  The Ubuntu installer has never failed me, but it is just common sense.

---

### Post by WSTGangsta on 2006-01-19
So heres what I am understanding:
I can just use the install CD and it will just guide ,me through the process and these is little to no risk of data loss.

---

### Post by Herman on 2006-01-20
I agree with azz, the Ubuntu installer partitioner is very safe and there is little or no risk of data loss caused by the software.
If you are reasonably careful and have had a look at the website sef gave you then that should help you to be informed in advance of what sort of questions you will be asked and what choices you will be offered, and what you can expect to happen next. 
After that you should find it very easy to install Ubuntu 'dual boot' with Windows.
If you don't find it easy, let me know what it is you found difficult or confusing and I will rectify the /hermanzone/ 'Ubuntu Dual Boot' website to make it clearer for anyone following in your footsteps in the future. :D (Herman).

---

### Post by Heretic Monkey on 2006-01-20
Another noob in the area....

I already have a partition on my main hard drive (well, it actually seems to be a "Windows Virtual Hard Drive", or something like that).  Unfortunately, it's a FAT32 system.  Is it possible to install Ubuntu to this file system, or will i have to create a new partition?

Another question.  I have about 20 gigs of music/video/programs through my Windows OS.  If i repartition, is there a large threat that i'd lose this info? 

Also, what's this about a shared folder?  I've run Knoppix before, and it was able to recognize and access all the files on the Windows partition.  If i dual boot w/ ubuntu, would i need to create another partition to store the files that can be interchanged?

---

### Post by az on 2006-01-20
[QUOTE=WSTGangsta]So heres what I am understanding:
I can just use the install CD and it will just guide ,me through the process and these is little to no risk of data loss.[/QUOTE]
Yes, but that is not a reason to not backup you important data!

That's just common sense....

---

### Post by az on 2006-01-20
[QUOTE=Heretic Monkey]Another noob in the area....

I already have a partition on my main hard drive (well, it actually seems to be a "Windows Virtual Hard Drive", or something like that).  Unfortunately, it's a FAT32 system.  Is it possible to install Ubuntu to this file system, or will i have to create a new partition?[/QUOTE]

You will just create an ext3 filesystem on that partition...


Anoth[QUOTE=Heretic Monkey]er question.  I have about 20 gigs of music/video/programs through my Windows OS.  If i repartition, is there a large threat that i'd lose this info? 
[/QUOTE]

It is a good idea to back up your data...  One slip of the fingers.....  But partitioning is very safe.

---

