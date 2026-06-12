---
title: "Intel Display Problem Only on Karmic/Gnome"
date: 2010-03-10
forum: Hardware
---

### Post by ggordon on 2010-03-10
I have a Samsung SyncMaster 2343 and Intel 82G33/G31 graphics controller.  It has worked fine displaying 2048 x 1152 with Intrepid and Jaunty.  I upgraded to Karmic today and can no longer display at high resolution with GNOME.

2048 x 1152 does work fine for the following with Karmic:

[INDENT][LIST]
[*]KDE
[*]xfce
[*]GNOME failsafe
[/LIST][/INDENT]

If I use Linux kernal 2.6.28-18 it does work fine with GNOME, except Compiz can't find the drivers it wants.  The problem occurs with the default kernal 2.6.31-20 that was installed with Karmic.

This is not the problem that many people have had where the higher resolution is not displayed as an option that they can select.  Rather, in order to start GNOME I have to first log on using something like KDE and set the resolution lower, log out, and then log in to GNOME.  If I try to log on to GNOME with the resolution at 2048 x 1152, or log on with a lower resolution and then change the resolution to 2048 x 1152, the screen goes black with what appears to possibly be the entire display squeezed into the width of a few pixels on the left edge of the screen.  Or I might be seeing the the few pixels on the rightmost part of the display over on the left edge.

I can't make sense out of this.  If it's a driver issue, why does it only fail for GNOME, but not the other display managers.  I don't know much about the GNOME failsafe mode, but if it is a GNOME issue, why can I use the high resolution with GNOME failsafe, but not regular GNOME?

---

### Post by ggordon on 2010-03-10
Well, I seem to have fixed the problem.  I had given up for now and started working on a sound problem. I was following a guide for correcting my sound problem that involved purging and reinstalling some packages.  That had a side effect of removing gdm and ubuntu-desktop, which then had to be reinstalled.  It appears that reinstalling them somehow fixed my problem.

I now have a 2048 x 1152 display on GNOME.  :p

---

