---
title: "Installing older nvidia drivers"
date: 2010-01-11
forum: Hardware
---

### Post by rednick on 2010-01-11
Hi. I've installed Ubuntu 9.04 on an old laptop I have been given.  It bears the logo "Designed for Microsoft Windows XP" but it could have fooled me because it won't run it!

It will run Ubuntu but even 2D graphics performance is hideous. GNU Backgammon in 2D mode lags horribly and 3D mode won't even run.

Rough Spec is as follows
Celeron Mobile 1.5GHz, 384MB RAM, 20GB drive and GeForce Go 4400 graphics.
From what I can gather the last nVidia proprietary driver to support my card
was version 1.0.9626.  I have found a .run file for this but no Debian packages.

The problem is if I run it in INIT1 I can't get network support and it requires web access to download some kernel components.  If I run it INIT3 (as the installer suggests) it fails because an X server is running.  Also it keeps referring to kernel version 2.4 not 2.6.x as is current.

Is it possible to install proprietary drivers for my card on this version of Ubuntu? If anyone has successfully done so, please would you walk a clueless n00b through the process of how.

---

### Post by mocoloco on 2010-01-12
I thought that card was still supported?  Do you not have a driver to install if you open System > Administration > Hardware Drivers?

---

### Post by rednick on 2010-01-12
Looking at the nVidia site re the current drivers, the GeForce FX4400 Desktop card is supported as are GeForce Go 6xxx cards for laptops, but not the Go 4xxx series.

Going into the Hardware Drivers, yes there are some to install but on restart, X launches and I have a black screen with no image at all. I then have to reboot to a command prompt and manually edit the xorg.conf file to use the driver "nv" to restore any visual output in Ubuntu.

So I gave up on those ones and tried the ones from the nVidia site that listed my card as supported.

---

### Post by rednick on 2010-02-23
UPDATE

Finally found a fix for this.
In the nVidia binary drivers manual page (OK, OK, I know) it mentions the black screen problem - the nVidia driver defaults to D-SUB output, not the laptop screen! Fix is as follows

Install the nVidia drivers from System > Admin > Hardware Drivers.
Reboot - you'll get the Ubuntu startup noise and a blank screen
Now pressCTRL-ALT-f1 to return to console and log in if nec.
sudo nano /etc/X11/xorg.conf
Add a line Option in the Screen section: Option "UseDisplayDevice" "DFP"
Save and reboot.

On my laptop this still left the problem of the nVidia driver incorrectly detecting the native resolution of the laptop's flat panel. If you find yourself in this situation, do a web search on "customEDID" for a fix.

---

