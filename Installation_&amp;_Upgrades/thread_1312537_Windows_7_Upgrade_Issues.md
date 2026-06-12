---
title: "Windows 7 Upgrade Issues"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Noobs*McGee on 2009-11-03
Hi,

So those of you who read my previous thread know that I was trying to reinstall Windows XP on my computer.  I ended up doing so, doing a clean install from the restore disc that came with my computer.  However, initially after installing Windows, I was unable to boot to it, because I kept getting GRUB Error 17, which I assumed had something to do with changes that had been made to the MBR when I had installed Ubuntu.  Anyway, not knowing a thing about the MBR or how to make changes to it, I decided I would reinstall Ubuntu, configuring it to dual boot with Windows, thinking it might fix the booting issue.  I was right.
Problem is, after reinstalling Ubuntu, I then updated Windows XP to Windows 7, and now my computer boots directly to Windows without providing the choice to boot to Ubuntu.  So now my question(s):

Is there a way to fix GRUB so it will prompt to select an OS at startup (as it was doing before the Windows 7 upgrade)?  Would reinstalling Ubuntu again fix the problem?  If yes to the latter, how would I go about removing the first Ubuntu installation, so that I don't have two installations of Ubuntu on my HDD?

Also, when I reinstalled Ubuntu after restoring Windows, I didn't allocate as much space as I wanted to Ubuntu (I just ran the default install, which gives Ubuntu like 2.5GB).  I want Ubuntu and Windows to have equal size partitions.  If it is possible to remove the old Ubuntu install and then reinstall, would resizing the Windows partition on install (in gparted) be okay?  And if it's not possible to remove the old Ubuntu install and reinstall (but it is possible to fix the GRUB loader) would it be possible to change the space allocated to each partition without messing up either installation (Windows or Ubuntu)?

Can someone please get back to me on this one?  Several of my previous posts here have received virtually no response, and if I don't get a response on this, I will likely not be using Ubuntu on this computer again (which would suck).  Your help would be greatly appreciated.

--NM

---

### Post by sliketymo on 2009-11-03
> **Noobs*McGee said:**
> Hi,

So those of you who read my previous thread know that I was trying to reinstall Windows XP on my computer.  I ended up doing so, doing a clean install from the restore disc that came with my computer.  However, initially after installing Windows, I was unable to boot to it, because I kept getting GRUB Error 17, which I assumed had something to do with changes that had been made to the MBR when I had installed Ubuntu.  Anyway, not knowing a thing about the MBR or how to make changes to it, I decided I would reinstall Ubuntu, configuring it to dual boot with Windows, thinking it might fix the booting issue.  I was right.
Problem is, after reinstalling Ubuntu, I then updated Windows XP to Windows 7, and now my computer boots directly to Windows without providing the choice to boot to Ubuntu.  So now my question(s):

Is there a way to fix GRUB so it will prompt to select an OS at startup (as it was doing before the Windows 7 upgrade)?  Would reinstalling Ubuntu again fix the problem?  If yes to the latter, how would I go about removing the first Ubuntu installation, so that I don't have two installations of Ubuntu on my HDD?

Also, when I reinstalled Ubuntu after restoring Windows, I didn't allocate as much space as I wanted to Ubuntu (I just ran the default install, which gives Ubuntu like 2.5GB).  I want Ubuntu and Windows to have equal size partitions.  If it is possible to remove the old Ubuntu install and then reinstall, would resizing the Windows partition on install (in gparted) be okay?  And if it's not possible to remove the old Ubuntu install and reinstall (but it is possible to fix the GRUB loader) would it be possible to change the space allocated to each partition without messing up either installation (Windows or Ubuntu)?

Can someone please get back to me on this one?  Several of my previous posts here have received virtually no response, and if I don't get a response on this, I will likely not be using Ubuntu on this computer again (which would suck).  Your help would be greatly appreciated.

--NM

 Here is some good info:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I do not believe threatening to leave will cause too many tears.That is your choice.

---

### Post by dhavalbbhatt on 2009-11-03
> **Noobs*McGee said:**
> Hi,

