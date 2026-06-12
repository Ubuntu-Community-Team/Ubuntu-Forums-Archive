---
title: "ubuntu install won't detect hard drive"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by synthemesco on 2009-10-20
first post on the forums! hi to all :P

I'm posting from a Hardy Live CD - while playing around with wine on my Jaunty install, the system crashed and I had to reboot the pc manually, to find a system boot failure (INSERT SYSTEM DISK AND PRESS ENTER). Upon booting from this 8.10 cd to try to perform a grub recovery, I've found that all hard drives are gone from my Jaunty /dev folder (on sda2), and only sdb (which I use for media storage - that is, porn) shows up on fdisk when I try to re-install. However, system monitor does show sda and all of its partitions, and I can access them from this cd. Could anyone help me try to recover my Jaunty installation? 

Thanks in advance :)

---

### Post by dabl on 2009-10-20
> **synthemesco said:**
> first post on the forums! hi to all :P



Hi    ):P

> 

 I had to reboot the pc manually



No, you don't EVER (well, HARDLY ever) have to hit the power button, which I assume you did.  That can potentially damage the filesystem and lose data, and is normally unnecessary.  Next time you think it is "hung", press Alt-SysRq and while holding them down, press R-S-E-I-U-B in slow sequence, and it will do a graceful shutdown and then reboot itself.


> 

 Upon booting from this 8.10 cd to try to perform a grub recovery, I've found that all hard drives are gone



No, they are not "gone", they are simply not mounted, and therefore don't show up in the unmounted system (Jaunty).   Look in /dev of your running Hardy system and you'll see them all.

Since you nailed the power button, probably the first thing you need to do is run e2fsck on the Jaunty system partition.  

```
man e2fsck
``` or Google will provide examples of how to run it - note that you must leave the Jaunty partition unmounted while you fsck it.

Then, try to boot the computer in "Recovery" mode, and use the "Recovery Console" to "Fix X" or whatever seems to be the problem.

---

### Post by synthemesco on 2009-10-21
Back on Jaunty, hard drive still alive :D

e2fsck made a couples of fixes. then, I didn't really mind the hassle so I just backed up some files and made a fresh install.

thx for the advice, especially for that key combo which I had no clue about - hope I don't need to use it, but it will surely save me lots of trouble :)

---

