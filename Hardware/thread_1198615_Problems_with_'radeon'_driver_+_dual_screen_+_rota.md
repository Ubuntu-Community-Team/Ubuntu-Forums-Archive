---
title: "Problems with 'radeon' driver + dual screen + rotate"
date: 2009-06-27
forum: Hardware
---

### Post by zcrar70 on 2009-06-27
Hi,

I'm trying to set up the following:

* dual monitors, 1920x1200 + 1024x1280
* the second monitor is a 17", rotated 90 degrees to the left
* the second monitor sits to the right of my main 24"

This is using the 'radeon' open source driver in Ubuntu Jaunty x64.

I can get this to work with xrandr, but I can't get it to work by editing the xorg.conf file; this is annoying, because it means that the GDM logon screen isn't displayed at the correct resolution, and that the screen flickers just after logging in as xrandr is run (I have it running in my .xsession file.)

Here's my xorg.conf - note the 'Rotate' option is commented out:

```
Section "Monitor"
    Identifier	"HP LP2475W"
    Option      "PreferredMode" "1920x1200"
EndSection

Section "Monitor"
    Identifier	"HP L1740"
    Option      "PreferredMode" "1280x1024"
    #Option      "Rotate"      "left"
EndSection

Section "Screen"
	Identifier	"screen0"
	Monitor		"HP LP2475W"
	Device      "Radeon 4850"
	DefaultDepth 24
	SubSection "Display"
            Depth   24
            Virtual	3200 1280
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Monitor		"HP L1740"
	Device      "Radeon 4850"
	DefaultDepth 24
	SubSection "Display"
        Depth   24
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier  "Multihead"
	Screen      "screen0"
	Screen      "screen1" RightOf "screen0"
EndSection

Section "Device"
    Identifier	"Radeon 4850"
    Driver      "radeon"
    Option      "Monitor-DVI-0" "HP L1740"
    Option      "Monitor-HDMI-0" "HP LP2475W"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

The 'rotate' option doesn't seem to be doing anything - if I set the virtual screen to be the correct size (2944x1280), the display on the second screen is correctly rotated in GDM, but it is mirrored to display the main screen, the GDM on the main screen only takes up half of the display, and the second screen displays garbage once I log in; if I set the virtual screen to what it is now, the rotate option just doesn't do anything (i.e. the second screen doesn't mirror the main screen anymore, but it isn't rotated at all.)

Does anyone have any suggestions on how to fix this?

thanks,
Nick

---

