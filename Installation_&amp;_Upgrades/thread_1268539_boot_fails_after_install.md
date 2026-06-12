---
title: "boot fails after install"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by cesium62 on 2009-09-17
I'm installing Linux on my 4th computer at home and having problems getting the machine to boot.

The machine is a about a 3-year old e-machines computer.  (Had a seagate 200GB drive in it.)  I can get more details if that's absolutely necessary.

I burned a minimal install CD.  I installed linux from that CD.  Everything was working great. We tossed the 10-year old crt monitor in favor of a new LCD monitor.  We rebooted multiple times while configuring the monitor.  We downloaded firefox and some other apps.

Tonight (We installed linux on Monday, screwed around with the new monitor and downloading additional software on Tuesday, Tonight is Wednesday) when my son booted the computer we got grub stage 1.5 error 18.  After scanning forums and power-cycling a few times while tweaking hard disk settings in the bios (e.g. disable LBA, disable block mode, ...) I decided to play with 'recovery' mode (I think it's called something else, but my mind blocks out the word...) from my minimal install CD.  This spent a couple-few minutes printing out things that looked like disk errors.  Messages to the effect of blocks not getting read.  Blocks 50 to 58 and block 111.  It looked like the recovery mode looped through the problems 5 to 10 times and then decided it was time for a new install.

Because things had been working and then stopped on a reboot; and because the recovery mode seemed to be seeing disk problems, I decided maybe the disk drive was bad.  I removed the 200GB seagate drive and installed a pair of old 40GB drives I happened to have lying around in the garage.

I popped in the minimal install CD and went through a fresh install.  This time I manually partitioned the system.  I created a /boot partition (bootable, ext3, mount on /boot, used the required minimum 3.2 GB), a swap partition (4GB), a / partition (ext3, 16GB), and a /usr/local partition (ext3, 16GB).  I labeled at least the boot partition.  On the second drive, I created a single /home partitition (max, ext3, not bootable).

The install ran to completion.

When rebooting after the install, grub was not accessible.  The BIOS refused to consider the possibility that we might want to boot off the hard disk drives.  I used the minimal install CD in 'recovery' mode and was able to 'od' at least parts of the hard disk drives.  But I don't know enough to figure out what sorts of things I ought to have tried while using the shell in recovery mode.

The fact that I seem to be able to configure ext3 filesystems on partitions and I seem to be able to run 'od' on partitions makes me think my disk drives are basically working.

Did I do something really stupid when manually partitioning the disk drives?  Do BIOSes really like having NTFS file systems lying around in order to figure out how to run grub?

What tool should I use to figure out if there are hardware problems?  What troubleshooting steps am I missing?  What would an expert do at this stage?

thanks, Chuck

---

### Post by cesium62 on 2009-09-17
"rescue" is the word I mean instead of "recovery".

---

