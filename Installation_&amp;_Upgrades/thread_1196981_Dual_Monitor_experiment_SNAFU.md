---
title: "Dual Monitor experiment SNAFU"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by xapemanx on 2009-06-25
Hello Ubuntu community, thanks to those who read my post, and thanks again to those who respond.

as you can see this is my first post and I will try to include as much information as possible about the problem I am encountering.

on my problem rig I am currently running Ubuntu 9.04 Jaunty with a sapphire 4850 and the latest 9.6 catalyst drivers.

I have been running on a single monitor set-up for the past month now, using the proprietary drivers for about the first two weeks then upgraded to ati/amd's new 9.6 drivers.

My problem started last night when I decided to run a dual monitor set-up by adding my old Dell 20" CRT to my current 23" LCD acer with the 9.6 Catalyst drivers.
I had both monitors running well mirrored. I then removed the mirror and extended the desktop but couldn't get my LCD to be the #1 monitor with my CRT as #2 to the right. so I started switching settings but to no avail the LCD would not go #1. I then set catalyst to run each monitor independently but did not suit my taste. I also noticed now that I could enable the ATI Xinerama (this was greyed out before) so I flicked it on and rebooted.

And now the problem itself.
During post all goes well both monitors mirror untill after the splash screen. The screen simply projects a black image. I have since removed the CRT monitor and went back to my single monitor setup with my acer LCD and the problem still persists. I have since booted from the CD and have tired the code for removal
```
cd /media/disk/usr/share/ati
sudo sh ./fglrx-uninstall.sh
```then I get this error 
```
[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run ./fglrx-uninstall.sh (this is not recommended).

```I suspect I get this error because I'm booting from CD. I am curious of how to use the FORCE_ATI_UNINSTALL command.

I'm suspecting that I've broken the catalyst driver and am now looking for a way to remove the driver using the live session user, then fall back on the proprietary driver. I seemingly run into restriction problems using the live session user. 

I've tried loging out then login in with my username/password but it wouldn't accept.

If someone could point me in the right direction you would have my eternal gratitude

---

