---
title: "error 22"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Dangrab34 on 2009-10-22
My system is a 1T drive with C: Vista, D: XP, and D:, E:, F: G: and H: all data drives.  I first tried to install Ubuntu 9.04 on half fo H: that I unallocated.  I was unable to set up a /, home and swap ( because it was at the end of a 1T drive?? ).  I then installed an old PATA 20G drive that I partitioned as 9.5G home, 9G / and 2G swap and installed Ubuntu.  The installation seemed to go great, but when I rebooted at the end after the post it tried to load grub and stopped with grub error 22.  Since I was unable to open the cd drive due to the stop I powered down and manually opened it to put the live installation disk back. 

When I run grub> find /boot/grub/stage1 it returns (hd1,5).  I think the original boot sector was on (hd0,0), the original 1T drive, but I am not sure.

Can someone tell me how to get my triple boot of vista, xp and ubuntu working?

Thanks,

Dan

---

### Post by dstew on 2009-10-22
When you get the grub error 22, does it also give a text explanation like "No such partition" or does it just print the number and stop? I am guessing that it just prints the number. That means you have a grub stage 1.5 error. The disk booted, grub started, but could not find its stage2 file.

The reason this happens is that the BIOS and the Linux OS under which grub was installed count the disks differently. It is interesting that your Live CD system (which is running the grub *shell*, not the grub boot loader) sees a grub stage1 file on (hd1,5). Does your PATA disk really have 6 partitions? I suspect not. That means you probably have an Ubuntu installation on partition 6 of your 1T drive. This is strange, because your message does not sound like this could have happened.

Anyway, things are bolloxed up. Grub will probably have to be re-installed. You can go ahead and try the [usual method]("http://ubuntuforums.org/showthread.php?t=224351"), but that method may fail if your BIOS and Linux are counting disks differently.

I would recommend running the [Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/") to automatically analyse your setup. This script was written by forum contributor mieirfra, and is very useful for complex boot debugging.

---

### Post by Dangrab34 on 2009-10-22
Now that you mention it i see that right before the error message it says "grub loading stage 1.5  

You are correct that the 20G PATA has only 3 partitions, swap, /, and home

the problem is that I can't boot anything.  I am considering running vista repair and try to start all over.  

I will look at the boot information script  before I try to repair vista





> **dstew said:**
> When you get the grub error 22, does it also give a text explanation like "No such partition" or does it just print the number and stop? I am guessing that it just prints the number. That means you have a grub stage 1.5 error. The disk booted, grub started, but could not find its stage2 file.

The reason this happens is that the BIOS and the Linux OS under which grub was installed count the disks differently. It is interesting that your Live CD system (which is running the grub *shell*, not the grub boot loader) sees a grub stage1 file on (hd1,5). Does your PATA disk really have 6 partitions? I suspect not. That means you probably have an Ubuntu installation on partition 6 of your 1T drive. This is strange, because your message does not sound like this could have happened.

Anyway, things are bolloxed up. Grub will probably have to be re-installed. You can go ahead and try the [usual method]("http://ubuntuforums.org/showthread.php?t=224351"), but that method may fail if your BIOS and Linux are counting disks differently.

I would recommend running the [Boot Information Script]("http://sourceforge.net/projects/bootinfoscript/") to automatically analyse your setup. This script was written by forum contributor mieirfra, and is very useful for complex boot debugging.

---

