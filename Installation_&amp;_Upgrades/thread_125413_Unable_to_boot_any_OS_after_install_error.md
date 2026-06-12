---
title: "Unable to boot any OS after install error"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by migui_man on 2006-02-03
Hi everybody. 

Firstly, I must say that I was finally able to boot Windows after some fight, and luckily it seems that I didn't cause any harm in my computer, so this is not a cry for help. I'd just like to tell about the problem I had, and read your opinions about it.

I'm trying Ubuntu for the first time. I tried the LiveCD, and it was great: perfect hardware recognition, nice desktop, and that wonderful Debian package management. Then I downloaded the install CD, and I had a problem. When the installer was writing the packages to the disk, an error occurred and the process halted. When I rebooted my computer, it started to reboot automatically at start-up, just when it tried to run GRUB.

What I finally did was to boot with a floppy (a Windows 98 piece of art that has saved me many times), erase the MBR with fdisk /mbr, and install a minimal Fedora system so that it would set-up GRUB again. Well, I guess there must be a an easier way to do this with a rescue CD, so I'd be grateful if someone can tell me what tools can be used in Linux for these things, or where to find a good recovery tutorial.

I think that the cause of the problem was a corrupted install CD. I was lazy enough not to check the checksum of the downloaded image, and then I erased it after burning, so I don't know for sure. But, I don't remember, does the Ubuntu CD check its own integrity before installing? If it doesn't, I think it should, as it prevents this kind of surprises. If it actually does it, then do you think there can be a problem with my hardware?

And then, about the bootloader problem, it seemed quite serious to me. I could only fix it with some luck, and I could potentialy have lost all my Windows system. I don't know exactly what happened. I guess that Ubuntu doesn't install GRUB until it is sure that the rest of the system is written to the disk, because otherwise it'd be quite dangerous. So I maybe the problem was my previous Linux (and GRUB) installation, that crashed because it couldn't find the old kernel, because it couldn't read the new ReiserFS partition, or something like that. Do you think that this could be true? And in that case, do you know how I can set GRUB to a "failsafe" configuration that prevents these problems? And with other bootloaders? Well, if it were possible, I think it'd be nice to have this precaution in the installer. What do you think about it?

Bye-bye,

Miguel

---

