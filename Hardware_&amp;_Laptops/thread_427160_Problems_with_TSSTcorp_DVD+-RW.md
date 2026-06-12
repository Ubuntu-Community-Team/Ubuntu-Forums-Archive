---
title: "Problems with TSSTcorp DVD+/-RW"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by wykthorr on 2007-04-29
Hy,
I've got a TSSTcorp DVD+/-RW drive installed on a NEC Versa P440 notebook and I have had a whole lot of problems with it.

1. If I insert a CD/DVD in the empty drive let's say 30-40 minutes after bootup the media will not be automatically mounted and the mount process will hang if I try to mount it manually. On the other hand if I put the disc in while the computer boots or soon after I enter the GUI it works fine.

2. If I leave a disk in the drive the media will be automatically ejected with no interaction on my side.

3. The latest:  After upgrading to version 7.04 of Ubuntu the system sometimes starts responding really really slow to any commands. Basicly it becomes unusable. When I managed to switch to a tty the message "hdc: drive not ready for command" kept on being displayed. An immediate solution to the problem seems to be taking the drive out of the bay and inserting it back (it's hotplugable). After I do so the computer starts responding to commands again.

Please help it's getting really annoying.

---

### Post by mortram on 2008-02-07
I've searched exhaustively to try to fix this problem but it persists on my HP dv6000 with 7.10.  Everything else on the laptop works just fine.  

you can try following these links, it sounds like a few people have resolved the issue but many have not.

ubuntuforums.org/archive/*index.php/t-446140.html
ubuntuforums.org/*showthread.php?p=942785
bugs.launchpad.net/.../*+bug/107952/comments/4	 

On my system it freezes so badly that I can only *sometimes* get to a terminal, only to see the error "hda: drive not ready for command" printed over and over again.  I can do nothing but power off the machine.

There are a couple of peculiarities:

1) On several attempted installs, this issue only occurs *after *allowing Ubuntu to run software updates.  Someone in one of the above links mentions the updates reconfiguring either HAL or hdparm.conf, however I have not been able to determine what changes those might be, even backing up my hdparm.conf prior to updates and restoring it.

2) The issue does not occur with Fedora 8.

I'd love to resolve this issue given that the problem seems to be with an update reconfiguring something, but so far it seems nobody has found a solution.

---

