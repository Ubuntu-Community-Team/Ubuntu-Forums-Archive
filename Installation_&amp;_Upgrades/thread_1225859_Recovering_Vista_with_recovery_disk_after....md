---
title: "Recovering Vista with recovery disk after..."
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Suff on 2009-07-29
Is it still possible to run the recovery disks to reinstall vista to factory settings that came with my computer after I have installed Ubuntu over the complete drive partition?

I was wondering because vista crashed on me after I tried to run "Gateway Recovery Management" and wasn't able to boot again. So I installed Ubuntu which didn't recognize any other OS's on the drive. What I want to do is restore vista then install Ubuntu 32bit. 
(Currently running Ubuntu 64bit) :(

I still have four days or so until the recovery disks arrive so I'm a bit worried. This is probably more windows related but help would be appreciated. Enjoying playing "Mines" in the mean time.

---

### Post by hyperAura on 2009-07-29
well if u did format the whole partition before installing ubuntu i highly doubt that ur gonna succeed something with the recovery disks.. u'll probably need the vista installation disk to get it back working again..

---

### Post by Suff on 2009-07-29
Well i noticed some old files from vista in the "Filesystem" directory, but under properties it says some contents unreadable.

Is this only part of ubuntu?

---

### Post by ularlaut on 2009-07-29
In my office we are using HP g3635d Desktop PC's, which has a Recovery Management Software factory installed.

Before I installed Ubuntu on the PC, I run the Recovery software that automatically make Backup CD/DVD of the systems.

The Software says that the CD's / DVD's can be used to recover my PC System only by booting from it.

However, they (HP/Compaq) also stated that the recovery can be run successfully **IF** the recovery Partitions in the HardDisk is still intact (unchanged), which is "partially" hidden.

And when we installed Ubuntu, we only delete the primary partition for used by Ubuntu, we did not touch the other partitions.

We actually never try to recover from Ubuntu to Vista, since Ubuntu is running well in our system and environment.

So,  my opinion from your question / problem is that you may have a 50-50 chance of fully recover your system.

Hope my comment helps.

regards,

---

### Post by coffeecat on 2009-07-29
It probably depends on how your manufacturer set things up. My Sony laptops came with only recovery partitions, but I was able to make recovery DVDs with the system. And the recovery DVDs can be used to completely reformat the hard drive and reinstall Windows, **and** create a new recovery partition. That's true of both my older XP laptop and newer Vista one.

If your manufacturer is any good the recovery disks *should* be able to reformat the hard drive before installing Windows, so  the presence of Ubuntu will not matter.

That's if your manufacturer is any good, of course.

If you find that the recovery disc is looking for a NTFS partition and can't make one itself, there is a possible solution. Boot up with an Ubuntu live CD, go to System > Administration > Partition Editor (Gparted), delete all the partitions on the hard drive and create a NTFS partition for the recovery disc to use for installing Vista. However, I would hope the recovery disks are programmed to create both the standard recovery partition and C: partition in their factory condition.

---

### Post by Mark Phelps on 2009-07-29
> **Suff said:**
> ... So I installed Ubuntu which didn't recognize any other OS's on the drive...

Didn't the fact that the install didn't detect Vista tell you something was wrong?  This should clue you in to what you most probably did was wipe the partitions on your drive when you installed Ubuntu.

> What I want to do is restore vista then install Ubuntu 32bit. (Currently running Ubuntu 64bit)

Given that you are receiving recovery disks (plural), if you only have one disk now, it most probably was supposed to boot you into a recovery partition -- which probably doesn't exist anymore.

So, you won't be able to restore until you get the disks.

---

### Post by omegaweapon on 2009-08-06
I'm curious to know if this worked or not.  Back when I tried dual booting with Open SUSE, I screwed up the MBR during the installation and had to use the Vista Recovery Disks to restore the OS.  However, after restoring the OS, I noticed that my drive was still partitioned the way I had it before I attempted to dual boot.  This just makes me think that the recovery disks don't write over a linux partition / repartition to factory settings.

Long story short, did the recovery disks get Vista back on your computer?

---

### Post by lisati on 2009-08-06
The Toshiba M200 laptop I currently use (one of the Satellite range) shipped with only a recovery partition. I was able to make a set of recovery DVDs with software that came preinstalled. When one day I decided I wanted a clean install of both Vista and Ubuntu, the recovery disks worked without problems.

---

