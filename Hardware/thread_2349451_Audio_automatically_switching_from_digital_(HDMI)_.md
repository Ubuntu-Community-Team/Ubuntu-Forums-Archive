---
title: "Audio automatically switching from digital (HDMI) to analog"
date: 2017-01-14
forum: Hardware
---

### Post by primuspaul on 2017-01-14
I run these two scripts that worked perfectly on Mint to switch between my monitor and HDTV. DVI uses 3.5mm speakers and HDTV gets the signal via the HDMI port. Unfortunately, now on Ubuntu, it works, but after a few minutes of HDMI usage, it switches the sound (HDMI remains on) to Analog and disables the HDMI sound. Is there a way to keep it from switching from one output to the other automatically?

```
xrandr --output HDMI-1 --off --output DVI-I-1 --auto
pacmd set-card-profile 0 output:analog-stereo

``````

IN="DVI-I-1"
EXT="HDMI-1"

if (xrandr | grep "$EXT connected"); then
    xrandr --output $IN --off --output $EXT --auto
    pacmd set-card-profile 0 output:iec958-stereo
else
    zenity --info --text="HDTV NOT CONNECTED!"
fi

```

---

### Post by primuspaul on 2017-01-15
Well, I'm still testing it, but I think I figured it out. The computer has a device installed that provides front USB and audio/mic jacks. Apparently, one of them died and is going crazy turning on/off, prompting Ubuntu to stupidly change between audio output jacks, with no apparent way to disable the arbitrary behavior. My solution was to plug a blank 3.5mm (bulk solder on connectors I bought for something else) TRRS jack into it and just leave it there.

But seriously, why not put in an option to disable the auto switching? A simple problem as this shouldn't require a hardware solution.

---