So those of you who read my previous thread know that I was trying to reinstall Windows XP on my computer.  I ended up doing so, doing a clean install from the restore disc that came with my computer.  However, initially after installing Windows, I was unable to boot to it, because I kept getting GRUB Error 17, which I assumed had something to do with changes that had been made to the MBR when I had installed Ubuntu.  Anyway, not knowing a thing about the MBR or how to make changes to it, I decided I would reinstall Ubuntu, configuring it to dual boot with Windows, thinking it might fix the booting issue.  I was right.
Problem is, after reinstalling Ubuntu, I then updated Windows XP to Windows 7, and now my computer boots directly to Windows without providing the choice to boot to Ubuntu.  So now my question(s):

Is there a way to fix GRUB so it will prompt to select an OS at startup (as it was doing before the Windows 7 upgrade)?  Would reinstalling Ubuntu again fix the problem?  If yes to the latter, how would I go about removing the first Ubuntu installation, so that I don't have two installations of Ubuntu on my HDD?

Also, when I reinstalled Ubuntu after restoring Windows, I didn't allocate as much space as I wanted to Ubuntu (I just ran the default install, which gives Ubuntu like 2.5GB).  I want Ubuntu and Windows to have equal size partitions.  If it is possible to remove the old Ubuntu install and then reinstall, would resizing the Windows partition on install (in gparted) be okay?  And if it's not possible to remove the old Ubuntu install and reinstall (but it is possible to fix the GRUB loader) would it be possible to change the space allocated to each partition without messing up either installation (Windows or Ubuntu)?

Can someone please get back to me on this one?  Several of my previous posts here have received virtually no response, and if I don't get a response on this, I will likely not be using Ubuntu on this computer again (which would suck).  Your help would be greatly appreciated.

--NM

What version of Ubuntu have you had installed on your machine? The reason I ask is, if you are still on 9.04 (Jaunty) or less, then you should have GRUB 0.97, for which I know how to get your GRUB re-installed. If you are however, on 9.10 (Karmic), then you will most likely have GRUB 2.0 installed - for which I am not sure how to get that re-installed. 

For Grub 0.97, it should be like this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


For your second concern, about re-sizing your partitions, that should be simple - use your Gparted, using the LiveCD (this is the Ubuntu installation CD that you would have created to install Ubuntu), under System -> Administration and you can re-size your partitions. I am assuming you know how to use a LiveCD.

---

### Post by julianb on 2009-11-03
I have never tried this and I don't know much about windows 7, but...


1. As far as I know there is no problem installing Ubuntu for dual-boot use, on a machine that has Windows 7 already installed.

2. The way that I would delete a previous copy of Ubuntu from the hard drive is to boot a liveCD as though you wanted to try out Ubuntu without installing. Mount your Linux hard drive partition.

your hard disk is probably called hda OR sda
second hard drive, if present, probably called hdb or sdb

you can find out the name of your linux partition using this command: (you may guess at the hard drive name till you get it right)

```
sudo fdisk -l [hard drive name]
```

look for the partition with ext4 or ext3 as the filesystem type. probably hard-drive-name followed by a number, like sda5 or sda2. Then use the following command

```
sudo mount /dev/[partitionName] [location to mount drive]
```

