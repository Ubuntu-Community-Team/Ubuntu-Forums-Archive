---
title: "Can't get into Ubuntu!"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by dabear on 2006-01-28
Hi, I've gotten my self into some problems when installing ubuntu breezy to one of my buddies. There were no problems in the installation, but when Ubuntu starts (after grub lets go), it's stalling at «calculating module dependencies». I've tried reinstalling, but this happens every time. When i start in debug mode - after a bunch of text is showing - ubuntu stops at

```

snd-hda-intel:can't be loaded
missing kernel or user mode driver snd-hda-intel
ignoring pci display device 01:00.0 
ignoring pci display device 01:00.1

```

Any ideas?

---

### Post by sjtravers on 2006-01-28
I came across a couple of other posts which might be of use to you if you can boot in recovery mode.

[http://www.ubuntuforums.org/showthread.php?t=87406](http://www.ubuntuforums.org/showthread.php?t=87406)

[http://www.ubuntuforums.org/showthread.php?t=111870&highlight=intel+hda](http://www.ubuntuforums.org/showthread.php?t=111870&highlight=intel+hda)

Cheers,
Stu

---

### Post by dabear on 2006-01-29
Well, i can't boot into recovery mode either (it just stops without the ability to use ctrl + alt + fX). In one of the threads you linked to, it says that this issue is fixed in kernel 2.6.14, does this mean that if I install dapper instead, this will be fixed?

---

### Post by psomas on 2006-01-29
try reinstalling it...if you still have problems maybe the installation cd has a problem...
i wouldn't recommend installing dapper...at least before its official release... 
i don't know if you can change the kernel...
maybe someone more exerienced can answer... :???:

---

### Post by dabear on 2006-01-29
Heheh, I know I can't change the kernel, after all I can't even get into the command line. I've tried reinstalling twice, first with a self-burned cd, then with the official one. I think I'll wait for flight 4 / beta1, and then give it a shot.

---

