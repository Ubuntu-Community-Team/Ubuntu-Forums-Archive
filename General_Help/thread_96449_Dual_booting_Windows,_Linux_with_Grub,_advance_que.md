---
title: "Dual booting Windows, Linux with Grub, advance question"
date: 2005-11-28
forum: General Help
---

### Post by phoenixy on 2005-11-28
Hi guys,

First of all, I just want to say that I had dealt with Grub before. Setting it up to multiboot Ubuntu, gentoo, windows, and qnx is quite straight forward. The catch is that I installed windows first, thus it wrote its boot loader into the partition it belongs to.

Now, what if I want to install Windows after Linux? One legit need for this procedure would be reinstalling a screwed-up windows. I did a quick google search and all HOWTO mentions usage of floppy disk. It makes sense, but the laptop that will be housing Windows and ubuntu have no floppy.

So, I was thinking along the line of setting up grub to start up first, then it makes the windows partition active(windows not yet installed), then launch the boot CD and let go from there. Basically, skip the CD boot process in BIOS, and do it from GRUB, so that I can make use of its partition hiding feature.

So, does this sound reasonable? Does anyone know good webpage dealing with this type of setup? Thanks in advance! :D

---

### Post by Kevinator on 2005-11-28
I recently installed Windows on the first partition of a disk that had Ubuntu on the second partition (where the third partition was an extended partition with one logical drive for swap -- Ubuntu's normal setup, I think). Of course grub was wiped out in the process, but all I had to do to restore it was boot from the Ubuntu installation CD, go through the steps up to the partitioning phase, set the partitions the way they were originally while marking them to NOT BE FORMATTED, then continue. I immediately got an error because there was no place to install the system. This took me back to the main installation menu where I could simply select the Install GRUB option.

I admit this wasn't the cleanest way of doing it (maybe you can just shell out of the installer and run grub's installer), but it worked fine. I wouldn't have done it if I valued the data on the disk though, since I wasn't sure what the installer would do. I just wanted to see if it would work, and I was already planning to reinstall Ubuntu anyway (went from the 64 bit version to the 32 bit version).

---

### Post by phoenixy on 2005-11-28
Hey, that's good to know. I was thinking about just install GRUB off the installation CD without doing anything else. What you said made sense. 

So, I need to get 2 windows and 1 linux onto the hardrive how abou this setup?

part1(active) = Windows
part2(active) = /boot
part3(active) = Windows
part4(extend) = everything else

By the way, my hardrive is clean and I have free reign over it. I won't mind doing a little experiment with it.

Also, a quick question: Windows will always write to the MBR on partition1, right? So does that implies other than the first windows, other windows can be installed in logical partitions?

---

### Post by akiro.yamamoto on 2005-11-29
[QUOTE=phoenixy]Hey, that's good to know. I was thinking about just install GRUB off the installation CD without doing anything else. What you said made sense. 

So, I need to get 2 windows and 1 linux onto the hardrive how abou this setup?

part1(active) = Windows
part2(active) = /boot
part3(active) = Windows
part4(extend) = everything else

By the way, my hardrive is clean and I have free reign over it. I won't mind doing a little experiment with it.

Also, a quick question: Windows will always write to the MBR on partition1, right? So does that implies other than the first windows, other windows can be installed in logical partitions?[/QUOTE]


Yes they can and not only that if you install them one right after the other
the M$ boot loader will give you the option of choosing which version
of windows to boot.
Then if you install / re-install GRUB it will give you the option to boot either one as well.
Regards

---

