---
title: "Upgraded from 9.04 to 9.10 Now the system doesn't work"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by kadal27 on 2009-11-03
Mine is Pentium(D) Dual Core with Intel Mother Board 1 GB Ram + 15" CRT
It is with Win98, XP and Ubuntu 9.04
Last time I upgraded from 8.04 to 9.04 without any problems.
Now the installation CD of 9.10 did not allow to upgrade.
I tried the update manager and commandline also and those also failed.
Finally I tried for Web Upgrade.
It went on around 7 hrs and after reboot show the following message and fails to boot.
I tried sever attempts and recovery mode. Nothing helped me.

init: sreadahead with process (2053) terminated with status 1
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2054) terminated with status 1
General error mounting filesystems
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@arivukkadal-desktop:~#

Control+D did nothing.
Please help me to recover my system.
(I need my mails from Thunderbird)

---

### Post by witeshark17 on 2009-11-03
Do you have a recent recovery DVD? It's not a good time for this, but before an OS upgrade, a good idea is to use your recovery CD/DVD create utility.

---

### Post by VaiPhile on 2009-11-03
I am having a similar problem.  My system has been able to mount /proc, but everything past that fails. (prim and swap).  I was able to force my primary HD to mount RW by changing it in grub, but I'm also still dropping to the recovery console because it's failing to mount the swap disk.  It just states "waiting on device UUID=HexString".  Confirmed that the UUID's are correct and match /dev/disk/by-UUID/ entries.  Anyone else having these problems?

---

### Post by kadal27 on 2009-11-04
> **witeshark17 said:**
> Do you have a recent recovery DVD? It's not a good time for this, but before an OS upgrade, a good idea is to use your recovery CD/DVD create utility.

I have the installation (live) DVD of 9.04 and CD of 9.10
Any of these help me?

The DVD of Jaunty has recovery option.
When I tried, it reached a # prompt and I don't know how to continue.

---

### Post by treeclimber on 2009-11-04
Mine had the same message.  Any help appreciated.  I have no idea what to do.

---

