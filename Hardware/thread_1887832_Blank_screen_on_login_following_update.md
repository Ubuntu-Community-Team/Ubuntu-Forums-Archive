---
title: "Blank screen on login following update"
date: 2011-11-28
forum: Hardware
---

### Post by wanichan on 2011-11-28
I recently installed a lot of updates on a 10.10 for my Toshiba NB205.

But now when I boot up, I get the blinking cursor, it goes to a black screen, and makes the "drum" sound but then all I get is a blank screen. I tried raising the brightness key to no avail.

So I logged in using nomodeset via grub and do:

sudo service gdm stop
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
startx

Then it loads into x and I can do my work.

It also seems to be the gnome rather than unity desktop that came with the original netbook edition I had installed on this thing. Which is fine, but (1) I'm curious what caused this problem in the first place and (2) whether it is safe to restart it without going back to the blank screen issue on boot. It just seems in general something got messed up with the xorg.conf file during the updating sequence and I have no idea what happened.

Here are the specs from LSPCI that relate to the graphics card:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60


thanks.

---

