---
title: "Thinkpad will not boot"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by steadirob on 2007-05-01
Hi, mu first post here. I have been reading many websites and pages to find an answer but am still left in the dark.

I have a Thinkpad P4 (G40) that i wanted to make dual boot as I read interesting and promising reviews about Ubuntu.
So i downloaded the ISO, burned with infra recorder, checked the file with the winMD5sum and all was well.
I also read many install procedures and saw video's of it and it all seemed like a piece of cake.

Booting up from the cd went well, so I started to install. 
I wanted to leave my original harddisk intact (with XP-prof) and install on a specially prepared USB disk with 8Gb for Linux, 2 Gb for the swap file and another 30 Gb partition for data.
This was all carefully selected in the manual setup and partitioner.

after the install, i wanted it to reboot, removed the cd that popped out and started again.
From that moment on I am stuck. 
Grub starts, then error 21, which is as i have read, it can not find the path/disc

I can get into bios screen at start up. the boot option for USB disc(ettes) is enabled.
I can choose the USB, the HDD, the CD or a Lan card, but all that is returned is the same error 21, after which the machine is completely inaccessable.(except for the on-off switch)
I can also get the boot list by pressing F12 at start up, giving me the options i mentioned. the only option that gives any different result is the CD, when I put in the LiveCD (ISO) in it, but it returns: "no operation system found" or something like that.

As this is a fairly old laptop (but in good shape) I have no rescue CD from it.

So at this moment i have a paper-weight blinking error 21 and have no idea how to solve this, after reading all information, mainly because i cannot input any command anymore.

Open to all suggestions...............except totally formatting my HDD with it's - paid- XP!

Rob

---

### Post by amohanty on 2007-05-01
First - to recover XP, use the install CD, or if it only came with a repair CD, goto bootdisk.de and get a winxp boot CD image and burn it. Then boot with it and at the command prompt use:

fixmbr

to reinstall ntloader to your boot location.

Now as to ubuntu, the reason grub gives an error 21 [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)
is that it cannot find the disk. Its a USB drive so by default is a hotplug device, as a result of which GRUB may barf. Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

and see if it helps. its old but much of it should work.

HTH
AM

---

### Post by steadirob on 2007-05-17
Well, I managed to get my Laptop back  in it's original state, but it was not easy!

After i found a way to get a floppy running on it with I could boot from that to XP again, then MBRFIX could restore the master boot record.
It took some weeks to find all the needed info and steps to make.......

Makes me hesitant to try Ubuntu again, though I see that now a nice video editing program for it has been released that i would like to try.
But i don't want to ruin my original disk again! :(

Thanks for the information that got me started to restore the laptop!

So what is the save way to install/try Ubuntu without having the Grub loader ruin everything?

Rob

---

