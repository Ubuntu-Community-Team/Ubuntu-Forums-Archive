---
title: "Ubuntu crashed, busybox, was able to run ubuntu from pendrive"
date: 2011-10-07
forum: Hardware
---

### Post by mymistrust on 2011-10-07
So, I switched off normally last night and when I started my netbook (running Ubuntu for netbook, 10.04), it was all normal. When I inserted a pen drive (NTFS) and selected some files from my HD to transfer them to the pen drive, it crashed, and now I can't make it work.

That's what happened when i tried to restart again:
GRUB-EDITENV: ERROR: CANNOT OPEN THE FILE /boot/grub/grubenv

Then I reseted it and when trying to start once again, here's what I got:
mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
 failed: Invalid argument
 mount: mounting /dev on /root/dev failed: No such file or directory
 mount: mounting / sys/ on root/sys failed: No such file or directory
 mount: mounting /proc on /root/proc failed: No such file or dirctory
 Target filesystem doesn't have /sbin/init.
 No init found. Try passing init= boot arg

 BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

So I made a flash pen drive with the same Ubuntu version and plugged to my netbook, and I was able to start it as a test.

The problem is, I can't access my folders because I'm not superuser while using the Ubuntu on the flash pen drive. I want access to my folders in order to make a quick back up before installing once again Ubuntu... But the terminal I open doesn't let me even log in with my username and password.

HELP!

---

