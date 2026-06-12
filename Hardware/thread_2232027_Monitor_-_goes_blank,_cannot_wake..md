---
title: "Monitor - goes blank, cannot wake."
date: 2014-06-29
forum: Hardware
---

### Post by bmhm on 2014-06-29
Hello everyone.

last week I upgraded my kubuntu installation to Kubuntu 14.04, using ```
do-release-upgrade
```. As far as I can tell, the system runs just fine.

After a few minutes of idling, my monitor goes blank, despite I disabled the setting in kde's energy options. The PC itself is running (no S3, etc.), I can even login via ssh. But the monitor won't react to mouse movement or keyboard input. It just stays blank. Switching to TTY1-8 won't help either.

My lucky guess: My LG-Monitor isn't being recognized correctly. EDID-Output: [http://paste.ubuntuusers.de/419217/](http://paste.ubuntuusers.de/419217/) - the interesting thing: KDE things, I'm using a monitor made by Goldstar Company Ltd. Xorg does not: xorg.0.log-grep: [http://paste.ubuntuusers.de/419222/](http://paste.ubuntuusers.de/419222/)

Graphics card:
```
 $ lspci -v | grep -iA1 vga
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Barts XT [Radeon HD 6870] (prog-if 00 [VGA controller])
        Subsystem: XFX Pine Group Inc. Radeon HD 8670
```

There are no Errors [(EE)] in that file. Also, switching to fglrx driver didn't help.

Any help or guess is appreciated.

---

### Post by sp40140 on 2014-06-30
I have Ubuntu 14.04 64bit running on i7 EliteBook laptop. If my screen is locked or screen saver is on... I have to close the lid (so either hibernate or suspend.. not sure which one) and then press the power option again to bring it back to life.
This wasn't an issue until 12.*. 

Try to disable screen savers, screen locks. and try it.

Cheers,

---

### Post by bmhm on 2014-07-01
> Try to disable screen savers, screen locks. 
I have disabled screen savers from kde settings, and made sure that no other screen saver processes were running.

> on i7 EliteBook laptop.
I'm running on a desktop PC. No chance of having a lid opened or closed.

---

### Post by bmhm on 2014-07-03
Hi,

can someone else please be so kind and have a look into this? Thanks a lot in advance!

---

### Post by bmhm on 2014-07-09
Sorry to bump again, but my bugs or threads never get answered. But this problem is really a show stopper! PLEASE be so kind to respond.

---

