---
title: "Windows wont load after installing 9.10 as side by side"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by KinKiac on 2009-11-10
Hello everyone.  I have run into a bit of a problem.  I have been using Ubuntu since 9.04 without any major problems, nothing I couldnt fix.  Then I upgraded to 9.10, again without any real problems.  

However, this past weekend I decided to show Ubuntu to my dad on his home PC.  He's always been open to Linux although hadnt really tried any of the newer distros, so I thought Id let him try Ubuntu.  

We tried out the live cd which seemed to work fine, so I decided to do a full install for him.  He already had windows vista installed on a single 200g drive so we had to select to install Ubuntu side by side windows, where Ubuntu resizes the partition and installs grub for a dual boot.

After install Ubuntu worked fine, although my dad only has dial-up where he is living and so couldnt update or connect to the internet.  This wouldnt have been a problem, as I was able to download Keryx on my home PC and was going to get all his updates plus some other software.  

Unfortunately today he went to go into windows and when he selects the windows loader from the grub menu he gets an error saying "error reading disk".  He can see the windows partition in Ubuntu fine and can even mount it and get into all the files fine, just wont load windows.  

Is there anyone out there who might know what went wrong and/or how I might try to fix it?  Any help at all would be greatly appreciated.  

Thanks

---

### Post by cariboo on 2009-11-10
I don't know if this will help, but try running:

```
sudo update-grub2
```

to see if that solves the problem.

---

### Post by KinKiac on 2009-11-10
Will this command work on his PC if he has no internet?

---

### Post by jamesrfla on 2009-11-10
Yes it will

---

### Post by KinKiac on 2009-11-10
Ok cool, Ill give that a try, thanks a lot guys!

---

### Post by KinKiac on 2009-11-10
Well guys.... it looks like we will never know if that simple update command would have worked on my Dad's PC.  Unfortunately he is like me, and just cant leave stuff alone, lol.  Since I found out about the issue earlier today he decided when he got home form work to try to fix the issue.  However, he knows next to nothing about linux, so he tried fixing things the windows way.  He decided, after I told him it probably wouldnt work, to run his PC recovery disks for windows.  In doing so he first killed the ubuntu installation, and then it killed his windows too, formatting the drive and then only doing a partial recovery.  Im assuming it ran into issues when the recovery disk figured out the partitioning table had changed and then couldnt read the rest of the disk, so it stopped giving the same error as before "error reading disk"  

So, again thanks a lot for the help, but we arent going to be able to go any further with this.  Its a good thing my dad didnt have anything too important on his PC that he cant get back, and is actually taking things quite gracefully.  He is not turned off Ubuntu at all even though he lost some stuff and now has to reload everything.  He's decided to leave the PC as is for now(I hope), until I can get over there on my days off on the weekend, and then Im going to re-install either XP or maybe windows 7 for him.  Only this time I am going to create the Ubuntu partition BEFORE we install windows, that way we wont have to deal with any issues regarding the partitioning table or resizing the disk or anything that would cause an issue with his windows(he still needs it for certain programs, although Im hoping to change that.)

Thanks Guys!

---

### Post by crosspicker on 2009-11-10
I just wanted to jump in here and give you a quick heads up on installing Ubuntu first and then Windows, be aware that if you're not carefull windows will re-install the MBR, then you won't be able to boot into ubuntu until you reinstall GRUB. 

Just in case you weren't prepared for this before you start.

---

### Post by Mark Phelps on 2009-11-11
OK, so the next time you try this, do NOT allow the Ubuntu installer to shrink the Windows 7 partition!  This runs the risk of corrupting the OS partition such that it will no longer boot.

If you had used the Windows 7 disk management utility to shrink the partition and then used manual partitioning in the Ubuntu installer -- you would have a working dual-boot system now.

---

### Post by kinmye on 2009-11-12
Emm .. I am reading Mark advice too late.
I have already installed ubuntu, as kinkiac. And vista does not boot.
Any advice? Do you recommend 
sudo update-grub2
Thanks a lot!

---

### Post by kinmye on 2009-11-12
Reading my post, I don't know if it is clear enough.

