---
title: "New Version of Ubuntu &amp; ThinkPad ATI Radeon Mobility 7500 Support/Drivers?"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by n1nj4Lo on 2007-08-14
Main question is has Ubuntu finally decided support ThinkPad a31's built in video card: ATI Radeon Mobility 7500, Or has anybody come across or made any good working and successful drivers for this card and gotten dual display/monitors to be supported and enabled? 

Thanks

---

### Post by overdrank on 2007-08-15
> **n1nj4Lo said:**
> Main question is has Ubuntu finally decided support ThinkPad a31's built in video card: ATI Radeon Mobility 7500, Or has anybody come across or made any good working and successful drivers for this card and gotten dual display/monitors to be supported and enabled? 

Thanks

Hi if you have not found a solution to your issue, I have used this "how to" to install on a dell c 640 with that graphics card
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Hope it helps. Good Luck!:)

---

### Post by n1nj4Lo on 2007-08-15
I done the above stated and mine still says:
> server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Tungsten Graphics, Inc.

Instead of: 
> server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
which I believe is what it's supposed to be, I even saved the notepad when editting it and then restarted to promptly make sure of it taking effect...

---

### Post by overdrank on 2007-08-15
Hi are you able to get yes with the command 
```
glxinfo | grep "direct rendering"
```

---

### Post by n1nj4Lo on 2007-08-15
It says "No" everytime I try....

---

### Post by overdrank on 2007-08-16
> **n1nj4Lo said:**
> It says "No" everytime I try....

Ok sorry for the delay, maybe try this thread as it worked for the ATI 7000
[http://ubuntuforums.org/showthread.php?t=246746&highlight=ATI+Radeon+Mobility+7500](http://ubuntuforums.org/showthread.php?t=246746&highlight=ATI+Radeon+Mobility+7500)
I hope this helps. Good luck!

---

### Post by DwightDE on 2007-11-08
Fixing dual monitor output for IBM/Lenovo Thinkpad T42 and others with ATI Radeon Mobility 7500:

First, fix any funny stuff in /etc/X11/xorg.conf by following instructions at the top of that file.  That is, do:

[FONT="Courier New"]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT]

Then, in the "Display" SubSection of the "Screen" section of xorg.conf, add:

[FONT="Georgia"]Virtual 2304 1024[/FONT]

where 2304 is the sum of your monitor widths, and 1024 is the greatest monitor height.

Then remove that annoying line that prevents the right alt key from working.

Restart the x server (or reboot).

Then run the commands:

[FONT="Georgia"]xrandr --output VGA-0 --right-of LVDS
xrandr --output VGA-0 --mode 1280x1024[/FONT]

where 1280x1024 is the resolution of your external monitor.

You should probably put these in a script so you can execute them easily after logging in.

The script file would look like:

[FONT="Georgia"]#! /bin/sh
xrandr --output VGA-0 --right-of LVDS
xrandr --output VGA-0 --mode 1280x1024[/FONT]

Don't forget to mark it as executable.

---

### Post by DwightDE on 2007-11-08
Oops.  That assumes that your external monitor is an LCD type.  That's where the "LVDS" comes in.  Run xrandr without parameters to see how it sees your external monitor and use the appropriate designation.

---

