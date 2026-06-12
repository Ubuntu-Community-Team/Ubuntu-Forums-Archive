---
title: "Changing from winxp to ubuntu -- help me."
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by xander on 2005-01-25
Hi,

I`ve instaled UBUNTU as a second system on my PC, but I`ve fallen in love with UBUNTU and now I want to erase XP from my hardisk without loosin data from UBUNTU.

I got 80GB disk with 4 windows partitions and linux swap part + ext3 partition with / mount point.
Is any possibility to change this configuration to only linux PC by erasing windows without loosing any data from linux and win partitions? I wanna have a few mount points like /boot, /home/ for better security of data.

Can U help me? ](*,) 

----
Xander

Sorry for my english :-)

---

### Post by machiner on 2005-01-25
Sure...back up your stuff, nuke your partitions and take it from there.

When you're finished, low-level-format the disk. You may have a floppy with this utility, esp if you bought a maxtor or WD hard drive. If not, you can download one.

If you don't LLF your drive you can always restore your partitions if you find that you neglected to back up something importand...but be diligent and LLF the drive. It's a good practice. It will take HOURS on an 80 GB drive.

Pop in Dr. Strangelove and witness the genius.

After this is finished (easy) boot to your Ubuntu disk and set up your partitions with the installer - easy.

If you don't want to set up your partitions with the installer - download SystemRescue Disc 2.x (a gentoo live distro) . Type menu at the first prompt, then arrow to boot into System Rescue.

When you're at the prompt type...run_qtparted

IN Qtparted you can create your partitions and inititlize your partition.

This is extremely simplified, I know - but it's an easy task and I am sure if you do a search you will find more precise instructions...on google and here.

rock on -- welcome to the wonderful world of Ubuntu. You won't regret the choice.

---

### Post by ctt1wbw on 2005-01-25
I'm probably right behind this guy.  In a few months maybe.

---

