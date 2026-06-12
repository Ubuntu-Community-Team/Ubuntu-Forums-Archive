---
title: "Can't enable horizontal edge scrolling on touchpad"
date: 2016-12-12
forum: Hardware
---

### Post by dsirus5 on 2016-12-12
Greetings all,

I recently switched back to Ubuntu Gnome 16.10 in the course of my semi-annual distro-hopping.  To my mild consternation, edge-scrolling did not work by default, and there was no obvious GUI setting to turn it on; however, after a bit of Googling and a bit of fiddling, I got it working with a one-line script in ~/.config/autostart (which just runs "/usr/bin/xinput set-prop 11 291 0, 1, 0" - it turns out device #11 is my touchpad and setting #291 is "scroll method enabled").

This got edge-scrolling working just fine - along the VERTICAL axis.  For reasons I have been unable to determine, and in spite of much Googling and much fiddling, I can't get HORIZONTAL scrolling working.

When I run "$ xinput list-props 11", I get this output:
```
Device 'SynPS/2 Synaptics TouchPad':    Device Enabled (145):    1
    Coordinate Transformation Matrix (147):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (298):    1
    libinput Tapping Enabled Default (299):    0
    libinput Tapping Drag Enabled (300):    1
    libinput Tapping Drag Enabled Default (301):    1
    libinput Tapping Drag Lock Enabled (302):    0
    libinput Tapping Drag Lock Enabled Default (303):    0
    libinput Accel Speed (281):    0.360294
    libinput Accel Speed Default (282):    0.000000
    libinput Natural Scrolling Enabled (286):    0
    libinput Natural Scrolling Enabled Default (287):    0
    libinput Send Events Modes Available (265):    1, 1
    libinput Send Events Mode Enabled (266):    0, 0
    libinput Send Events Mode Enabled Default (267):    0, 0
    libinput Left Handed Enabled (288):    0
    libinput Left Handed Enabled Default (289):    0
    libinput Scroll Methods Available (290):    1, 1, 0
    libinput Scroll Method Enabled (291):    0, 1, 0
    libinput Scroll Method Enabled Default (292):    1, 0, 0
    libinput Disable While Typing Enabled (304):    1
    libinput Disable While Typing Enabled Default (305):    1
    Device Node (268):    "/dev/input/event6"
    Device Product ID (269):    2, 7
    libinput Drag Lock Buttons (297):    <no items>
    **libinput Horizonal Scroll Enabled (270):    1**
```

That last line, which I've emboldened, would seem to be the relevant setting, right?  But toggling it on and off seems to make no discernible difference.

In the course of my Googling, I've come across a number of people suggesting solutions like "$ synclient HorizEdgeScroll=1" ... which is how I remember getting the touchpad working in previous Ubuntu incarnations.  Running synclient from the command line confirms that I'm not using the synaptics driver, but (presumably) xinput is natively handling those responsibilities:
```
$ synclient 
Couldn't find synaptics properties. No synaptics driver loaded?
```

So I find myself stuck.  Has anyone out there run into the same problem?  If nobody has a fix or workaround, I'll go ahead and file a bug report.  Just thought I should check with the forums denizens first :)

Oh, and in case it's relevant:  I'm running kernel 4.8.0-30-generic with GNOME 3.20.4.  Everything on the system is pretty close to default, as I've just installed it in the last week, and all software and libraries have been apt-get dist-upgrade'd.

---

