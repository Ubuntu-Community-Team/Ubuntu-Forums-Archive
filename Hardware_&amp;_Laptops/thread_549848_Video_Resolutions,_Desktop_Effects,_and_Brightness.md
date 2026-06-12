---
title: "Video Resolutions, Desktop Effects, and Brightness controls, Oh My!"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by Rockman4140 on 2007-09-13
> After struggling to get my wifi working, I've decided to attempt to get Ubuntu looking as snazzy as I can. I was going t use Beryl on my computer, but noticed it is being re-merged with Compiz, so instead I want to use CompizFuzion. I can config it, and I've attempted to run it with no go. I'm getting the dreaded "The Composite Extension is not available" error, and I'm scared my card may not be strong enough.

I'm running an ATI Radeon X1200 card, glxinfo | grep direct proved Yes

I also was wodering what decent widescreen resolutions are, and why X wouldn't let me use aything but the basic 640x480,800x600, and 1024x768.

Finally, not being able to switch my brightness with my power management programs suck. I have a Toshiba Satelite A215-S4817 if that would help.

Everyone's help is very much appreciated more than you could ever know.

After messing around and attempting to get my stupid ATI card using a normal widescreen resolution, I have stumbled upon a plethora of very distressing issues.

- I am playing a game of Russian Roulette with X right now, 1 out of 3 shots with turning my computer on and booting into Ubuntu work. It seems that when it does work, WICD doesn't. I stall on X before I get to the login screen, and restarting is of no use.

- After downloading a GUI to edit my xorg file, I still cannot get my blasted card to go into 1440x900 or whatever. The config file looks fine, but whenever I use anything but the fglrx driver, I get a no screen found error.

- PowerPLAY apparently doesn't work on my chipset, and I have a feeling that may come into play with the brightness, Why can't ATI work out a better driver for Linux?

I am so close to ripping my hair out. I want so bad to use Ubuntu, but if these problems keep coming up, I'll be very depressed. Vista is so slow and weak compared to Ubuntu, but the compatibility is what I need most of right now.

Any help would be oh so greatly appreciated.

---

### Post by Rockman4140 on 2007-09-16
WICD is now in on the game of Russian Roulette. Sometimes when loading WICD, it won't connect to my access point at all. It's very confusing, to connect one session, shut down, and it not working again.

---

### Post by Rockman4140 on 2007-09-25
I've killed the wicd program and killed the tray.py program, and restarted X, but even after booting without net access, I cannot re-run it and attempt to get access. Does anyone know a tip I may be missing out on?

---

### Post by Rockman4140 on 2007-10-04
The Resolution is killing me. I got the mouse working, WICD isn't acting up, my mouse chugs along at full speed, so only my headphones not working and this widescreen deal is the last blocks toward Vista independence.

I attempted a modeline for a 1440x900 Resolution, but it turns out X barfs up whenever I feed it that. Here's the errors.

gtf 1440 900 60
```
  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

```

```
(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Toshiba Widescreen TFT 15.4: Using hsync range of 30.00-70.00 kHz
(II) VESA(0): Toshiba Widescreen TFT 15.4: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Not using mode "1440x900" (no mode of this name)
(II) VESA(0): Not using mode "1200x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Toshiba Widescreen TFT 15.4: Using hsync range of 30.00-70.00 kHz
(II) VESA(0): Toshiba Widescreen TFT 15.4: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Not using mode "1440x900" (no mode of this name)
(II) VESA(0): Not using mode "1200x800" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x350"
(**) VESA(0): Display dimensions: (330, 210) mm
(**) VESA(0): DPI set to (78, 92)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (122)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (121)
(II) VESA(0): Attempting to use 85Hz refresh for mode "720x400" (136)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x400" (186)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x400" (186)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x350" (1c6)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
```

I'm still using the VESA driver since fglrx and ATI haven't worked for beryl running, but if I can't even get a resolution that doesn't give me a freakin headache, I guess I shouldn't worry. Any help would be much appreciated.

---

### Post by Zimmer on 2008-02-23
Where did you get the info for the Modeline you created? And did you put a corresponding 
'Modes' statement in the Screen section of the xorg.conf?

See if post #3 helps with your problem..
[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

Regards
Zimmer

---

