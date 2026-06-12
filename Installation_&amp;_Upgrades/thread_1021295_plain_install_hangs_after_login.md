---
title: "plain install hangs after login"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by cid0680 on 2008-12-25
Hello all,

I'm trying to install 8.10 on my sister's desktop (a dell dimension 2400). The install CD was great, no hitches; I let it keep XP and partitioned off another half of the disk for U, but otherwise didn't do anything custom. It boots up fine, and gives the nice graphical login screen. However, after you type the username/password, it changes to a plain orange background, nothing else...there's a few seconds of disk activity...then it hangs.

I've used linux quite a bit but I'm not very good at diagnosing this kind of stuff. I booted the recovery mode and dropped to the root shell, and tried to look around the logs, but I'm not sure where to look. In /var/log/gdm, there's logfiles named ":0.log", which appear to be X server log files...the meat of them contains 3 lines saying

AUDIT: Tue Dec 23 12:00:46 2008: 4798 X: client 4 rejected from local host (uid=0 gid=0 pid=4972)
AUDIT: Tue Dec 23 12:00:46 2008: 4798 X: client 4 rejected from local host (uid=1000 gid=0 pid=5040)
AUDIT: Tue Dec 23 12:00:46 2008: 4798 X: client 4 rejected from local host (uid=1000 gid=1000 pid=5041)

Under /var/log, the Xorg.0.log file doesn't have any Errors (EE), but does have the following warnings:

The directory "/usr/share/fonts/X11/cyrillic" does not exist.

intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80000203 to 0x00000000
intel(0): PIPEASTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
intel(0): PIPEASTAT after: status:

intel(0): Failed to allocate texture space.

Other than that, I'm not quite sure where to look...none of the other log files seem to have anything to do with X. There's mention of a bunch of problems in "main.c" for pulseaudio...
In /etc/X11, xorg.conf just has "Configured Video Device", "Configured Monitor", etc under the sections "Device", "Monitor", and "Screen".

XP tells me the system has a Pentium 4 2.5Ghz, 768MB of RAM, an Intel 82845G/GL/GE/PE/GV graphics controller...

Any help greatly appreciated!

---

### Post by cid0680 on 2008-12-25
bump...Boy, it's busy in here on xmas day... :)

---

