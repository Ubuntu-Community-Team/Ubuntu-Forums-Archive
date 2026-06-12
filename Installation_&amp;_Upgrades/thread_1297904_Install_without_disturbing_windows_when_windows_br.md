---
title: "Install without disturbing windows when windows broken"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by addisondm on 2009-10-22
Hello all, I was wondering if someone would be kind enough to help me out. 
 
Is there any way to do the "install inside windows" option with ubuntu when you have no access to windows or the internet? 
 
is there a way to copy the files manually from the cd or boot from the cd and do the "install inside windows option"? 
 
I had a problem with windows getting corrupted (hal.dll missing and copying the dll back to system32 folder does not fix problem) and found that ubuntu could be installed without disturbing the windows partition...so I picked up ubuntu and find out that you actually need to be in windows to see this option?-which defeats the purpose of me installing ubuntu...:confused: is there any way I can install without disturbing windows partition by booting off the cd? I believe I have a 9.04 cd....

---

### Post by SonicSteve on 2009-10-22
I'm a bit confused as to what you think you will gain by installing Ubuntu into a broken windows installation? Perhaps someone knows of a way but my original question still stands. When and if you succeed with this project how will it help you?

Truth be told you can boot the Live 9.04 CD then use the option of resizing the windows partition, thus leaving it intact and ending up with a dual boot, Ubuntu and a bad windows install.

Edit one more thing,
If I was doing this, and a dual boot was my goal, I would boot with the Live CD, back up my data, then;
1. Re-install windows, by repartitioning the hard drive, then formatting it. During the repartitioning stage I would plan what I wanted for space on Windows and for Ubuntu. Then make the partition for windows and leave the rest unpartitioned blank space.
2. Install ubuntu by using the leftover blank space. The ubuntu install will detect windows and create a dual boot environment.
3. Copy my backup data back to the drive.

---

### Post by addisondm on 2009-10-22
I would like to fix the windows install later if I am able to rather than re-installing and keep ubuntu after. It could possibly be a simple fix for windows so re-installing it is a huge pain, I also have nowhere to back up my data... I have my genuine windows xp cd but when I go to run the install/repair I get a blue screen. So I would like to install ubuntu for now and use it until I find a solution with windows. I know I could just run it off the cd but I'd rather have it actually installed with all the software packages.
 
edit: also once my internet is working again I can create a shell account on ubuntu and go on my home computer from work to use irc hehe
 
double edit: good to see you are from brampton, im in mississauga

---

### Post by SonicSteve on 2009-10-22
To fix the windows problem,

It may just be the windows MBR master boot record

This can be fixed with a Windows CD. I'm thinking that your running XP?
You boot up the windows installation Process from the CD, then when it asks you if you want to repair an installation you say yes.

Once your at a command prompt, run the command fixmbr

it's been while since I did this but that is the basic process. Quite often the message you receive about a file missing isn't so much a missing file but a bad MBR pointing to the wrong place or no place at all.

If that doesn't fix it I would still re-install. My experience has taught me that it's most often faster to re-install than to tinker...tinker...tinker...and finally fix it. The tinker method can be rewarding when you fix it, and you learn in the process but a fresh install is a very good thing also. Cleans out the crud, starts fresh, and believe me windows needs this.


EDIT.
I've never installed Ubuntu, onto a broken windows partition, however... assuming that won't cause any trouble, my first solution of installing using the resize partition option would work. One thing though, backup your data first. If the windows problem is really caused by a dying Hard drive trying to resize it may fail and possibly data loss. 

On the possibility of installing into a broken windows installation, I don't know how possible this is unless you have another computer running windows which you had installed ubuntu into. Possibly then you could copy the virtual hard drive from one computer to the other, it's just looks like a single file if my memory serves correctly. Then you may be able to install GRUB on the broken computer and give it a boot option pointing to the virtual ubuntu install. It's a bit complicated but it might work. I'm not sure what happens during the boot process on a WUBI installation which is why I'm unsure.

---

### Post by addisondm on 2009-10-22
Hmm I was going to try fixmbr but it said it might wipe out my partitions but I guess I will give it a try. I did try to rebuild bootfg and that did not work, I also tried copying the file off a cd, I also tried copying the file from the service pack folder, and I also tried fixboot...So maybe I will try chkdsk /r and fixmbr and I will update with my progress.
 
I still do want ubuntu though lol
 
edit: see above for re-install, I cant- I get a blue screen when trying to repair or redo a fresh install

