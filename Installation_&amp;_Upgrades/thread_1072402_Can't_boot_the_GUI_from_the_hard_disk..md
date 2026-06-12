---
title: "Can't boot the GUI from the hard disk."
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Vic the Trader on 2009-02-17
"Boot from (hd0,0) ext 3 aa45776c-8c3c-4b3a-8815-7c40bc73b9ba

Starting up...

Loading, please wait...

mount:mounting /dev/disk/by-uuid/aa45776c-8c3c-4b3a-8815-7c40bc73b9ba on /root

failed: Invalid argument

mount: mounting /root/dev on/dev/ .static/dev failed: No such file or directory

mount: mounting /sys on/root/sys failed: No such file or directory

mount: mounting /proc on/root/proc failed: No such file or directory

Target file system doesn't have /sbin/init.

No init found. Try passing init= bootarg.

Busytbox v1.10.2(Ubuntu 1:1.102-1ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs)"

This is the black screen-white texted message I get on my monitor after the POST.  I can't work within the OS other than what appears to be one of the built in command lines. Typing help, brings up a list of incomprehensible programming paths to type.

Since I couldn't load the OS from the hard drive, I tried to reformat, but unfortunately I believe the disk is damaged so when I tried to boot from CD I had problems like freezing and inactivity. I am gonna burn a new disk and try to boot from that later.

This all started because I was messing around in Gparted. I think I deleted a partition without making a new one.

---

### Post by Vic the Trader on 2009-02-17
Forget it, it's all good.  I ended up just making another copy elsewhere and I reinstalled it with no problems.

---

