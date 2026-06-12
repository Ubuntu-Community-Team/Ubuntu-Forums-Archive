---
title: "A Bit Jittery About Ubuntu IDE Disk Migration to SATA  Drive for Multi-Booting"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by casparov on 2009-01-28
Hi, Everyone...  

I am currently configured w/ a 500GB SATA drive booting W98 (not really used anymore) and W2K SP4; I have a 100GB Ubuntu IDE drive that is currently unconnected.  My SATA drive does not now contain GRUB.  

I would like to dual boot Ubuntu and Windows again but do not, like most people, wish to reinstall all the apps on my Ubuntu 8.04 IDE drive, which I would have to do if I simply (and maybe this would be best) used the live CD route and reinstalled GRUB and a fresh copy of Ubuntu 8.10 onto the SATA drive.  

Does anybody have an idea of how I could copy my Ubuntu IDE drive to a new LINUX partition on the SATA drive?  Is there a tried and true procedure for this?

Many thanks to anyone reading this and/or replying to it.

Always trying to find the easy way out, 

Casp.

---

### Post by tommcd on 2009-01-29
> **casparov said:**
>  
Does anybody have an idea of how I could copy my Ubuntu IDE drive to a new LINUX partition on the SATA drive?  Is there a tried and true procedure for this?


There is a program called **clonezilla** that should be able to do this:
[http://clonezilla.org/](http://clonezilla.org/)
You could hook up the IDE drive that contains Ubuntu and clone the Ubuntu install onto a spare partition (assuming you have a spare partition) on the sata drive. There is also a clonezilla live CD that would probably be good for this purpose:
[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)
I have never used clonezilla, so you will have to read the documentation on the clonezilla site to learn how to use it.

You will then have to update grub to account for the Win 98 and Win 2K on the sata drive. You clould just run **sudo update-grub** after you clone Ubuntu onto the sata drive. Or reinstall grub from the live CD. Or add the Windows entries manually, which would be something like:
```

title Windows 2K
rootnoverify  (hdX,Y)
savedefault
makeactive
chainloader    +1

```
Replace X and Y with the partition number of Windows. Remember that grun starts numbering partitions from zero.

If I was doing this I would probably just do a clean install of Ubuntu 8.10 onto the sata drive. But you do have the option of using clonezilla.

---

### Post by casparov on 2009-01-29
TOMMCD...

Thanks a million for your reply.

Your last injunction about how you would just perform a clean install of 8.10 got my attention.  If someone as savvy as are you would just start over, then maybe I should, also.  

I do have an additional question re the clonezilla route.  Would I be able to use the Ubuntu Live CD to create a LINUX partition on the SATA drive, to which I could then use Clonezilla to copy the Ubuntu IDE partition?  

Thanks so much, 

Casp

---

### Post by tommcd on 2009-01-29
> **casparov said:**
> TOMMCD...
I do have an additional question re the clonezilla route.  Would I be able to use the Ubuntu Live CD to create a LINUX partition on the SATA drive, to which I could then use Clonezilla to copy the Ubuntu IDE partition?  


If you need to make a partition to install Ubuntu on the sata drive you could use a GParted or Parted Magic live CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://partedmagic.com/](http://partedmagic.com/)
The root partition will likely need to be at least as big, or bigger, than the root partition on the IDE drive that you are cloning. Also make a swap partition (2X RAM upt o 1GB). You can also make a separate home for your files. Then just clone the Ubuntu 8.04 root partition from the IDE drive onto the sata drive. Then update grub and you should (hopefully) be good.

---

### Post by casparov on 2009-01-29
TOMMCD...  

Thanks a million for the update and clarification.  I will try your recommendation this weekend and report the results. 

Sorry to be so thick about this, but when you say, in the final step, that I should clone and be good to go, are you saying that the cloning should be via clonezilla, or would a Windows program, like Seagate's Disk Wizard, be able to recognize and to clone the IDE partition to the SATA?

Thanks again, 

C.

---

### Post by tommcd on 2009-01-30
You should be able to clone 8.04 from the IDE drive to the sata drive with Clonezilla. BTW, a new version of Clonezilla just came out today.

---

### Post by casparov on 2009-01-31
Tommcd... 

Thanks so much for that last, and I will reply w/ results.  

Casp

---

### Post by casparov on 2009-02-04
TOMMCD... 

Well, thank-you for the heads up re GParted--the ISO ran beautifully and reclaimed 125GB of NTFS space on my SATA drive, turning that into "unallocated space", which, in turn, I used (through GParted) to create a "Linux-Swap" partition of the same size.  (I take it that "Linux-Swap" is the terminology that Gparted uses for both a Linux partition and a swap partition to use for installation of the OS.)  

This brings me to this query: first, is cloning the same thing as copying?  (I take it that copying means copying data, program, and system configuration settings and placing them within a partition or space which may, potentially, be larger than the source drive; while cloning means taking all the partition attributes and recreating that partition elsewhere.)  This is relevant because GParted allows one to copy a partition by unmounting it then copying and pasting it to another location.  If I can simply copy and paste my Linux partition in this fashion, then that is what I will do (because the new Linux partition created by GParted is larger than the original IDE Linux partition.)  Second, if that made sense (?), could I perform that operation then, as you indicated, simply use the Ubuntu Live CD to reinstall GRUB?

Finally, provided I can do these things, what happens when my Linux boot meets the new hardware I have on my current PC?  (The Linux IDE was a slave within a more modest system.)  Although all the components on my new PC are Linux compatible (I saw to that ahead of time), am I relegated, after all this, to a new install in light of the hardware surprises my original Ubuntu install will meet in the new machine?

Thanks again (and again and again),

Casp

---

### Post by tommcd on 2009-02-04
> **casparov said:**
> I take it that "Linux-Swap" is the terminology that Gparted uses for both a Linux partition and a swap partition to use for installation of the OS.)
A swap partition is just swap. The swap partition is analogous to virtual memory in Windows. It is used to swap out programs to a hard drive swap partition if all your RAM is used up. You need at least a root partition and a swap partition. A better setup is a root, swap, and home partition for your files.
> **casparov said:**
> 
This brings me to this query: first, is cloning the same thing as copying?  (I take it that copying means copying data, program, and system configuration settings and placing them within a partition or space which may, potentially, be larger than the source drive; while cloning means taking all the partition attributes and recreating that partition elsewhere.)  could I perform that operation then, ...as you indicated, simply use the Ubuntu Live CD to reinstall GRUB?
Copying is not the same thing as cloning. Cloning involves creating an exact image of the old drive to the new drive. The first page of this article explains the difference:
[http://www.pcstats.com/articleview.cfm?articleID=418](http://www.pcstats.com/articleview.cfm?articleID=418)
You can then reinstall grub from the Ubuntu live CD and everything should (hopefully) work. I have never done this myself though; but I have heard that Clonezilla works well.
> **casparov said:**
> 
Finally, provided I can do these things, what happens when my Linux boot meets the new hardware I have on my current PC?  (The Linux IDE was a slave within a more modest system.)  Although all the components on my new PC are Linux compatible (I saw to that ahead of time), am I relegated, after all this, to a new install in light of the hardware surprises my original Ubuntu install will meet in the new machine?

Ubuntu should bootup just fine on the new system. The only issue you may have is that, as an example, if the old PC had a nvidia card and the new PC has a ati card, you would need to install the ati 3D driver to get direct rendering enabled. Other than 3rd party driver issues like that you should be good.

---

### Post by casparov on 2009-02-06
TOMMCD...  

You saved me quite a bit of frustration in pointing out that the GParted Linux-Swap partition was just that.  I deleted it through the GParted interface and left the remaining space "unallocated". 

GParted is an amazing program--both for what it does, and the fact that it is free.  Anyone working in the dark due to lack of experience (like me) would be well advised to use this program when playing w/ PC partitions. 

Instead of using Clonezilla I simply copied and pasted (GParted's terms) the Ubuntu partition onto the SATA drive into the unallocated space I created earlier.  GParted left me w/ an invitation to expand that partition the full length of the unallocated space (using a simple arrow/slider) and I did.  It copied the partition and verified the integrity of the process before closing.  I couldn't believe how simple it was.

I haven't reinstalled GRUB but will do so from the 8.10 Live Cd I burned recently.  From what I understand all I need do is run that CD and, from the terminal it provides, enter a couple of commands after "sudo grub".  (I hope that's true.) 

Anyway, I will report the final results and many thanks, again.  I hope that this series of posts will help another. 

Regards,  

Casp

---

### Post by casparov on 2009-02-06
I don't know how I do it, but I ran into a mess w/ the last, supposedly easy, stage of all this. 

After attempting to reinstall GRUB (I used the "sudo grub; find /boot/grub/stage1; root (hd0,5); setup (hd0) routine) I rebooted after the reinstall appeared to go w/o error. 

Upon finding the GRUB boot list I selected 8.04 Ubuntu and was greeted by the intractable (for me) "error 21: selected disk does not exist".  

I found on other forum replies that a problem seems to exist when migrating to SATA disks, or something. Anyway, I then tried installing 8.10 from the Live CD and nearly made perilous changes to the size of my main Windows partition.  I quit the install but impaired the size of my first partition, an unused W98 area.

Is there any way to fix the Ubuntu boot error 21?  I am not really literate in Linux command line syntax, so any very complicated fix will not be good for me.  

It may be that I should just wipe out my copied and pasted 8.04 partition and start over w/ 8.10.  (I noticed that the installation for 8.10 asked whether it should import user settings from my "sda6" disk, which is the copied Ubuntu 8/04.  Perhaps this gives me the best of both worlds.)

Just a bit flummoxed here...  

C.

---

### Post by tommcd on 2009-02-06
> **casparov said:**
> 
After attempting to reinstall GRUB (I used the "sudo grub; find /boot/grub/stage1; root (hd0,5); setup (hd0) routine) I rebooted after the reinstall appeared to go w/o error. 
Upon finding the GRUB boot list I selected 8.04 Ubuntu and was greeted by the intractable (for me) "error 21: selected disk does not exist".  

A (hopefully!!) easy fix for grub issues would be to try and reinstall grub from the Super Grub disc:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
> **casparov said:**
> 
It may be that I should just wipe out my copied and pasted 8.04 partition and start over w/ 8.10.  

That is what I would have done from the get go. You could install Intrepid in less than 30 minutes. Then perhaps another hour to reinstall all your programs and configure things, and you would be done with it. I have always done clean installs rather than upgrades. I have installed and configured Ubuntu so many times that I can get it done very quickly. I don't consider the little bit of downtime to be a problem. And if you install from the Live CD you can browse the net while it is installing.

Also, if you do not have have a separate home partition, this would be a good time to create one. Then the next time you install Ubuntu your partitions are already set up, so you can skip the partitioning and just select your root and swap partitions for the install, choose /home as the mount point for your home partition, and go right into the install.

---