---

### Post by SonicSteve on 2009-10-22
Blue screen when trying to repair or install is a bit ugly. Can you boot into the Ubuntu Live environment?

---

### Post by Mark Phelps on 2009-10-22
> **addisondm said:**
> ...  
Is there any way to do the "install inside windows" option with ubuntu when you have no access to windows or the internet? 
Lack of internet access is not a problem, as you can install from a CD or DVD, but you can't install inside Windows because the installation has to be run from an active MS Windows session.

> is there a way to copy the files manually from the cd or boot from the cd and do the "install inside windows option"? 
Same problem as mentioned above.
 
>  confused: is there any way I can install without disturbing windows partition by booting off the cd? I believe I have a 9.04 cd....

You could shrink the Windows OS partition, create Linux partitions in the free space, and install Ubuntu that way -- but if your MS Windows OS is Vista, you need to use its Disk Management utility to do the shrinking -- so you're back to square one in that case.  IF your OS is XP, you can boot from a GParted LiveCD (which you can download from distrowatch.com) and strink the OS partion, and create new Linux partitions.

---

### Post by pricetech on 2009-10-22
> **addisondm said:**
>  I also have nowhere to back up my data.


Then get somewhere.  Seriously, if your data has ANY value at all, go out and buy a thumbdrive, external hard drive, something, to back up your date to BEFORE you do anything else.


> **addisondm said:**
> .. I have my genuine windows xp cd but when I go to run the install/repair I get a blue screen.

Sounds like a hardware issue, probably memory.  Again, back up your data before running any diags on the computer.  Booting to the CD should work no matter how botched your winders install is.

---

### Post by addisondm on 2009-10-22
> **SonicSteve said:**
> Blue screen when trying to repair or install is a bit ugly. Can you boot into the Ubuntu Live environment?
 
Yes I am able to is there a utility in there to modify partitions?

---

### Post by addisondm on 2009-10-22
> **Mark Phelps said:**
>  
You could shrink the Windows OS partition, create Linux partitions in the free space, and install Ubuntu that way -- but if your MS Windows OS is Vista, you need to use its Disk Management utility to do the shrinking -- so you're back to square one in that case. IF your OS is XP, you can boot from a GParted LiveCD (which you can download from distrowatch.com) and strink the OS partion, and create new Linux partitions.
 
My os is xp yes, I can boot into ubuntu live- can I modify the partitions there or do I need gparted?
 
The purpose of the internet by the way was to download packages as I'm not sure what comes with the ubuntu install- I am interested in programming utilities/web server etc

---

### Post by addisondm on 2009-10-22
> **pricetech said:**
> Then get somewhere. Seriously, if your data has ANY value at all, go out and buy a thumbdrive, external hard drive, something, to back up your date to BEFORE you do anything else.
 
 
 
 
Sounds like a hardware issue, probably memory. Again, back up your data before running any diags on the computer. Booting to the CD should work no matter how botched your winders install is.
 
 
I have a thumb drive but it wont hold over a terrabyte of stuff...
 
Regarding booting from the CD it copies a bunch of stuff at the beginning then it goes to blue screen-  I dont make it to the recovery console part of the install or the installation part.  Fortunately I installed recovery console locally and its one of my boot options

---

### Post by Mark Phelps on 2009-10-22
> **addisondm said:**
> My os is xp yes, I can boot into ubuntu live- can I modify the partitions there or do I need gparted?
Yes, you CAN use the Ubuntu LiveCd to do partition work.  I generally recommend the GParted LiveCd because (1) the version revised frequently, whereas the ubuntu distros are not, and (2) the GParted LiveCd doesn't mount any partitions, while the Ubuntu LiveCD does.
 
> The purpose of the internet by the way was to download packages as I'm not sure what comes with the ubuntu install- I am interested in programming utilities/web server etc
Understand, was just commenting that internet connection is not required to install Ubuntu.

---

### Post by Mark Phelps on 2009-10-22
> **addisondm said:**
> I have a thumb drive but it wont hold over a terrabyte of stuff...

Hey, I know what you mean! 

When you have terabytes of stuff (not so unusual nowadays when 1.5TB drives can be had for $100), where exactly do you back these off to?  Not everyone wants to fork out the $$ for an external multi-TB drive JUST to have around in case offline backup is needed.

---

### Post by addisondm on 2009-10-22
Does WINE come with ubuntu on the cd?

---

