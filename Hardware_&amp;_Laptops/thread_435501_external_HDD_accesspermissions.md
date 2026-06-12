---
title: "external HDD access/permissions"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by se7ensamurai on 2007-05-07
Hey there Ubuntu community. I've scoured the forums for a couple of days now and can't find the answer to my little problem.

Long story short: I was running Edgy with 2 drives, I wanted to do a clean install of Feisty so I put a bunch of files I wanted to save on the secondary drive. When i did the install, I wanted to go back to a dual boot system so removed the second drive, and got an external USB case for it. All the installs went fine (of course) so now I want to recover the data on the USB drive. It seems to mount fine, however when I go to copy a folder over or even try to open a locked folder i get some weird errors (see attached screenshots).
the drive unmounts itsself, and I'm at a total loss. 
The info on the drive isn't vital, but I don't want to just give up and reformat the thing.

drive is in Ext3, and shows up as sda when i run fdisk.
I'm thinking of trying Mondo, any ideas out there?

---

### Post by se7ensamurai on 2007-05-07
NO suggestions eh?
well, I'm currently trying to format the thing, so we'll see what happens. So far I can't even do that. GParted recognizes the drive but dosen't give me any options with it. :( ggggrrrrrrrr.

---

### Post by rcmullins on 2007-05-08
I am currently having a similar problem.   Seems that gparted will really only work on external hard-drive when booting it from a live disk.

I am still researching this problem, as I have an external hard-drive problem.

Threads are here:

[http://ubuntuforums.org/showthread.php?t=419692](http://ubuntuforums.org/showthread.php?t=419692)
[http://ubuntuforums.org/showthread.php?p=2615470#post2615470](http://ubuntuforums.org/showthread.php?p=2615470#post2615470)
[http://ubuntuforums.org/showthread.php?t=428799](http://ubuntuforums.org/showthread.php?t=428799)

I hope these help.  Feel free to jump into the forum.  Seems like information is spread all over the forums with regard to this problem, it would be nice to have a central repository of all the problems and solutions for External Hardrives, etc.

I am currently running Feisty which incidentally does not have the g-ntfs added to it, which may mean it is not stable enough to include in the overall packaging.  Install through the Synaptic Package manager.

good luck!

---

### Post by se7ensamurai on 2007-05-09
well, thanks for the response anyways. There seems to be an issue with permissions and what not, especially in GNOME. I was able to boot to a MEPIS live disk, which allowed me to at least read the drive without errors. However, I could not mount the physical drive as R/W in live mode.

SO i went through 90% of my linux live disc collection, with no luck. Ubuntu 6.06 woulden't boot for some reason. 6.10 booted, and had GParted, but woulden't format any disks (usefull?). 7.04 recognized the disks, let me mount them, woulden't give me write access to the physical disk, and didn't have GParted installed. I resorted to downloading a new version of GParted live and using that to descimate the disk. I reformated to fat32 (just in case i wanted to interact with a winderz partition), and now it works perfectly fine.

My advice is that if you want to back anything up, use a preformated disk, and do not use a physical disk to back stuff up before you turn it into an external drive.

piece. luv. A-Piness.

---

