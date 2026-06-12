---
title: "Partition Magic shows BAD partition after Ubuntu install"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by zero64 on 2005-07-03
Hi, I just got done installing Ubuntu for the 3rd time in the past week or so. The first two times were on my new 300GB SATA hard drive--I backed up and deleted everything on it when Partition Magic said the drive was bad (I wish I could remember the exact error--I think it may have said something about the partition table, or disk geometry).

Anyway, I thought that was a one-time fluke, but when I installed Ubuntu again on my 160GB PATA drive, Partition Magic showed basically the same thing, that the disk is bad, though without the error message this time (see the attached image).

Does anyone know of a way to fix this? Do you think it's just a problem with Partition Magic, or is there actually something wrong with the disk, caused my the Ubuntu installation, or some combination of it and my use of Partition Magic?

Edit: The operating systems (Linux/Windows XP) seem to be able to read from the drive fine.

Any assistance is appreciated.

Thanks,
Sam

---

### Post by Omnios on 2005-07-03
I read that Partition magic could possibly corrupt a partition table and aperently this happenes a lot as there are a lot of post of such. Personaly I used QTparted in Linux to resize my patition on a 120G Western Digital EIDE drive and it worked well (not shure if it can repair you tables.

This is the thread of what I did.
[http://ubuntuforums.org/showthread.php?t=45605](http://ubuntuforums.org/showthread.php?t=45605)

Also did you chdisk -r before partitioning this is known to cause problems if you have bad sectors etc.

Id do a chdisk -r remove the blank space and try remaking the main partition though I have no idea how!

---

### Post by dickohead on 2005-07-03
Partition Magic 8 only recognises ext2/3 partitions, so if you formated in something like ReiserFS it might show up as bad? Although more likely it should show up as unknown... I would do as suggested above and try another program, then see what happens.

But if you can boot into Ubuntu and Windows - then who cares what Partition Magic says?

---

### Post by zero64 on 2005-07-04
Thanks for the replies.

> But if you can boot into Ubuntu and Windows - then who cares what Partition Magic says?
Well, this is my feeling to some extent. It's just that I like using Partition Magic.

I used Window's disk management tool to delete Ubuntu's swap partition and replace it with a FAT32, and then PM quit complaining (incidentally, it still showed a problem when I left it as free space). I haven't booted into Ubuntu again yet, but perhaps I can just recreate the swap partition using PM.

My guess is that Partition Magic and the partitioner used in the Ubuntu install just don't get along very well; I suppose that's not totally unexpected since I've read several times on this forum not to mix partitioning tools.

---

### Post by dickohead on 2005-07-05
[QUOTE=zero64]Thanks for the replies.


Well, this is my feeling to some extent. It's just that I like using Partition Magic.

I used Window's disk management tool to delete Ubuntu's swap partition and replace it with a FAT32, and then PM quit complaining (incidentally, it still showed a problem when I left it as free space). I haven't booted into Ubuntu again yet, but perhaps I can just recreate the swap partition using PM.

My guess is that Partition Magic and the partitioner used in the Ubuntu install just don't get along very well; I suppose that's not totally unexpected since I've read several times on this forum not to mix partitioning tools.[/QUOTE]
 you could always try the latest version of Partition Magic (now ownde by symantect) and see if it has issues?

---

### Post by az on 2005-07-05
Partition magic will eventually go away.

With the setup you are running (and most other setups) there is no reason to use a proprietary disk partioner when the free alternatives do a perfect job,

---

### Post by zero64 on 2005-07-07
In Linux, sure, the free partitioner is fine. Do you know of a good free alternative for Windows though?

---

### Post by ad noiseam on 2005-07-27
I have the exact same problem as the original poster, and would really like to be able to repair my HD, as I need to change some things with the various NTFS partitions on it (I have several NTFS partitions on it, as well as the Linux ones).
Has anybody been able to solve this problem?

---

### Post by aveline on 2005-07-27
[QUOTE=ad noiseam]I have the exact same problem as the original poster, and would really like to be able to repair my HD, as I need to change some things with the various NTFS partitions on it (I have several NTFS partitions on it, as well as the Linux ones).
Has anybody been able to solve this problem?[/QUOTE]
 First off... PM works fine *if* you patch from ver 8 to 8.1 I think it is.  To the person who said, free utils work fine... no they do not always work fine... I've used a few and some have their own quirks.  I found a way around some of this, see below.

Secondly ignore PM saying its BAD.  Update Xp to sp2, patch PM 8 (don't use a ver lower than 8 btw) & do NOT let it make ext2/3 partitions for you to install any linux onto... just make free space.  

Thirdly if you do NOT have PM, I use an old Mandrake cd (the first one of the set) to partition things off.  Go thru their setup, get to partitioning (its as intuitive as PM's) & when you're done and its said, written to disk just quit & reboot.  Done.  Install linux flave of choice.

aveline

---

### Post by az on 2005-07-27
[QUOTE=aveline]First off... PM works fine *if* you patch from ver 8 to 8.1 I think it is.  To the person who said, free utils work fine... no they do not always work fine... I've used a few and some have their own quirks.  I found a way around some of this, see below.

Secondly ignore PM saying its BAD.  Update Xp to sp2, patch PM 8 (don't use a ver lower than 8 btw) & do NOT let it make ext2/3 partitions for you to install any linux onto... just make free space.  

Thirdly if you do NOT have PM, I use an old Mandrake cd (the first one of the set) to partition things off.  Go thru their setup, get to partitioning (its as intuitive as PM's) & when you're done and its said, written to disk just quit & reboot.  Done.  Install linux flave of choice.

aveline[/QUOTE]

The ubuntu partitioning tool is the same as the mandrake one.  So we get back to the original point that Partition Magic is the problem here.


ad noiseam:  You can use the Ubutu installer partitioner to move your partitions around.  It can resize ntfs partitions.

---

### Post by ad noiseam on 2005-07-28
[QUOTE=azz]ad noiseam:  You can use the Ubutu installer partitioner to move your partitions around.  It can resize ntfs partitions.[/QUOTE]

How can I access the installer's partitioner once Ubuntu is already installed and running?

---

### Post by az on 2005-07-28
Well, it is best to partition an unmounted drive anyway, so booting from the installer allows you to run from ramdisk without mounting your harddrive.  


Just boot and make your way to the partitioner.  Quit after you have made your changes.

---

