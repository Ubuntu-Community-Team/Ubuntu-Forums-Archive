---
title: "Impossible to restore xorg.conf"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by isenalim on 2007-11-09
Hi,
I have a fresh Gutsy installation on a Vaio laptop FE41M with Nvidia Go 7400 card. I am using the proprietary drivers and everything was fine until I had to connect the laptop to an external beamer through the VGA port. 

I thought that the new "Screens and Graphics" applet would do the job but it didn't work quite well: only 640x480 resolution on the VGA port and no clone output on my laptop screen, probably due to bad refresh rate. Anyway, the good thing is that I managed to do my presentation.

Luckily, somehow a backup of xorg.conf was automatically done to xorg.conf.1. The bad thing is that if I copy back the old xorg.conf.1 to xorg.conf, it is again automatically changed!

As a result, I have a bad resolution on the login screen. After login I have my old native resolution, 1280x800, which I could restore only using the Screen Resolution applet under the System - Preferences menu ( the new Screens and Graphics and nvidia-settings couldn't permanently restore my original resolution, I had to change it after every login!)

The second bad effect is that on the text console (ctrl+alt+Fx) I had almost unreadable characters, they are "shadowed" in some sense...

I also have exactly the same problem on Vaio FZ11Z with Nvidia Go 8400 Graphic card after I tried to connect an HDTV to the HDMI port...

Why does xorg change xorg.conf at every restart of the X session? how can I avoid it?

Thanks a lot!

---

