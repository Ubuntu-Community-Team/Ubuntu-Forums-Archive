---
title: "Administrator Settings..."
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by Clayton South on 2008-02-18
Hi everyone...

here's my question: I want to let non-administrator users be able to change the monitor settings in Screens and Graphics. Is there a way to somehow move these functions over to allow regular users to affect changes without me logging in?  I tried moving the menu items over, but it still asked me for admin password.

Is there a way to re-assign the security or priviledges for these functions?

Thanks!

-Clayton South

---

### Post by aysiu on 2008-02-18
If you have the proper available resolutions set up in /etc/X11/xorg.conf, any user should be able to select the preferred resolution in System > Preferences > Screen Resolution without having to enter a password.

---

### Post by Clayton South on 2008-02-18
Ok, thanks for this!

I'm using a laptop, with an analog cable that gets sent to my flatscreen monitor. Sometimes the desktop shows up on the monitor and other times not. Unlike windows, which i no longer use (I am all Ubuntu), I can not just hit function-f4 to send the desktop to the monitor. Is there a util to allow for this? My wife says that the double screens drive her crazy.

Thanks!

-Clayton South

---

### Post by aysiu on 2008-02-18
Try editing the /etc/sudoers file with the command ```
sudo visudo
``` and then adding this line: ```
*username* ALL = NOPASSWD: /usr/bin/displayconfig-gtk
``` where *username* is your wife's username. That might work. You'll have to create a launcher in her account for the command ```
gksudo displayconfig-gtk
``` though.

---

