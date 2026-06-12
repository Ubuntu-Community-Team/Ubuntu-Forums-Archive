---
title: "Ubuntu won't recognize my VGA connected TV"
date: 2009-12-16
forum: Hardware
---

### Post by tylersontag on 2009-12-16
Hey all, I’m building a media center out of an old desktop (which has turned into discovering all the components are bad and basically bareboning a new computer &#61514; )to hook into my new Sharp 42’’ LCD TV ([http://www.sharpusa.com/ForHome/Home...C42SB45UT.aspx](http://www.sharpusa.com/ForHome/Home...C42SB45UT.aspx)) and I’m having a problem getting 9.10 to detect it.

I had an old CRT that I did the install on and it detected it fine (Display shows 16’’ Whatever Monitor) and even loaded with support up to 1100~x900~ resolution. Now if after a boot I just plug in my TV it looks fine, displays fine.

However, when I reboot with the TV hooked up, it boots to 800x600 and the display panel shows “Unknown Device” So I’ve been using xrandr just to manually add the resolutions I want but I have to do it every boot. Im using my motherboards integrated Intel GMA X4500 video card and haven’t installed anything special in the way of drivers past a fresh install of Ubuntu 9.10, it looks good, runs compiz fine. I suppose in my startup file I could just put the 3 commands that create/add/set the resolution but that seems kinda hacky. Any ideas?

And, on a lesser note, you’ll notice on that TV’s page, it claims Full HD 1080p (1920 x 1080) Resolution. But when I use xrandr to set that resolution (60 and 120 Hz) it won’t display and says to drop it down to 1600x1400. I’m running this through a VGA cord, maybe it can only take 1920x1080 through an HDMI cord, I don’t know, just thought I’d toss that out there too. Thanks for any help, im pushing 2 years since I dropped windows and went 100% Ubuntu (minus a virtual box of XP) and lovin it.

---

### Post by DaVince21 on 2009-12-16
> However, when I reboot with the TV hooked up, it boots to 800x600 and the display panel shows “Unknown Device” So I’ve been using xrandr just to manually add the resolutions I want but I have to do it every boot. Im using my motherboards integrated Intel GMA X4500 video card and haven’t installed anything special in the way of drivers past a fresh install of Ubuntu 9.10, it looks good, runs compiz fine. I suppose in my startup file I could just put the 3 commands that create/add/set the resolution but that seems kinda hacky. Any ideas?

I suggest you edit /etc/X11/xorg.conf - you can set custom resolutions there based on modelines.

It looks a bit like this (for me at least, I actually added new modes for the first time myself today):

```
Section "Device"
	Identifier      "Intel 945G "
	Driver         "intel"

	Option          "monitor-VGA1" "vga"
	Option          "monitor-LVDS" "lvds"
EndSection

Section "Monitor"
	Identifier      "vga"

	# Let's add undetected resolutions to our VGA1 device.
	ModeLine	"1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
	ModeLine	"1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
EndSection
```
You seem to know a bit about adding modes and setting resolutions from the command line, so I think you can take it from here and change what's necessary. If not, I'm willing to point out what's what.

---

### Post by tylersontag on 2009-12-22
Hmmm, this is a fresh, clean install of 9.10 and to my suprise, since i had thoguth to check the .CONF file earlier... there is none.  There is an XORG.CONF.Failsafe file but even lookign for hidden files... no XORG.CONF

I tried adding your configurations to my *.Failsafe file but next reboot did not have an effect.

X hasn'd abandoned the conf file has it?

---

### Post by tannedin on 2010-03-25
> **tylersontag said:**
> Hmmm, this is a fresh, clean install of 9.10 and to my suprise, since i had thoguth to check the .CONF file earlier... there is none.  There is an XORG.CONF.Failsafe file but even lookign for hidden files... no XORG.CONF

I tried adding your configurations to my *.Failsafe file but next reboot did not have an effect.

X hasn'd abandoned the conf file has it?

Add it to your xorg.conf file, anything that follows (ex xorg.conf.failsafe or xorg.conf_bu) won't be read by the system.

---

