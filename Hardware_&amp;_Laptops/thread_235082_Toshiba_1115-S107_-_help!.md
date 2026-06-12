---
title: "Toshiba 1115-S107 - help!"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by ThAixStYLe on 2006-08-12
I was able to create a dual-boot setup for Windows/Ubuntu on my laptop fine.  When running off of the LiveCD everything seemed to be fine--everything appeared to be functional with just about all my hardware recognized.  However, I noticed that occasionally, my system would freeze.  I attributed this to some kind of driver incompatibility and decided that I would go ahead with installation and solve this matter afterwards.  I also noticed that "buttons" would be rendered with artifacts occasionally.  These artifacts appeared as dots that would disappear whenever the button was refreshed (by doing a rollover).  I attributed this to my graphics driver and assumed that everything would be fine after configuring everything correctly.

So far, my endeavors to address both these issues has been unfruitful at best.  I still get the artifacts on the buttons, and the freezing has gotten worse.  I have run numerous hardware diagnostics to determine if either my RAM, HDD, or MB were having some problems, but I found that all were functioning just fine.  Some sectors of the HDD were beginning to deteriorate, having read times, but nothing too bad.  My RAM passed the tests perfectly as well as the MB.

When the comp freezes, everything becomes unresponsive--mouse does not move and I can't use any keyboard shortcuts to supplement the loss of the mouse.  All I can do is power off the laptop and power it back on.  I tried to isolate the problem to a single application, but this appears to happen randomly no matter what application I use.  Sometimes I can use Ubuntu for an extended period of time and sometimes the comp freezes as soon as I access the applications menu or run Firefox.

Like I said before, I'm not sure if this is a driver related issue because Ubuntu seemed to recognize all my hardware just fine.  I verified this by checking the device manager.

I don't know how else to proceed.  Any help would be greatly appreciated.  Thanks in advance!

---

### Post by endlesssnowfall on 2006-08-13
I have a Toshiba 1115-S103 dual booting Ubuntu/Windows as well.  The way I fixed the artifacts on buttons problem was by doing the following:

In terminal:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

Then, in the Section "Device", add the line 

> 
Option "RenderAccel" "false"

Here's what mine looks like:

> Section "Device"
[INDENT]Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY"[/INDENT][INDENT]Driver		"ati"[/INDENT]	[INDENT]BusID		"PCI:1:0:0"[/INDENT][INDENT]Option		"RenderAccel" "false"[/INDENT]EndSection

Once you're done, restart X with Ctrl+Alt+Backspace.  If you run into any problems restarting, just use the xorg.conf.backup.

As for the freezing problem, I also ran into that whenever I tried installing AIGLX, or the "radeon" driver instead of the "ati" one that came default.  If you have a newer ATI graphics card, you might try installing the fglrx drivers.

---

