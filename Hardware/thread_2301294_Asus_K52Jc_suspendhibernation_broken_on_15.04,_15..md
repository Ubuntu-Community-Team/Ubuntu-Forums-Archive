---
title: "Asus K52Jc suspend/hibernation broken on 15.04, 15.10 workaround found"
date: 2015-11-01
forum: Hardware
---

### Post by BzukTuk on 2015-11-01
Hello,
I have a problem with my old ASUS K52Jc laptop. On newer linux distributions suspend & hibernation does not work correctly. When I put laptop to sleep everything works as one would expect - but when I woke my computer {hybernation or sleep - does not matter} there is 30-50% chance, that system freeze after showing Login manager (gdm, slim, lightdm...) or terminal login prompt. After spending few evenings investigating (using help provided here [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)) I found that network driver (jme) is the problem. So I put following into /lib/systemd/system-sleep/remove-jme.sh :
#!/bin/bash
[ "$1" = "post" ] && /sbin/modprobe jme
[ "$1" = "pre" ] && /sbin/modprobe -r jme
exit 0

And suspend started working 100% correctly. {I dont use hibernation very often, so I dont know, if thaw from hibernation would work flawlesly}. But this solution does not work very well for KVM Virtual Machines with bridged virtual net interfaces.

After few months I found that when disable WakeOnLan before suspend using command "ethtool -s eth0 wol d" I always can resume without crash/freeze. This network interfaces WoL is set on g (magic packet) by default after startup (maybee even from POST).

Hibernation is another story - when system boots up, I dont have option to run "ethtool -s eth0 wol d" before system is loaded to RAM from swap, so it freeze on some occasions. But this does not concern me very much - suspend to ram works at least.

I would like to ask, where can I report this bug and hopefully get it fixed :) On Debian 7 wheezy, ubuntu 14.04, antix and other distributions without systemd,  sleep and hibernation usually works, but on newer distros with systemd like ubuntu 15.04, 15.10, Debian 8 jessie, fedora 22, manjaro (archlinux) suspending requieres this "ethtools -s eth0 wol d" workaround, so I thing systemd makes something very differently from other init approaches.

Thank you for your help and sorry for my bad English

---

### Post by diegoviola on 2016-02-25
The fix for this is here:

[https://bugzilla.kernel.org/show_bug.cgi?id=112351](https://bugzilla.kernel.org/show_bug.cgi?id=112351)

And the patch was queued for inclusion in the Linux 4.6 kernel.

---

