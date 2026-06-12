---
title: "new motherboard, can't boot.."
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by nobody008 on 2008-12-19
Hello,

I was using ubuntu kernel 2.6.15-52-amd64-server on my desktop pc. Recently, my motherboard failed so I replaced it with new motherboard, ASUS P5QL.

All other components are working well so I just replaced the motherboard and plugged all others but I can't boot now.

The following is what I see now:


After Loading Essential Drivers:   [OK]
Mounting Root File System :        blank
Waiting for root filesystem :      blank

It sits there for about 2-3 minutes until eventually it shows black screen and a terminal shell with a message along the lines of 


Begin: Waiting for root file system... ...
Cannot find /dev/hda1
ALERT : dev/hda1 does not exist

BusyBox Built In Shell
#_



I found a thread about this problem [http://ubuntuforums.org/showthread.php?t=197956](http://ubuntuforums.org/showthread.php?t=197956)

However, I'm not sure how to fix it even if I read it couple of times. 


I have only one SATA HDD and one cd-rom drive. There is no Windows installed in this computer.

I will really appreciate if somebody can tell me how to fix it step-by-step procedure....

Thanks in advance.

---

### Post by Mark Phelps on 2008-12-19
Run "sudo fdisk -lu" (that's a lower-case ell, not a one) from a terminal and look at the results.  On my system, SATA drives are "SDx" not "HDx", so it may be reporting your drive as SDa not HDa.  If that's true, go into /boot/grub/menu.lst and, if the entries indicate hda, change them to sda.

---

### Post by markbuntu on 2008-12-19
No no no. grub ALWAYS uses hd(x) in the menu list. you need to map sd drives in /boot/grub/device.map like this

(hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by jimbean on 2008-12-23
i switched mobo and now am having prob`s with acpi {need to disable in bios} also cant shut down

so i yahoo`ed answer here

[https://answers.launchpad.net/ubuntu/+question/16914](https://answers.launchpad.net/ubuntu/+question/16914)

dont know if its help or not but i was looking for a solution to my broblem

sorry for barging in

---