### Post by SonicSteve on 2009-10-22
> **addisondm said:**
> Yes I am able to is there a utility in there to modify partitions?

If you can get onto the internet from the Live CD you could install Gparted. Although I think it's part of the normal install which would mean that it's likely part of the Live CD under system>administration>partition editor

The installation process of ubuntu can do all the partition editing and shrinking you'll need.

---

### Post by addisondm on 2009-10-22
> **SonicSteve said:**
> If you can get onto the internet from the Live CD you could install Gparted. Although I think it's part of the normal install which would mean that it's likely part of the Live CD under system>administration>partition editor
 
The installation process of ubuntu can do all the partition editing and shrinking you'll need.
 
 
so I should allocate maybe 10 gb to ubuntu?
 
edit:i downloaded gparted i am going to try it when i get home from work

---

### Post by SonicSteve on 2009-10-22
> **addisondm said:**
> so I should allocate maybe 10 gb to ubuntu?

It depends on how big your drive is. By the sound of it you have at least 1Tb. I would give it 10-15 for it's system files, though my installs have never exceeded 6-8gigs. It's the swap and /home folder space to consider also. I have an 80Gb drive.
I use 10 for the system files aka / or root (yes just / ), 1024 for swap, and  the rest for /home (like Mydocs, its where the system gives you full access). I actually make 3 linux partitions
10gb /
1gb swap
whatever left for /home
In your case the files you currently have stored taking up as much room as they do, you may not be able to allocate much.  What size is your drive or drives and how much is left on each one?


You should know that resizing that disk could take a very long time. The length of time will also depend on how full the drive is. I really feel queasy about doing this before you back up at least your most important stuff. When you have as much as you do and not enough space it becomes a matter of priorities. You know you can't save it all but if you think about it there may be some things that you care about most that you do have room for.

---

### Post by pricetech on 2009-10-22
> **addisondm said:**
> I have a thumb drive but it wont hold over a terrabyte of stuff..

Ok then, here's what I'd do:
Get another hard drive.  Install whatever OS or OSs you want on it.  Put your original drive in the computer as a secondary drive and there's your stuff.

I'm assuming of course that you don't want to lose your data.

---

### Post by SonicSteve on 2009-10-22
In case you are interested my current / (system files) partition is 14Gb, and it has used 4.4Gb. So I could likely make my partition about 8Gb total and be fine.

---

### Post by addisondm on 2009-10-23
Wow nothing but constant problems... So I found a spare 160gb hard drive, I booted from ubuntu disc, installed ubuntu (9.04 i think) onto the hard drive and dedicated the entire 160gb to it.  The install completed without any problems or errors.  
 
I took out the ubuntu cd, disabled my other hard drives in the bios (2 other sata, 1 ide) and I set the 160gb hard disk to be the one that gets booted from.  I went to boot and it is like there is no operating system, it is tellin gme to enter a correct boot device and press a key.

---

### Post by Mark Phelps on 2009-10-23
> **addisondm said:**
> Wow nothing but constant problems... So I found a spare 160gb hard drive, I booted from ubuntu disc, installed ubuntu (9.04 i think) onto the hard drive and dedicated the entire 160gb to it.  The install completed without any problems or errors.  
 
I took out the ubuntu cd, disabled my other hard drives in the bios (2 other sata, 1 ide) and I set the 160gb hard disk to be the one that gets booted from.  I went to boot and it is like there is no operating system, it is tellin gme to enter a correct boot device and press a key.

Was there any other drive connected at the time? GRUB, by default, installs to the MBR of the "first" drive it finds -- which, in the case of multiple drives, is not necessarily the drive that Ubuntu installed to unless that also is the "first" drive.

---

### Post by addisondm on 2009-10-23
so i re enable all the drives and try booting off all of them?
 
did it just add a boot option or could it have messed up the booting of the other drives?

---

### Post by pricetech on 2009-10-23
Maybe I wasn't clear;  When you installed Ubuntu on another drive, did you remove your original drives first or leave them connected ???  As mentioned above, Ubuntu will install to the first drive it finds.

---

### Post by Mark Phelps on 2009-10-24
> **addisondm said:**
> so i re enable all the drives and try booting off all of them?
 
did it just add a boot option or could it have messed up the booting of the other drives?

GRUB, by default, on any system running MS Windows, will "mess up" the MBR of the first drive it finds.

You could try connecting each drive, one at a time.  The one that tries to boot GRUB is the one that had GRUB installed to the MBR.

---

