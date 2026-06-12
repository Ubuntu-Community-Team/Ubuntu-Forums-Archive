---
title: "system won't boot after system update"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by karn105 on 2009-08-25
I recently ran system update on my ubuntu 8.10 installation.  After restarting so that the updates would take effect, my system can't boot and I get dropped the following screen

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/b65ea726-9280-4a2d-82ad-a9f51fa70116 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
I've searched around the internet and come a across this article 
[http://ubuntuforums.org/showthread.php?t=1137272](http://ubuntuforums.org/showthread.php?t=1137272)

but none of those suggestions seem to work.

The funny thing is, I can still boot the previous version of the kernel without a problem.

Does anyone have any ideas other than re-installing?

---

### Post by karn105 on 2009-08-26
bump

---

