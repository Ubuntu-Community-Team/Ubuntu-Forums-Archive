---
title: "Grub was not installed properly"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by soulsizzle on 2006-01-31
I just recently installed Ubuntu on a tri-boot system.  The first insallation steps went perfectly fine aside from one problem.  Ubuntu wasn't installed properly.  Once i rebooted the system after the initial step, the windows boot program started up as oppossed to Grub.

I've googled and searched through the forums, but I'm not sure what steps I need to take to correct the problem.  Any help would be appreciated.

---

### Post by Adrian on 2006-01-31
[QUOTE=soulsizzle]I just recently installed Ubuntu on a tri-boot system.  The first insallation steps went perfectly fine aside from one problem.  Ubuntu wasn't installed properly.  Once i rebooted the system after the initial step, the windows boot program started up as oppossed to Grub.

I've googled and searched through the forums, but I'm not sure what steps I need to take to correct the problem.  Any help would be appreciated.[/QUOTE]

You'll probably find this HOWTO helpful:
[http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by soulsizzle on 2006-02-01
The problem was that grub, by default, installs itself on hda.   Because all of the hard drives in my system are SATA, there is no hda.  Therefore, I had to specify that grub install on sda instead.  Of course, now, grub hangs when I reboot (just says grub in the upperleft and won't let me do anything).  But, hey, at least I got it to install!! :)  I'm working on getting that solved.

---

