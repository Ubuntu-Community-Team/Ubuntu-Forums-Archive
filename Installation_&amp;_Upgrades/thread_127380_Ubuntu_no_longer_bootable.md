---
title: "Ubuntu no longer bootable?"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by UK31337 on 2006-02-08
Hi, I've run into a serious problem on my laptop.

Ubuntu worked fine up until I tried it this evening.  My laptop has a RAID configuration, with Windows installed on sda1, and Ubuntu Breezy on sdb1.

The problem is this:  When I try to start Ubuntu normally, it gets to a couple of steps beyond "Loading modules" then crashes:

> /bin/sh: can't access tty: job control turned off

And I get a useless command prompt, as it won't let me mount anything and tells me all my commands (apart from those viewed by typing help) are wrong.

When I do a hard reboot, and choose Ubuntu recovery from GRUB, I get something along these lines:

> 
Running /scripts/local-premount
swsusp: Suspend partition has wrong signature?

EXT3-fs error (Device sdb1 ***[sdb1 is my Linux drive]***)
ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
EXT3-fs: group descriptors corrupted!

/root/dev: No such file or directory


Somehow it seems the whole drive with Ubuntu on it got corrupted, but how?  I think it maybe because I chose it by accident instead of Windows, and did a hard reboot during Ubuntu's starting up, could that have caused it?  I've done that before but the system's never hit these problems.

Is there any way of recovering this situation, or should I reformat the drive and install Ubuntu again?

Thanks in advance.

---

