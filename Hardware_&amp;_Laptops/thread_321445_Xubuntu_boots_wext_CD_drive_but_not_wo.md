---
title: "Xubuntu boots w/ext CD drive but not w/o?"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by SFGary on 2006-12-18
Based on recommendation I installed Xubuntu 6.0.6.1 on an old laptop: Toshiba Portege 3480 P3/600 with 192k and a 12G HD, external CD/DVD drive on a docking connector. 

The installation from the external CD-ROM went fine and Xubuntu works well when it is docked. However when I undock the laptop and boot the PC it freezes at "mounting root file system" and hangs and after a couple of minutes it says: 
[B]
"Booting  'ubuntu kernel 2.6.15-26-386
root (hd0,0)
(etc etc)
Uncompressing Linux...Ok booting the kernel.
ALERT! /dev/hde1 does not exist. Dropping to a shell!

Busybox v1.01 (debian....)
/bin/sh: can't access tty: job control turned off
#"[/B]
--------------

I tried to use a secondary dock w/o the DVD drive and it did not work but when I hook up the dock with DVD/CD drive the boot process works. So I am assuming it has something to do with external drive from where I installed  Xubuntu...

If anybody has any suggestions on how I can get it to work I would greatly appreciate it. Thanks, Gary

---

### Post by SFGary on 2006-12-19
Guys, I looked thru a bunch of posts but am not able to find fix, can anyone help? it looks like Xubuntu is not looking at the right partition? even though there's only one...admit I am a n00b.

---

### Post by joebaker on 2006-12-22
When your system is docked and running publish to this forum the contents of these files:

/boot/grub/menu1st
/boot/device.map
/etc/fstab

The next person to look at this problem will be able to glean more information about the cause of this problem using these results.

device.map might need to look like this:-----
(hd0) /dev/hda

 /boot/grub/menu1st  should probably reference hda  with a number attached to the end instead of hde as your message alluded to.

Good Luck!
xubuntu has lots of promise for usefulness for these older machines!
-Joe Baker
Burlington, Wisconsin

---

