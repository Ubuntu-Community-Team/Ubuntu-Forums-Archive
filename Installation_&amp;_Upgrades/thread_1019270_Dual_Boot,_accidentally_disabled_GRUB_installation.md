---
title: "Dual Boot, accidentally disabled GRUB installation"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by abcminiuser on 2008-12-23
Hi all,

I've just tried to turn my Vista machine into a dual boot Ubuntu (7.10) machine, and have failed miserably - I now have an unbootable machine.

During the installation I turned off the option to install GRUB automatically, hoping to use the Vista bootloader instead. That didn't work, as apparently the installation messed with the Windows bootloader anyway, and I now get a "No Operating System Found" message. I made sure my files are still intact by mouting the Vista partition from my live CD, but can't seem to get grub to install, as I have no boot parition (apparently).

What is the simplest way to get grub up and running, so I can boot into either OS?

Thanks
- Dean

---

### Post by abcminiuser on 2008-12-23
Woohoo! Fixed my own problem. The installation killed the boot flag on my Vista partition. Fix was easy, for posterity:

> Run Terminal
> Type sudo gparted
> Click on Vista partition
> Click Partition->Manage Flags
> Turn on the boot flag
> Restart

Now I need to figure out how to boot to Ubuntu from the Vista bootloader...

- Dean

---

