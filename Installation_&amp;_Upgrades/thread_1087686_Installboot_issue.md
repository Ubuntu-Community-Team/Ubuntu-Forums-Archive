---
title: "Install/boot issue"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by joeklln on 2009-03-05
I just recently installed ubuntu 8.10 along side windows xp from a cd. The istall appeared to work correctly. After all the install screens completed it rebooted. Then it asked to boot windows or ubuntu. I selected ubuntu and after a few minutes the following came up.

[COLOR="Blue"]gave up waiting for root device. common problems
 -boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0BE9B7459A0A2027 dies not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.[/COLOR]

Any suggestions? I did notice that it installed the ubuntu file on my HD but it does not appear that it is on its own partition. It it necessary that it be on its own partition?

I have an AMD64 processor and am running XP pro with 2G of RAM if that helps. Thanks again for any help anyone can be.

---

### Post by jellybaby on 2009-03-05
Hi,

yes it does need a seperate partition. If you installed from the liveCD then there must be a seperate partition (plus a swap partition).
Somebody with your problem [found a solution here]("http://ubuntuforums.org/showpost.php?p=6581939&postcount=322")

All the best!

---

