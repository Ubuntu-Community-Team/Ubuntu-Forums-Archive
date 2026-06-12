---
title: "Booting Issue UDEVADM Trigger"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by billyhig on 2009-09-07
Hey all,

I just installed Ubuntu 9.04 and I'm having a little trouble.  After the intial install the OS opened with no issues.  The first thing I did was attempted to run the updates.  It downloaded all the updates but then halfway through installing them my crappy battery crapped out.  Now whenever I try to power on the laptop It goes to the Ubuntu loading screen with the status bar but then changes to this following error. 

Starting up...
Loading, please wait...
udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device.  Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay = (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4419a64a-2249-4e53-8ce3-9bad945e3c7a does not exist.  Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)


I'm a newb to Ubuntu, so please excuse my ignorance if I'm overlooking something obvious.  I first attempted to reinstall the OS from disc again, but for some reason I can't get the machine to boot to disc.  

Anyone have any ideas?

---

### Post by billyhig on 2009-09-09
Hey all,

Just following up on this problem I had.  I believe when my laptop powered down something got corrupted.  After about 100 times booting my laptop I was finally able to get it to boot from the disc again.  I reinstalled Ubuntu and ran the updates.  No problems to report of yet, but thanks anyways!

.Billy

---

