---
title: "Resume/Thaw issue in 12.04"
date: 2013-01-23
forum: Hardware
---

### Post by Byb on 2013-01-23
Hi world
I need your help.
My Dell latitude D800 shows black screen on Resume/Thaw. I use kernel 3.2.0-36-generic with the new nvidia-96.43.23 which now makes my nv28 GeForce4 4200Go laptop video board working, and gnome-shell.
To have resume/thaw to work, I have to close my X session, then switch to console and send a sudo pm-suspend or pm-hibernate (so making pm features useless).
From X session, when I get the black screen, the kill x shortcut does not seem to do anything, only the shortcut ending with "B" ;) does the same thing a long press on power button does. I even can't switch to console, the shortcut won't display it.
The pm-suspend log does not seem to show any error.
I was advised to 
```
GRUB_CMDLINE_LINUX_DEFAULT="noquiet nosplash"
GRUB_TERMINAL=console
```with no difference
Thank you for help please

[EDIT]: additional info, not sure if related with the issue:
When normal booting or from thaw, while loading grub, my system often sends a lot of beeps. There is a very short time and little message on the top left on the screen I reached to capture with a camera in movie mode, stating```
error: no video mode activated
```, then the usual grub menu is displayed in (25x80 characters mode)

---

### Post by Toz on 2013-01-23
I know the post is a little dated, but you might want to give this a try: [http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/").

---