you may replace [location to mount drive] with the following [i think!]
```
~/
```
if that doesn't work, you can try using ```
/usr
``` as the location to mount the drive


you may delete all files from the mounted hard drive by going to the location in which the drive is mounted 
```
cd [location where drive is mounted]
```
and deleting all of the files.
(look up the "rm" command and notice the "recursive" option. you can learn about a particular command by doing a google search for "man [command-name]")

---

### Post by Fatman_UK on 2009-11-03
Windows installs its own bootloader whether you want it or not. The thing to do is boot the Live CD and reinstall the GRUB bootloader. (What dhavalbbhatt said, basically.)

[EDIT]

[http://ubuntuforums.org/showthread.php?t=1310896](http://ubuntuforums.org/showthread.php?t=1310896) has some Grub 2 information.

---

### Post by Noobs*McGee on 2009-11-03
> **sliketymo said:**
> Here is some good info:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I do not believe threatening to leave will cause too many tears.That is your choice.
That link is virtually a novel, it would take me hours to sort through all that to even figure out what in there was supposed to relate to my problem.  Was that really supposed to be helpful?
And I clearly wasn't "threatening to leave", I was lamenting the fact that if I can't resolve this problem I CAN'T continue to use Ubuntu.  Thanks for the condescension though.

 

> **dhavalbbhatt said:**
> What version of Ubuntu have you had installed on your machine? The reason I ask is, if you are still on 9.04 (Jaunty) or less, then you should have GRUB 0.97, for which I know how to get your GRUB re-installed. If you are however, on 9.10 (Karmic), then you will most likely have GRUB 2.0 installed - for which I am not sure how to get that re-installed. 

For Grub 0.97, it should be like this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


For your second concern, about re-sizing your partitions, that should be simple - use your Gparted, using the LiveCD (this is the Ubuntu installation CD that you would have created to install Ubuntu), under System -> Administration and you can re-size your partitions. I am assuming you know how to use a LiveCD.


Thanks for the HELPFUL response, dhavalbbhatt.  I should have mentioned that I installed Ubuntu 9.04, so I guess it's GRUB 0.97.  I have to go to class soon, so I don't really have time right now, but I will try out the method in your link later today.

As for using gparted in the LiveCD, this will resize the partitions without affecting either installation?

Thanks again for your response, I really appreciate it!

-NM

---

### Post by Mark Phelps on 2009-11-03
> **Noobs*McGee said:**
>  ... As for using gparted in the LiveCD, this will resize the partitions without affecting either installation?

There have been reports of GParted corrupting Vista OS parititions when it was used for resizing; Windows 7 is too new for any reports either way.  To be safe, you should burn a Recovery CD using the Windows 7 built in feature. That way, if you do encounter post-resizing boot problems, you have a CD for fixing them.

---

### Post by Noobs*McGee on 2009-11-03
Hey guys,

I used the method described in the link for restoring GRUB and everything seems to be working fine now :KS

I haven't tried resizing the partitions yet though, as I'm not sure if it will work: when I open gparted in the LiveCD, it shows the Windows ntfs partition /dev/sda1, and the extended partition /dev/sda2 with the Linux ext3 partition /dev/sda5 and the linuxswap partition /dev/sda6 as subpartitions (see below).  The first thing that stumped me is, if I resize the Windows partition, do I then copy the ext3 partition to the newly freed space and delete the old partition, or am I supposed to copy the /dev/sda2 (extended) partition (which contains the ext3 and the linuxswap)?  Also, for some reason the /dev/sda2 partition and the linuxswap show as "mounted" even though I'm running the LiveCD, so I can't copy the ext3 partition (hence the little keyrings next to the partitions in the image).

Thank you guys for your help so far, I really appreciate it.  I hope someone can help me through the rest of this.

Thanks much,
-NM

[IMG]http://img689.imageshack.us/img689/425/screen001s.jpg[/IMG]

---

### Post by phillw on 2009-11-03
> **Noobs*McGee said:**
> Hey guys,

I used the method described in the link for restoring GRUB and everything seems to be working fine now :KS

I haven't tried resizing the partitions yet though, as I'm not sure if it will work: when I open gparted in the LiveCD, it shows the Windows ntfs partition /dev/sda1, and the extended partition /dev/sda2 with the Linux ext3 partition /dev/sda5 and the linuxswap partition /dev/sda6 as subpartitions (see below).  The first thing that stumped me is, if I resize the Windows partition, do I then copy the ext3 partition to the newly freed space and delete the old partition, or am I supposed to copy the /dev/sda2 (extended) partition (which contains the ext3 and the linuxswap)?  Also, for some reason the /dev/sda2 partition and the linuxswap show as "mounted" even though I'm running the LiveCD, so I can't copy the ext3 partition (hence the little keyrings next to the partitions in the image).

Thank you guys for your help so far, I really appreciate it.  I hope someone can help me through the rest of this.

Thanks much,
-NM

[IMG]http://img689.imageshack.us/img689/425/screen001s.jpg[/IMG]

One of the best tutorials I've found for GP is here ...[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Yes, there is a bit to read - but it will explain WHY you are doing things. Hope it helps you thru the last bit of your resizing.

read the intro, then go to re-sizing !!!!!

Phill.

---

### Post by Noobs*McGee on 2009-11-04
Hi phillw, 

Thanks for the link, there was a lot of good info in that article.  However, I'm still a little confused about how I should go about resizing.  I understand the process in the context of the example in the article, but I'm still not clear on a couple things in my specific instance.   First, why do the extended partition and swap partition on my drive show as "mounted" when I'm using the LiveCD?  Are they just always like that?  And since they are locked, how do I go about resizing (growing) the Linux partition?  I basically just want to make the Windows partition smaller (around 45GB) and increase the size of the Linux partition (to roughly the same size).  As informative as the article was, it didn't really go into depth on this sort of thing...
If anyone can clear this up for me, it would be a huge help.

Thanks,
-NM

---

### Post by Noobs*McGee on 2009-11-05
*bump*

Any partitioning experts out there?  I'd like to get this taken care of so I can start using Ubuntu normally again...

---

### Post by Mark Phelps on 2009-11-05
Having done LOTS of partitioning operations, I would strongly recommend the following:
1) Do NOT, repeat NOT, use GParted to resize your Vista OS partition.  Use the disk management tool in Vista to do this.  Yeah, I know that tool sucks, but if it refuses to shrink your partition beyond a certain point, it has good reasons for that refusal.  Using GParted to ignore those reasons is only going to corrupt your Vista OS partition.
2) Download and burn a GParted LiveCD from distrowatch.com and boot from that to do partitioning.  It won't mount ANY partitions when it loads -- so you won't run into the "mounted partitions" problem.

---

### Post by Noobs*McGee on 2009-11-05
Hey Mark,

Thanks for the heads up about partitioning Windows (I'm running Win7, not Vista, but I'm assuming the same applies to both).  I'm glad you pointed that out too, because the amount of space Win7 says is available to shrink is significantly smaller than what GParted showed as available (i.e. GParted would have shrunk it to a smaller size than Win7 indicates it can be shrunk to).  I think you probably saved me from a serious headache.

I will try using a GParted LiveCD when I have some time later, thanks for the suggestion/link.  I will let you know how it turns out.  Just to be clear, do I want to copy the extended partition (containing the ext3 and linuxswap logical partitions) to the newly empty space and delete the old ones?  Or do I want to go about this some other way?

Thanks,
NM

---

### Post by phillw on 2009-11-05
> **Mark Phelps said:**
> Having done LOTS of partitioning operations, I would strongly recommend the following:
1) Do NOT, repeat NOT, use GParted to resize your Vista OS partition.  Use the disk management tool in Vista to do this.  Yeah, I know that tool sucks, but if it refuses to shrink your partition beyond a certain point, it has good reasons for that refusal.  Using GParted to ignore those reasons is only going to corrupt your Vista OS partition.
2) Download and burn a GParted LiveCD from distrowatch.com and boot from that to do partitioning.  It won't mount ANY partitions when it loads -- so you won't run into the "mounted partitions" problem.


Yikes !!! Thanks for the heads-up on that one, It is also the recommended route for apc (I used their thread for my dual boot) 

I had a spare partition kicking around on my system, so didn't have that issue - It's nice that apc also follow that advice. End of day, their tutorial works - So, it is good advice

+1 Mark  :D

Phill.

---

### Post by phillw on 2009-11-05
> **Noobs*McGee said:**
> Hi phillw, 

Thanks for the link, there was a lot of good info in that article.  However, I'm still a little confused about how I should go about resizing.  I understand the process in the context of the example in the article, but I'm still not clear on a couple things in my specific instance.   First, why do the extended partition and swap partition on my drive show as "mounted" when I'm using the LiveCD?  Are they just always like that?  And since they are locked, how do I go about resizing (growing) the Linux partition?  I basically just want to make the Windows partition smaller (around 45GB) and increase the size of the Linux partition (to roughly the same size).  As informative as the article was, it didn't really go into depth on this sort of thing...
If anyone can clear this up for me, it would be a huge help.

Thanks,
-NM


Just re-read the thread, the link I use for apc is lurking over here --> [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Phill.

---

### Post by Noobs*McGee on 2009-11-06
I'm confused :confused:  That link seems to be a guide for installing Ubuntu alongside Windows.  I already have both Windows and Ubuntu installed, I just want to make the partition that Windows is on smaller and the partition that Ubuntu is on bigger (so that each OS has roughly the same space allocated to it on my hdd).  I now know to use the built in Windows utility to shrink that partition, now I'm just trying to figure out exactly how to go about resizing the Ubuntu partition.   I reread the previous link you gave me and I am still unclear on the specific approach I need to take to accomplish this.  My instinct would be to copy the Ubuntu partition to the space that is opened up by resizing the Windows partition, then delete the old Ubuntu partition and resize the new one to fill the extra space.  Is this the correct approach?  Or am I thinking this is simpler than it actually is?  Or better yet, am I making it too complicated?

---

### Post by phillw on 2009-11-07
> **Noobs*McGee said:**
> I'm confused :confused:  That link seems to be a guide for installing Ubuntu alongside Windows.  I already have both Windows and Ubuntu installed, I just want to make the partition that Windows is on smaller and the partition that Ubuntu is on bigger (so that each OS has roughly the same space allocated to it on my hdd).  I now know to use the built in Windows utility to shrink that partition, now I'm just trying to figure out exactly how to go about resizing the Ubuntu partition.   I reread the previous link you gave me and I am still unclear on the specific approach I need to take to accomplish this.  My instinct would be to copy the Ubuntu partition to the space that is opened up by resizing the Windows partition, then delete the old Ubuntu partition and resize the new one to fill the extra space.  Is this the correct approach?  Or am I thinking this is simpler than it actually is?  Or better yet, am I making it too complicated?

For your Win7 install, I'd head over here --> [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

So, shrink your partition for the windows area that way, then use gparted to expand your ubuntu area.

1)  BACKUP YOUR DATA 
2) Shrink your Win area as above
3) Use Gparted to grow your ubuntu area. 

Resizing partitions on live (i.e. your working computer)  systems is not for the faint of heart. Mine have allways gone fine, but that'll be because I back up EVERYTHING before I do it. The day I do NOT backup will the day it all goes horribly wrong.

If you want a severe headache on Gparted, it's over here -->>  [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)   I'd suggest reading the introduction.

Other horrors that can occur are here, for vista --> [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Do take your time and get an understanding of it. Brain surgery on hard disks is not best carried out after a night at the pub !!!

Phill.

---

### Post by Noobs*McGee on 2009-11-08
lol, thanks for the response and warnings phillw.  I'm very familiar with Murphy's Law, so it's always my first instinct to back everything up before making significant changes to my computer (hence the protracted plea in my previous thread asking how best to back up my Ubuntu installation).  I will be sure to make another backup disc of my Windows install, and I haven't been using Ubuntu yet since reinstalling, so the last backup I did is still current).

I will give the GParted LiveCD a try when I get some free time (and a sober head ;)) and I'll let you know how it works out.

Thanks a bunch for all your help!

--NM

---

### Post by phillw on 2009-11-09
> **Noobs*McGee said:**
> Hi phillw, 

Thanks for the link, there was a lot of good info in that article.  However, I'm still a little confused about how I should go about resizing.  I understand the process in the context of the example in the article, but I'm still not clear on a couple things in my specific instance.   First, why do the extended partition and swap partition on my drive show as "mounted" when I'm using the LiveCD?  Are they just always like that?  And since they are locked, how do I go about resizing (growing) the Linux partition?  I basically just want to make the Windows partition smaller (around 45GB) and increase the size of the Linux partition (to roughly the same size).  As informative as the article was, it didn't really go into depth on this sort of thing...
If anyone can clear this up for me, it would be a huge help.

Thanks,
-NM

For vista and Win7 use the M$ utility to shrink the M$ partition, there have been issues noted with using Gparted. Once you have 'told' windows to shrink, GParted will allow you to grow your Ubuntu partition. Once again, apc's tutorial can 'hold your hand' on doing it.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm?viewall=1](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm?viewall=1)

Do, however, take a backup of your important stuff. Power outrages, pestilence & floods can really mess up a repartitioning operation. 

Phill.

---

