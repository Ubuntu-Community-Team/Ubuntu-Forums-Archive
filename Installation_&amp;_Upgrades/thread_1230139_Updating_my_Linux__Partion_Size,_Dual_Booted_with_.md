---
title: "Updating my Linux  Partion Size, Dual Booted with M$'s OS"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by therocco2k on 2009-08-03
I've had Windoze on my computer for some time. I'm now Dual Boot with Ubuntu, I love it. I Didn't think I would need that much space in linux because I figured I'd only be doing a little programming in it but, hell - I'd like to do away with the Windows except for the gaming aspect and use Linux Ubuntu for everything else! Now i have 140GB of HD Space left on Windows, and only 20GB on Linux! I want to Add Triple that to Llinux and make them even.

When I set up Ubuntu, I downloaded the live dvd to a blank dvd from the ubuntu site, vista was already isntalled. Then I did the standard boot from the DVD-ROM and into ubuntu install and partitioned my disc space via ubuntu partioner.

However I did read a guide to help, and before I did anything I downloaded a Windows Program that Pre-Clears some of your Windows Space into extra space - I Forget the name but it cleared the 20GB from being windows partioion to raw space... 

How can I go back to make this happen change, Is there a Step by Step way to do this? :confused:

Thank you for your help, I really want to make Linux my MAIN OS from now on out, since i tend to become a IT or System Admin Guy for carrer (23yrd male, all self taught - (not to brag heheh: PHP,mysql, java developer, even hope to develope my own flavor of Linux one day.. ha. I'll look back at this forum and take suggestions from everybody because this forum is Very useful to all levels of Unix Linux users.

Thank you for your time, I'd appreciate this extra space ALOT, and here's my testiment to the Linux Community - Have a Laugh I Hope? Anybody?:

[IMG]http://www.fatbottoms.net/extra/linuxownswindoze.jpg[/IMG]

Hehe - Thanks

---

### Post by therocco2k on 2009-08-03
Can somebody please tell me how to enlarge my Current Ubuntu Filesystem Partition? I have Dual Boot with Vista, but Linux is the default system.

---

### Post by merlinus on 2009-08-03
Use vista's disk management tool to shrink its partition.  Delete temp files and empty temp directories, and defrag several times first.

Then you can use gparted on the live ubuntu cd to add the freed-up space to linux.  Depending upon whether it is a primary or logical partition, you may have to resize the extended partition first.

---

### Post by therocco2k on 2009-08-03
Actually I have no problem making partitions and adding OS's to them, I have 3 Questions

1.) How do I Safely resize the remaining 140GB of Windows Partition
and
2. )How do I ADD that extra SPACE to an already Created Linux OS Partition?
3.) Would I have to re-install Ubuntu?

I'm going to add my Entire MySQL DATABASES to Linux, which is in excess of 50GB and I only have 20gb left on my linux partition

Thank you so much

---

### Post by merlinus on 2009-08-03
If you can shrink vista enough, another option is to format the freed-up space as an ext3 partition, and keep your databases there.

As for temp files, most are preceded by a tilde (~).  There are temp directories in the vista system and user folders.

If you do not defrag, you will not be able to shrink it nearly as much as if you do.

---

### Post by therocco2k on 2009-08-04
> **merlinus said:**
> If you do not defrag, you will not be able to shrink it nearly as much as if you do.

Yes, I went into Vista - Disk Management and tried to Shrink the C Volume partition - It opened the box but the Available MB for shrinking was 0, and the shrink field wouldn't let me type any MB to Shrink it. I Did a Windows Disk Cleanup (No more then 5-10mb were deleted) - Then I downloaded Diskeeper and did a Manual Defragmentation, that Eliminated Approx. 5,742 Fragments, and it's Automatic Non-Stp[ Defrag is Running now (is constantly defragmenting in the background while Wind0ze is open). Here's Before and After Analysis Shots of the C Drive Diskeeper defragged.

**Before:**
[IMG]http://www.fatbottoms.net/extra/before.jpg[/IMG]:

**After**:
[IMG]http://www.fatbottoms.net/extra/after.jpg[/IMG]


I Went back to the Disk Managment to try and Shrink the Drive Down again, and it still wont let me shrink it a mb. I mean I can select Shrink, but it doesnt let me shrink any space... The First Time i did it was when I went to install Linux - I Shrank it for a 40GB Partition, now I'm down to like 15GB and declining... I need more space for my work in Linux

I have 140GB left on that drive alone out of a 250GB HDD Left, why would this happen? What do you think?_ I read that it stops you from shrinking your drive to a certain extent and that is not a problem or error but a Windows "FAEATURE"_ A Feature that stops you from taking EXCESS space off my remaining 140 GB  partition is horrible, I added linux so I wouldnt have to deal with these winderderders Issues.

Does anybody have a solution to add more space to my Ubuntu Linux Partion?

Thanks againm 
Rocco 
Ninja-marketing,net

---