I had a computer with Vista.
I have installed ubuntu 9.10. I have selected the partition size from the the ubuntu installer (not using windows tools). And as a result, now I cannot boot vista.

I am considering to follow the information on here:

[URL="http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"]http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD
[/URL]
Basically: burn a CD that boots vista and allows to reintall vista loader (MBR).
If I succeed, I will try to configure the vista loader (using information in linux partition, /boot/menu.lst ) or just delete de ubuntu partition and start again in the proper way.

Thank you!

---

### Post by Mark Phelps on 2009-11-12
That recovery CD allows you to run Startup Repair in an attempt to rebuild the boot loader files and the BCD store.  You may have to run it several times -- it takes more than one pass to fix everything.

If you go to the NeoSmart Technology website and check under EasyBCD support, you'll find some tutorials for doing boot loader repair.  You might (as I did recently) have to resort to using the Windows RE command line interface to fix the boot -- how's that for irony!

---

### Post by kinmye on 2009-11-12
ok. Finally I have got vista & ubuntu running! 

This is what I have done:
- Burn the Vista Recovery CD (just 130Mb) from the address in my previous post.
- Boot from the CD. There is a menu, to select which system to repair .. but no items in the menu ... no system have been detected.
- Anyway, press continue, ... start working and after aprox. 15 min. it says it is ok.
- Reboot, select vista from grub. Then it appears a menu with option "repair system" or normal boot.
- I have selected repair. A tool similar to the one in the  CD starts. After 15 min. it says it cannot repair the system.
- Reboot again with CD. Now, the menu is not empty: the vista O.S has been detected. But I cannot continue. The repair utility states that the version on the hard disk and the version on my CD are different ones --ask to include the original recovery disk, which I do not have--
- Reboot from the hard disk: the idea was to run again "repair". In the instructions from neosmart.net they say "The automated repair only fixes one thing at a time, and you might need several things fixed ...", so I wanted to try again ...
- But, for my surprise, after the grub menu, selecting vista ... It starts correctly!! I don't know who (first or second repair) has fixed the whole thing, but now both ubuntu and vista can be selected from grub menu and are working properly.

---
I admit it is my fault not to have shrinked the disk from vista before installing ubuntu. 
On the other hand, IMHO, it is a ubuntu failure that the installer allows to make a partition that can corrupt vista loader. It should have been advised: "if this is vista, please shutdown now!! You should shrink the disk from vista" (or just: please do some googling about how to install ubuntu +vista".

---

### Post by kinmye on 2009-11-12
Mark: thank you for the information

By the way: I wanted to save menu.lst from linux, to configure the vista bootloader, as they say in the neosmart.com web page. But I have not found this file (maybe grub2 has been installed ??, there is a directory in /etc/grub/...). But as I said, there was no need to install any other system for booting. Grub (or grub 2, or whatever) has been always there and finally the vista option has worked.

---

### Post by KinKiac on 2009-11-12
> **crosspicker said:**
> I just wanted to jump in here and give you a quick heads up on installing Ubuntu first and then Windows, be aware that if you're not carefull windows will re-install the MBR, then you won't be able to boot into ubuntu until you reinstall GRUB. 

Just in case you weren't prepared for this before you start.

Actually Ive done this many times before with 9.04 and have made that mistake before.  Windows was already installed in this case.  Its a big pain in the *** from MS's side really, it will even overwirte the MBR of you are installing windows on a totally separate drive.  

> **Mark Phelps said:**
> OK, so the next time you try this, do NOT allow the Ubuntu installer to shrink the Windows 7 partition!  This runs the risk of corrupting the OS partition such that it will no longer boot.

If you had used the Windows 7 disk management utility to shrink the partition and then used manual partitioning in the Ubuntu installer -- you would have a working dual-boot system now.

Actually I couldnt do that.  I dont think you read my post correctly.  My dad already had a vista preload on his hard drive, on a store bought, pre-configured PC.  We tried Ubuntu form the live cd and then decided to try the full installation.  I didnt have a choice but to tell Ubuntu to install along side windows and resize the partition because there was no other drives or partitions to use.  I knew this would run the risk of corrupting the windows side but I was hoping with the new version of Ubuntu they would have had this act pretty down pack considering any new user to ubuntu is going to choose this option, its the only one they have if they have a store bought PC with a windows preload and no extra drives. 

Im not bashing Ubuntu or anything I love it and use it as my primary OS.  But Im a computer guy with like 4 partitions on a 320gig drive, plus an extra IDE drive, plus I might consider getting a couple terabyte drives as well and see if I can set them up as raid 5.  My dad and many others out there who are just normal users would only have 2 options when installing ubuntu - side by side, which opens them up to the issues I ran into, or using the whole disk which wipes out their windows.  Its too bad they run the same risk regardless of what option they choose.

EDIT: Im actually going back to my dads this weekend to install windows again, however this time since we can do a clean install of windows I can partition the drive so that there is an extra partition for ubuntu Before we even install windows and we wont run into this problem again.  The issue is with a store bought PC that only has one partition and Windows preloaded.

---

### Post by Mark Phelps on 2009-11-12
> **KinKiac said:**
>  ... I didnt have a choice but to tell Ubuntu to install along side windows and resize the partition because there was no other drives or partitions to use...

Not to belabor this, but OF COURSE you had a choice -- to come to these forums to find out about what you were about to do, and the risks -- BEFORE charging ahead and hoping for the best.

Unless your machine already had 4 primary partitions, all filled up (and I am SURE it did NOT), you had the choice of:
1) Using the Vista Disk Management utility to shrink the Vista OS partition to make room for Ubuntu
2) Using the Ubuntu LiveCD to then create Linux partitions in the free space
3) Installing from the Ubuntu CD but using Manual Partitioning to reuse the partitions you just created.

