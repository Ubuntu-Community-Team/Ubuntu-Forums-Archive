---
title: "help configuring Mobile Intel(R) 4 series Express Chipset Family GMA 4500MHD"
date: 2009-03-01
forum: Hardware
---

### Post by Diabolis on 2009-03-01
HP dv5-1235dx
Generic PnP Monitor
Mobile Intel(R) 4 series Express Chipset Family
Adapter string / Media accelerator GMA 4500MHD

```
sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

```
cat /var/log/Xorg.0.log | grep EE
(EE) VESA(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration.

*and then this shows up*

giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

```
sudo cat /var/log/Xorg.0.log | grep Not

(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)

```

Edited the xorg.conf file to look like this:
```

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
	DefaultDepth	8

	SubSection "Display"
        Depth       16
        Modes       "1280x800" "1024x768"
    EndSubSection

    SubSection "Display"
        Depth       32
        Modes       "1280x800" "1024x768"
    EndSubSection
EndSection

```

Still get the same errors.

---

### Post by Diabolis on 2009-03-01
Another clue:
```

cat /var/log/Xorg.0.log | grep hsync
(II) VESA(0): Modeline "1280x800"x0.0 69.30 1280 1328 1352 1416 800 803 809 816 -hsync -vsync (48.9 kHz)
(II) VESA(0): Configured Monitor: Using hsync value of48.94 kHz

```

edited xorg.conf file:
```
Section "Monitor"
	Identifier   "Configured Monitor"
	HorizSync    60.0
EndSection

```

no luck

---

### Post by Diabolis on 2009-03-01
just had to change the xorg.conf file from vesa to intel :-S

---

### Post by Sodlig on 2010-01-14
I'm at this stage at the moment, where I installed Ubuntu onto my laptop which came out with XP.

Every driver got automatically installed besides my gfx, Intel Mobile 4 Series Chipset Integrated.

Obviously it looks like you did an installation of it, and I'm unable to find an Ubuntu version of it on Intels official site so I was wondering if it was a way to install it properly anyways.

I'm quite of a beginner to it all, so I would appreciate if I a simple step-by-step post could be made by someone.

Thanks in advance,
Sodlig.

---

### Post by DpinkyandDbrain on 2010-01-15
cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "i810" (module does not exist, 0)


I get this when i did your past instructions what does this mean and how do i resolve this?

---

### Post by Clark3934 on 2010-03-24
I get a similar output on Lucid Beta 1

$ cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

---

