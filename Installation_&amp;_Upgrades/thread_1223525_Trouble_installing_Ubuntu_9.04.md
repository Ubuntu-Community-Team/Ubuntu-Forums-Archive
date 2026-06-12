---
title: "Trouble installing Ubuntu 9.04"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by Xanrov on 2009-07-26
1°) From a Mac-Pro (8 CPU, 26 GB Ram) I downloaded and burned on CD, several times from different european sites, because of the problems hereunder exposed, Ubuntu-9.04-desktop-i386.iso. The discs produced checked OK with their imbedded integrity program

2°) then I tried to install this version on a Windows Vista computer, on a 200 GB disk on which I had made a partition of 12GB, close to the begining of the disk, plus a swap partition of 2 GB, located towards the middle of the disk.The first partition was to be formatted ext3 journaled and be on mount point /. The installation started OK but, at the very end, Grub installation failed 9with a message saying "Fatal Error". I repeated the operation several times, with different disks, asking installation either on hd0 (the default) or on the ext3 partition itself, the failure was the same

3°)After that, having VMware 2.0.5 on the Mac, I tried to install Ubuntu 9.0.4 as a virtual Machine. VMware provides an "Easy Linux Install" which doesn't work with Ubuntu versions but there is little difficulty in following the "classical" course of Ubuntu installation. Well, I made several tentatives , with different disks, with the same failure : The install starts pretty normally, but when approximatively 70% have been copied, the CD reading stops, and the Mac is frozen. It has to be restarted by switching it off.

I'm completely puzzled. Of course VMWare could ( and can) be incriminated. But I downloaded and installed without any problem Ubuntu 8.04.2 "TLS" as a virtual machine, on which I'm writing now.

So, what's wrong with version 9.04 ? (a pity , It looks nice).

Thanks for any advice

---

### Post by Sef on 2009-07-26
How did you partition the hard drive?   Did you use Vista's partitioner or not?

---

### Post by Xanrov on 2009-07-26
> **Sef said:**
> How did you partition the hard drive?   Did you use Vista's partitioner or not?

I used Paragon "Partition Manager" since "BootMagic" which ismuch better doesn't work under Vista.

---

### Post by Xanrov on 2009-07-27
After further tests I'm convinced that the current distro of UBUNTU 9.0.4 is buggy. One bug is the fact that, during installation, you can't type more than 5 chars in the Password text entries ( and then get a warning for pass  weakness you must override).Another one is the regular crashing of Grub installation ( on windows machines) A third the freezing of a recent Mac with VmWare during files copy,in the creation of a virtual machine.
On all these points the Ubuntu 8.04.3 "TLS"  dstro behaves without a glitch.

---

