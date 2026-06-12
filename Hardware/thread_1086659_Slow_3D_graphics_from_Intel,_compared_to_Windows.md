---
title: "Slow 3D graphics from Intel, compared to Windows"
date: 2009-03-04
forum: Hardware
---

### Post by theresonant on 2009-03-04
Hey all!

I have a HP 530 laptop, that came with an Intel graphics card. 'lspci' says this:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

Things work relatively well, resolution is ok, 2D graphics ok, but Compiz effects work kinda slow. The DesktopCube is laggy if I have more than 8 windows opened across all the workspaces, and if I use 'ElevateWindows' plugin, it's a killer... lagging is very obvious then. The 'Burn' effect is very slow for large windows, maybe rendering 2 or 3 or less frames only during the opening of a fullscreen window. Once I enabled the 'BicubicFilter', and the next time I opened a window, the screen got filled with garbage and I had to disable it by logging in to Enlightenment.

Also, TORCS is slower too in Ubuntu, having almost half the framerate it had in Windows when I tried it (which was around 70). That goes for most games. Also tried Warsow, which in Windows was running at highest resolution without a glitch, but in Ubuntu I'm forced to keep it to 800x600 with almost everything disabled or set to low quality. 

When I play games in Ubuntu I have to turn off Compiz and fall back to Metacity, otherwise the screen might flicker alot during gameplay, or simply the 3D won't get initialised. Therefore I run games with direct rendering enabled, yet they are still slow.

I know my graphics card is quite ok, I play NFS Underground 2 with high quality effects and high resolution and no frame lagging on my laptop (and other games that were very graphically demanding a few years ago).

This isn't really killing me (it's just slower eye candy, I can work without problems), but I'd like to see my graphics card running well in Ubuntu too. I know that Intel made their drivers open-source a while ago. 

Any hints? Thanks! And sorry for the long post.

EDIT: /etc/X11/xorg.conf contains:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Actually these are the ONLY lines in xorg.conf (except for the comments at the top). It doesn't really look like it uses the intel driver, does it?

---

