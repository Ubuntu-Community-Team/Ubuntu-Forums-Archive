---
title: "No kernels listed in grub bootloader!!!?!?!"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by chinbo99 on 2009-05-21
Hi all,
 
Not sure if anyone can help me with this as it quite complicated.
 
Basically this is what happened. I have Ubuntu 8.10 Server installed on an old IBM Pentium 4 system and it has been working fine for some time. I earlier shutdown the server (the proper way using the shutdown command and no errors were reported) and installed a second hard drive to just use as more storage alongside the server system on the primary drive. I checked the jumper settings to set a master and slave drive, and the bios picked the primary and new drive up correctly. On reboot, I received a large list of faults, but the main worry was many "segmentation faults". The boot sequence then just stopped at "Starting kernel log daemon".
 
So I had to reboot again and tried the recovery mode from the GRUB bootloader. I wasn't able to get a command prompt, as for some reason Ubuntu has forgotten the root password I set up??!?! So I tried the "dpkg - repair broken packages option". It searched around for a bit and came back with some available kernel updates and restricted modules packages, and some other packages to fix the broken packages problem. I let it download these and try to install them, but once again I got dpkg errors for these packages and they weren't installed properly. When I then rebooted again, the GRUB bootloader had lost all kernel options from its menu, leaving the only option as a memtest!!
 
I tried the repair broken system option on the original CD, and have looked at the disk with the shell option, and it appears the kernel files are still all there. I then tried to re-install the GRUB, and it failed, which the caused problems with the shell option!! So I am now unable to get a shell command prompt from the CD, and I have no kernels listed in the bootloader so I think I'm pretty stuffed.
 
Can anyone give me any advice as to where I can go from here. Stupidly, being relatively new to linux, I don't have any backups of anything. I have quite a lot of stuff running on the machine that has taken me some time to setup, and I could really do with not having to give up and start again. Is there any way I can get a working kernel re-installed, or if nothing else, get access to the disk to get all my config files off of it, so at least I won't have to start completely from scratch if I'm forced to start again?
 
I know that description is pretty washy, but without having access to any logs, I can't really be any more specific as I can't remember the exact fault descriptions, codes etc.
 
Any help would be much appreciated!
 
Chinbo99

---

