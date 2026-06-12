---
title: "AddScreen/ScreenInit Failed for driver 0..."
date: 2008-12-31
forum: Hardware
---

### Post by icanfly0307 on 2008-12-31
Hi,
   Whenever I start up my laptop, it tries to start the X Server but fails and drops to the shell prompt. I've tried logging in by manually typing [FONT="Courier New"]startx[/FONT], but it returns this error:

[FONT="Courier New"](EE) I810(0): [agp] Unable to bind system texture memory. Diabling DRI.

Fatal Server Error:
AddScreen/ScreenInit failed for driver 0

waiting for X server to begin accepting connections.
giving up.
xinitL Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.[/FONT]

I'm running an Intel 82815 Graphics Card with the i810 driver. I've tried the intel driver but it didn't work either. :(

Any suggestions? Thanks for your help.

---

### Post by supert8ch on 2009-12-13
I ended up with the same issue. This is after trying to use external display. I checked the log and there is lots of information in there but I have no clue how to read it. How did you get yours fixed?

---

### Post by gartechnical on 2011-03-18
I had the same issue with the server 10.10  I started it in failsafe mode. I would try to run startx and it came up with the addscreen screeninit failed for driver 0.  I restarted and selected failsafe mode.   The gui then started ok.  When I got to the desktop, a message appeared in the upper right corner of the screen saying no driver was installed and it was using the default driver.  I clicked on the icon in the system tray and picked the recommended driver for my graphics card.  It downloaded it and then was was asked to reboot.  The gui came up ok after that.

---

