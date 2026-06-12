---
title: "HP 2740p Tablet Calibration"
date: 2014-05-19
forum: Hardware
---

### Post by cfmackey on 2014-05-19
Hello everyone,
I've recently got my hands on the fantastic HP Elitebook 2740p hybrid notebook. It features both a multitouch display *and* a digitizer pen display. So far I've had terrific luck with this machine, except for the accuracy of the digitizer.

The digitizer's accuracy seems to be a millimeter off as soon as you approach a corner. So I got to calibrating it with xinput-calibrator
```
[SIZE=2][FONT=courier new][COLOR=#000000]collin@Lizzy:~$ xinput_calibrator --device 13[/COLOR]
[COLOR=#000000]Calibrating standard Xorg driver "Serial Wacom Tablet stylus"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]current calibration values: min_x=0, max_x=26312 and min_y=0, max_y=16520[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]--> Making the calibration permanent <--[/COLOR]
[COLOR=#000000]  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)[/COLOR]
[COLOR=#000000]Section "InputClass"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Identifier[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"calibration"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]MatchProduct[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"!!Name_Of_TouchScreen!!"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"MinX"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"118"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"MaxX"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"26225"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"MinY"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"-45"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"MaxY"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"16338"[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"SwapXY"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"0" # unless it was already set to 1[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"InvertX"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"0"  # unless it was already set[/COLOR]
[COLOR=#000000]    [/COLOR][COLOR=#000000]Option[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"InvertY"[/COLOR][COLOR=#000000]    [/COLOR][COLOR=#000000]"0"  # unless it was already set[/COLOR]
[COLOR=#000000]EndSection[/COLOR]

[COLOR=#000000]Change '!!Name_Of_TouchScreen!!' to your device's name in the config above.[/COLOR]
[COLOR=#000000]collin@Lizzy:~$ [/COLOR][/FONT][/SIZE]

```

And then, as instructed, I put that in to a newly created /usr/share/X11/xorg.conf.d/99-calibration.conf file, restarted, and experienced absolutely no change.
So I did the whole thing over again, but this time dumped the output into /usr/share/X11/xorg.conf.d/10-evdev.conf in the "evdev tablet catchall" section, same result, nothing.

Any pointers or advice at this point would be a great help, I'm immensely lost and I need to use the digitizer function on this notebook for school.

Cheers!

---

