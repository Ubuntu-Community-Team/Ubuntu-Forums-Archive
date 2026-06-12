---
title: "Bootup with new drive issues"
date: 2011-02-19
forum: Hardware
---

### Post by Dragonbite on 2011-02-19
My computer set up is this; Pentium 4 Dell Dimension desktop with 2 hard drives.  /hda = Linux and /hdb = Windows 7.  It is set up to boot to /hda (master) and the Grub menu selection includes an entry to boot /hdb (slave) (Windows).  Both disks are ATA.

I just bought a 250 GB SATA drive and I cloned my Linux partitions onto this new disk.  So far, it seems to be working and all my files are here (after a slight issue with the /home being encrypted..).

The first problem is when I boot up I get a "Primary disk not found" message and the option to hit F1 to continue or F2 to go to setup.  I hit F1 and it continues booting up without any further issues.

The bigger problem is when I re-attach the Windows ATA drive;  Depending on whether it is Master or not I run into one of two situations
[LIST=1]
[*](when Master)The machine takes a loooooooong time to boot up, still comes to where I have to hit F1, yet I can boot into Windows or Linux.
[*](when not Master)It comes up fairly quickly, I hit F1 but Windows cannot be found.
[/LIST]

When Windows doesn't work and I still boot up, I can't find the other hard drive anywhere. ***#sudo fdisk -l*** only comes up with the SATA drive, not the Windows one.

So there are 3 things I want that I am not sure how to get;
[LIST=1]
[*]Automatically boot to Grub without having to hit F1
[*]Faster bootup through the bios
[*]Being able to boot  to Windows or Linux without any problems.
[/LIST]

Am I missing something? Is this because of a mixed ATA and SATA? Is there something I need to fix in the BIOS?  I'm not sure where to look!

---