> I knew this would run the risk of corrupting the windows side ... Then all the more reason you should have hesitated and come here for advice, first.

These same steps have been posted again and again and again in this forum. A simple 5-minute search would have revealed LOTS of posts about these.

The Linux world is all about the freedom to make your own choices.  But with that freedom comes some responsibility -- to do some research before you go charging ahead into something you clearly don't understand.

> My dad and many others out there who are just normal users would only have 2 options when installing ubuntu - side by side, which opens them up to the issues I ran into, or using the whole disk which wipes out their windows.  Its too bad they run the same risk regardless of what option they choose.

BTW, I personally agree that the Ubuntu installer should provide strong warnings about the possible damaging side-effects of allowing it to shrink Vista partitions -- but I'm one lone, small voice in a huge community, surrounded by folks who seem to feel that any cautionary words are tantamount to Linux-bashing!

---

### Post by KinKiac on 2009-11-13
> **Mark Phelps said:**
> Not to belabor this, but OF COURSE you had a choice -- to come to these forums to find out about what you were about to do, and the risks -- BEFORE charging ahead and hoping for the best.


Actually it was my dad that was more charging ahead then me, but whatever, lol.  

> 
Unless your machine already had 4 primary partitions, all filled up (and I am SURE it did NOT), you had the choice of:
1) Using the Vista Disk Management utility to shrink the Vista OS partition to make room for Ubuntu
2) Using the Ubuntu LiveCD to then create Linux partitions in the free space
3) Installing from the Ubuntu CD but using Manual Partitioning to reuse the partitions you just created.


Maybe but oh well.  Also, i didnt realize there was a vista disk utility that could do that.  At least not one built into the system, if Id have known that i would have done so.  

Unfortunately I just didnt see anything anywhere that said "do not use the side by side option in Ubuntu installer" so I assumed it was ok.  Oh well, not a big deal.

---

### Post by crosspicker on 2009-11-16
I've never tried installing Ubuntu by resizing a Vista install, but I have done it many times with an XP install both at work and at home and never had a problem with the Ubuntu partitioner. I've also used GParted on a bootable cd to resize both windows and Ubuntu partitions and never ran into a problem with that either, but I also have never tried it with Vista. I do have Windows 7 and makes me wonder if I'll have the same problems if I resize those partitions, but I guess that will be a topic for a future post.

---

