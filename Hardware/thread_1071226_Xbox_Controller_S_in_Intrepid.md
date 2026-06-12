---
title: "Xbox Controller S in Intrepid"
date: 2009-02-15
forum: Hardware
---

### Post by Zeikcied on 2009-02-15
I'm having trouble getting the Xbox Controller S to work in Intrepid.  I don't know if it's a KDE4 issue or not.

I found the page on lshal as well as the bug report.  They claim that an update to xserver-xorg-input-evdev (or something like that) fixes the issue.  But I have the update those pages mention, but it still doesn't work.  I also installed xserver-xorg-input-joystick just to make sure, and that didn't help.

I did use a .fdi file for my Sixaxis controller a couple months ago, so I don't know if its presence is messing anything up, though I doubt it.

All the Controller S does is move the mouse with the left analog stick.

I did make lshal and diff files based on the one tutorial (before I actually bothered to read that it has been supposedly fixed), so I have those if they are necessary.

---

### Post by Zeikcied on 2009-02-19
I tried the userspace driver, but it didn't work.  The kernel module xpad keeps loading when I plug my controller in, and I don't know how to stop it from doing so (other than the rmmod command every time it loads).

The userspace driver won't even start, because it keeps giving me errors about not having access to uinput (which I don't know how to fix because the guide on this forum for the driver is outdated), or that uinput and/or joydev aren't loaded (which they are).

I think the guide says that the original Xbox controllers should work with xpad, with little issue.

Now, I know that xpad recognizes my controller.  The Joystick section on the Keyboard and Mouse settings page (in KDE4) lists my controller.  (Though it lists it as Xbox Controller Japan.)  So it at least recognizes it, but it doesn't properly set it up for some reason.

---

### Post by Zeikcied on 2009-03-18
Can anyone help?

---

