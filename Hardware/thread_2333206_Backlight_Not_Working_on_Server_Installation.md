---
title: "Backlight Not Working on Server Installation"
date: 2016-08-08
forum: Hardware
---

### Post by Voc on 2016-08-08
Hey everyone,

I'll start by saying I used the Ubuntu Server installation and I think that might be the reason I've been having trouble.  I've been having a difficult time getting the backlight keys to work like they should.  At first I thought it was just an issue with the keybindings not working, so I used chown and chmod on /sys/class/backlight/radeon_bl0/brightness then implemented a bash script triggered by a key binding to change the brightness.  However, every time I reboot, /sys/class/backlight/radeon_bl0/brightness becomes re-owned by root and doesn't allow write abilities without sudo (and resets the brightness to maximum).  If I use ```
sudo tee /sys/class/backlight/radeon_bl0/brightness <<< X
``` on terminal to change the brightness, then that value X "sticks" even after reboot.  Because I got the backlight keys working on a desktop installation using xfce4-power-manager, I decided to see if it would work on this installation, which it did not.  Therefore, I'm thinking that /sys/class/backlight/radeon_bl0/brightness and related files and programs were somehow given different permissions and ownership than they do with the desktop version.

So I guess my questions are:  1) Does this sound like it could be the problem, and 2) Is there a way to fix it without having to reinstall Ubuntu using the desktop disk?

Thanks for any help guys!
Luke

---

