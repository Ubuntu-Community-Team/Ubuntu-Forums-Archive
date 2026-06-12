---
title: "Grub Repair on Raid0 Help Please"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Rotstar on 2009-02-21
Hi all,
I'm going to keep this as simple as possible.  I have three operating systems on my computer.  Vista Ultimate 64, Windows 7 32, and Ubuntu 8.10.  They were installed in that order and working fine together.

I have three HD's on my computer.  500g 7200rpm x2 (working in Raid0), and 64g SSD (Solid State Drive).

The solid state was added recently.  I took out Windows 7 and reinstalled it on the SSD.  The grub was affected and nothing would boot up.

Fixed these issues by using the Windows disks and doing boot repair.  All is well with dual booting both the windows.  However not Ubuntu.

I have the super grub disk and have tried several things but I don't know enough about Linux to successfully repair the grub.  Seems the repairs it tries to make may not be considering that I'm in raid0.  NOTE to install Ubuntu in the first place I had to use the Alternate CD which made it possible to install on the Raid0.

Hopefully that all makes sense and one of you guru's out there can walk me through to a solution.  I'm new to linux so if it involves commands please include them in your reply.  Thank you much.  -Bon

---

### Post by dstew on 2009-02-21
In order to install grub onto a RAID0 you need to have an operating system running during the install that can recognize and mount the RAID. I don't think the system on the Supergrub disk has that capability, but I might be wrong. I know the installer on the Ubuntu Live CD cannot. But, as you say, the Alternate Install CD can.

You might consider installing all over again. If you want to try to install grub only, you might try using the Alternate Install CD, and once the kernel loads, drop to a command line. You would have to first see if the RAID has been recognized and mounted. Then, you could try to install grub to the RAID0 from the command line.

From the alternate install CD command line, try```
sudo dmraid -r
```That should list the array if it can see it. If so, see if you can start a grub shell from the command line:```
sudo grub
```If it says the program is not found, you might need to mount the RAID, and try to use it from there (it should be present as part of the Ubuntu installation on the RAID).

---

### Post by Rotstar on 2009-02-21
Well if I go into the live cd and open a terminal it doesn't recognize the command

sudo dmraid -r
says
command not found

and if I boot the Alternate CD my options are limited to some tests and a supposed system rescue that doesn't work.  It fails at mounting.  And new install option.  I'm about to say screw it and just try to install fresh.  I had nothing important in linux but I always try to fix things rather than wipe them just in case I did have something important.

Unfortunately when it comes to linux I have no idea how to run dmraid and do what I have to successfully.

Sucks because I had it all set up just the way I wanted it and it was running sweet. /sigh

---

### Post by dstew on 2009-02-22
You can install the dmraid program onto the Live CD system if you want to try again. You can use the Synaptic package manager in the System --> Administration menu. But, I have not directly done what you are trying to do, so I am just putting out some ideas. The re-install is probably the easiest way to go. Sorry I can't do more for you.

---

