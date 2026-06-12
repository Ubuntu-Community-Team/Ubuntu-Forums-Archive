---
title: "Ubuntu won´t start, i just keep getting error."
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by martuschka on 2009-11-03
Hi all, please help me if u can, i did an upgrade and now my ubuntu wont load it just says this on a black screen:

Starting up..
Loading, please wait..
19+0 records in
19+0 records out
Kinit: name_to_dev_t(/dev/disk/by-uuid/8715ff09-2fc5-4542-8d8e-388088ec0eac)= dev (8,3)
Kinit: trying to resume from /dev/disk/by-uuid-2fc5-4542-8d8e-388088ec0eac
Kinit: No resume image, doing normal boot…
Mount: mounting /dev/disk/by-uuid/b8c675c4-3b4f-42b4-9c24-75015d2d5420 on /root
Failed: Invalid argument
Mount: mounting /dev on /root/dev failed: No such file or directory
Mount: mounting /sys on /root/sys failed: No such file or directory
Mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn’t have /sbin/init.
No init found. Try passing init= bootarg.

Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) Built-in shell (ash)
Enter ”help” for a list of built-in commands

---

### Post by mikewhatever on 2009-11-03
Have you upgraded from Hardy Heron? To which release? Or perhaps it was an update?

---

### Post by martuschka on 2009-11-03
i had 8.10 and i just did the upgrade in the manager.

---

### Post by mikewhatever on 2009-11-03
Sorry I don't have the answer for you. I've googled, and the errors turned out to be quite common. One solution is described [-->here<--]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/244421/comments/3"). 
Could you boot from a live cd and check if you can access your Ubuntu partition. If you can, that means the filesystem is ok, which is good. Then let's check your UUIDs. If you can access the Ubuntu partition, navigate to /etc/fstab and post the contents of that file, also post the output of **sudo blkid** from a terminal.

---

