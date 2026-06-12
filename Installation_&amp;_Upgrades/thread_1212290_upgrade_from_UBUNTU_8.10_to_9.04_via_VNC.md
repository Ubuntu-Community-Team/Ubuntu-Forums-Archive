---
title: "upgrade from UBUNTU 8.10 to 9.04 via VNC"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by bl305 on 2009-07-13
Dear Ubuntu Users,

I tried to upgrade my ubuntu 8.10  to 9.04 via VNC. (I use this PC without monitor, only for a server)

The upgrade was seemingly succesfull via VNC but unfortunatelly at the and of the installation I had to restart the PC. After restart I recognised that the VNC has been disabled. I had to connect my PC to a monitor in order to allow VNC but I the system is not able to load the desktop environment. Samba server is working continously very well.

Does someone any idea how could I get back my ubuntu desktop?[B]

L.B.
[/B]

---

### Post by unlimitedz on 2009-07-13
Do you get a login prompt?  if not can you access your other TTY's?  (ctrl+alt+f1, f2, etc)?

---

### Post by bl305 on 2009-07-13
yes, I have a login prompt! After loging on in desktop environment while loading the graphical thing the Operating system jumps back to the login window.

At the login window I have the possibility to select different login mode. The ssh is working, but this way I only have a command prompt.

This command prompt could be very good for repairing the OS. Network mode is also working from this command prompt.

L.B.

---

### Post by unlimitedz on 2009-07-13
OK, drop to TTY1 and login.  then make a backup of your xorg.conf file (\etc\X11\xorg.conf)

run sudo gdm stop

and then run [I]sudo dpkg-reconfigure xserver-xorg

[/I]Follow the onscreen prompts.  Once finished do

sudo gdm start

you may have to do sudo startx also, not sure

switch back to TTY7 and see if anything is different.  You may need to reboot first.

If this ends up breaking it, revert back to the old xorg.conf file.

---

### Post by bl305 on 2009-07-13
> **unlimitedz said:**
> OK, drop to TTY1 and login.  then make a backup of your xorg.conf file (\etc\X11\xorg.conf)

run sudo gdm stop

and then run [I]sudo dpkg-reconfigure xserver-xorg

[/I]Follow the onscreen prompts.  Once finished do

sudo gdm start

you may have to do sudo startx also, not sure

switch back to TTY7 and see if anything is different.  You may need to reboot first.

If this ends up breaking it, revert back to the old xorg.conf file.

Thx, I try it out...

---

### Post by bl305 on 2009-07-14
unfortunately it does not work. I think the the only solution could be the reformat and reinstall the system...

> **bl305 said:**
> Thx, I try it out...

---

