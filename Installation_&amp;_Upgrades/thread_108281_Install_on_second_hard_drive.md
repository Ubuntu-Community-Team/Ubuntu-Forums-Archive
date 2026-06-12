---
title: "Install on second hard drive"
date: 2005-12-25
forum: Installation &amp; Upgrades
---

### Post by marlis56 on 2005-12-25
I am trying to figure our how to use the Install CD on a second HD. My boot HD is C:\ with Windows98.  My second HD is partitioned as D:\ and E:\ 
How should I proceed to install Ubuntu on the D:\ partition of my second HD?

---

### Post by exile on 2005-12-25
The first thing that I would do is from in windows, using fdisk, get the size of the different partitions. Write this down on paper.

In linux the disks and partition will be referred to as:

\dev\hda1 this is usually the C: Drive for most machines

after that
\dev\hda2 would be the sceond partition on the first drive, hda3, hda4 and so on.

\dev\hdb1 is the first partition on the second device. I'm making the assumption that both disks are on the same IDE cable.

SATA disks will be labelled like /dev/sda1, sda2, sdb1 and so on.

When it comes time to set linux up, use the size of the the partition information that you got from windows and use that to guide you when you get the ubuntu disk paritioner. You will need to set the partition up manually rather than putting it on auto pilot. DON'T install it on /dev/hda1 if that is your C: - it should say that the filesystem type is ntfs or fat32 - leave that one be.


As with anything like this - back up your data first. If in doubt and you're not sure what to do next, DON'T proceed, quit out, go back to windows and ask more questions. 

Installing can be daunting, but once you do it it never seems so bad after that.

Good luck and go at the speed that you are comfortable with.

---

### Post by marlis56 on 2005-12-26
Thanks Exile for the info.
My HD partitions have previously been set up in Windows fat32 and have been in use. I emptied my D:\ partition on the second HD to accept the ubuntu OS.
What I am trying to figure out is how to get Ubuntu to install on my D:\ partition on the second HD when I put the install disk in my CD drive and boot.
I have been reluctant to proceed through the install disk prompts for fear that it will wipe my C:\ drive clean and I would lose all files on the C:\ drive.
Do l I still have to use the Ubuntu disk partitioner even though I have a partition set up on my second HD?
How would I proceed? I sound like a real novice, but I think I'm fairly knowledgable about this stuff. 
Hope you are enjoying the start of summer down under.

---

### Post by stoneguy on 2005-12-26
There's something you need to know before you do this!

Since D is the 1st partition on your 2nd drive, it's going to lose that letter when you install Ubuntu because Win doesn't see Linux partitions. So E will turn into D, which will hose any paths and path-containing registry entries that used to point to E. (Partition Magic can deal with this, but that's pay software.)

If D and E were both data drives, you're in better shape. And if D had programs on it, copying the directory structure to what's now E will let them be accessed when the drive letters change.

And no, you can't leave the first partition on the second drive FAT32. You can't install linux onto a Windows partition type.

I think you'll also have to install GRUB on the MBR. And you'll need to set up a swap partition as well. you'll have to take down your old D partition completely to split it up (unless you have unallocaed space on either one of the drives).

---

### Post by marlis56 on 2005-12-27
Thanks to the info from Exile and a web site posted by Herman that has very detailed info on dual installations, I have successfully installed ubuntu on my D:\ drive. It is going to be a great initiation to linux.
The info that you, Stoneguy, provided is correct and I learned it during the reading and installation. I had previously done as you advised and had transferred my D:\ fat32 files to my E:\ partition. Then made a clean install of ubuntu onto what was my now empty D:\ drive, which is now \dev\hdb1. All is well. Windows is still recognizing my E:\ drive.
Thanks to all of you forumites for your willingness to be so helpfull.

---

### Post by marlis56 on 2005-12-27
More info to anyone reading this far. Windows still is recognizing a D:\ drive but shows it in explorer as empty.
GRUB was installed automatically and allows me to dual boot.
My 2 linux whiz grandsons visiting for the holidays edited GRUB which now boots to Windows by default as before (for my wife) and if I want linux I can boot to it.
They also edited to eliminate the need for me to enter a user name and password every time. It saved me having to learn how to do it myself, which I will review when I have time.
Pays to have grandsons!

---

