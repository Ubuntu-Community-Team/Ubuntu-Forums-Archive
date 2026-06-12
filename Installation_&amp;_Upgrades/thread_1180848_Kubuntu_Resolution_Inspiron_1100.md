---
title: "Kubuntu Resolution Inspiron 1100"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by sparvik on 2009-06-07
I am sure there is a post started on this already but I can't find it.

I installed Kubuntu 9.04 on my NB.  When first booted it had the wrong resolution.  I edited my xorg.conf to allow for higher resolution and rebooted (restarting X came back as x already running).
When it came back up the resolution was correct but all I had was a black screen with the mouse pointer.
I then tried deleting my xorg.conf and tried again since you could do this in earlier distros. Black screen no mouse or backlight.  
Recover mode fix display, black screen with mouse wrong resolution. dpkg-reconfigure the xorg from command line
black screen, mouse, correct res.
I then plugged the HDD into another computer and checked out my xorg.conf 
it is set back to the generic file settings.

Am I hosed, or is there a package that I can apt-get instead of starting from scratch again?

*I found out that alt+f2 and alt+f1 allow me to open apps but it seems that the desktop manager, panels, or widgets wont start while they started fine when I had the wrong resolution*

---

### Post by sparvik on 2009-11-04
Months later installed again using usb-key and a new iso download, worked fine

---

