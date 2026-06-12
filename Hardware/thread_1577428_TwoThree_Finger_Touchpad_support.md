---
title: "Two/Three Finger Touchpad support"
date: 2010-09-18
forum: Hardware
---

### Post by Cyclops_ on 2010-09-18
Hi all!

I just bought a new ASUS laptop.  It has hardware support for multi-finger on the touchpad.  I know it works because it worked in Windows before I installed the enlightened OS of Ubuntu... :)

Anyway,  I changed the settings in the settings windows... but it doesn't seem to do anything.  I should be able to scroll with two fingers, right click by tapping two fingers and middle click by tapping three fingers.  No go.

I have run synclient -m100  and watched it as I did various things.  The 'f' column always reports 1 or 0, though the W column reports low to high numbers based on how much of my hand I use to tap/touch the pad with.

Any help with this would be great!

Thanks!

---

### Post by Zorael on 2010-09-20
First of all, ensure that your pad is using the synaptics driver. Perhaps it's an unsupported device, in which case an updated driver might help.
```
$ grep -i touchpad /var/log/Xorg.0.log
# should spam some lines about SynPS/2 Synaptics TouchPad
```

If so (and perhaps even if not), you could manually try the xinput tool.
```
$ xinput list-props "SynPS/2 Synaptics TouchPad"
```
Refer to the output of '**xinput list**' if it seems your device has a different name.

This is the listed properties available to me on lucid with my Synaptics pad;
```
Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (134):   1
        Device Accel Profile (252):     0
        Device Accel Constant Deceleration (253):       1.000000
        Device Accel Adaptive Deceleration (255):       1.000000
        Device Accel Velocity Scaling (256):    10.000000
        Synaptics Edges (257):  1752, 5192, 1620, 4236
        Synaptics Finger (258): 24, 29, 255
        Synaptics Tap Time (259):       180
        Synaptics Tap Move (260):       221
        Synaptics Tap Durations (261):  180, 180, 100
        Synaptics Tap FastTap (262):    0
        Synaptics Middle Button Timeout (263):  75
        Synaptics Two-Finger Pressure (264):    280
        Synaptics Two-Finger Width (265):       7
        Synaptics Scrolling Distance (266):     100, 100
        Synaptics Edge Scrolling (267): 1, 1, 0
        **Synaptics Two-Finger Scrolling (268):   0, 0**
        Synaptics Move Speed (269):     0.400000, 0.700000, 0.009952, 40.000000
        Synaptics Edge Motion Pressure (270):   29, 159
        Synaptics Edge Motion Speed (271):      400, 800
        Synaptics Edge Motion Always (272):     0
        Synaptics Button Scrolling (273):       1, 1
        Synaptics Button Scrolling Repeat (274):        1, 1
        Synaptics Button Scrolling Time (275):  100
        Synaptics Off (276):    0
        Synaptics Guestmouse Off (277): 0
        Synaptics Locked Drags (278):   0
        Synaptics Locked Drags Timeout (279):   5000
        Synaptics Tap Action (280):     0, 0, 0, 0, 1, 1, 1
        Synaptics Click Action (281):   1, 1, 2
        Synaptics Circular Scrolling (282):     0
        Synaptics Circular Scrolling Distance (283):    0.100000
        Synaptics Circular Scrolling Trigger (284):     0
        Synaptics Circular Pad (285):   0
        Synaptics Palm Detection (286): 1
        Synaptics Palm Dimensions (287):        10, 199
        Synaptics Coasting Speed (288): 40.000000
        Synaptics Pressure Motion (289):        29, 159
        Synaptics Pressure Motion Factor (290): 1.000000, 1.000000
        Synaptics Grab Event Device (291):      1
        Synaptics Gestures (292):       1
        Synaptics Capabilities (293):   1, 0, 1, 1, 1
        Synaptics Pad Resolution (294): 110, 100
        Synaptics Area (295):   0, 0, 0, 0
        Synaptics Jumpy Cursor Threshold (296): 0
```
```
# syntax: **xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]**
# arguments inbetween [] are optional

$ **xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1**
# I believe the first number is for enabling vertical scrolling, and the second for horizontal. 0 disables

$ **xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Click Action" 1 3 2**
# First number is for one finger clicks, second for two, third for three. 1 means left click, 2 middle click, 3 right click
```
Refer to the list of '**xinput list-props "SynPS/2 Synaptics TouchPad"**' for what properties are available to your device. There are some other gems in there too, like Coasting, Edge Motion and Palm Detection. You can gleam some insight into what options do by checking the man page for **synaptics**, although the options there are listed as they would be entered in xorg.conf. So it's not immediately obvious how to express them in xinput properties.

Properties and devices can be referred to by their id numbers, but those may change upon adding new devices and upgrading drivers, so I'd recommend you just use the device and property names right away (in double quotes).

Once you get a setup you like, create a script that runs them all upon login, such as in **~/.kde/Autostart/**. Don't forget to set it as executable though, with '**chmod +x *<filename>***'.

---

### Post by Cyclops_ on 2010-09-20
Zorael,

This info is great.  Thank you!  Palm detection works great.

I think I found a problem with one of my properties:

```

Synaptics Capabilities (278):   1, 1, 1, 0, 0

```

Something is *reporting* that I don't have two- and three-finger support!  But the pad *does*!

Are there any special drivers out there I could use?  Where would I go to find them?

Many thanks for the help!

---

### Post by Zorael on 2010-09-20
You could try a live cd of Maverick Meerkat and see if the updated Synaptics driver there has better support for your pad. If so, at least you know there's an update available, though getting it backported onto your Lucid system might take some work. At least October is coming up, so Maverick isn't that far away.

The upstream bugtracker for the synaptics driver is [here](https://bugs.freedesktop.org/buglist.cgi?query_format=advanced&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&component=Input/synaptics&product=xorg) (product: xorg, component: Input/synaptics). If nothing else, you could file a bug about missing multi-touch support there. Mention that the synaptics driver reports it doesn't, and that it works in Windows.

Perhaps it's just a matter of adding the device id of your pad to some list - or perhaps it's a matter of low-level debugging the signals the pad sends. :<

---

### Post by Cyclops_ on 2010-09-20
Ooh.. fun... Meerkat.  I'll give it a try and let you know.  Thanks again for the help, Z.  :)

---

### Post by Cyclops_ on 2010-09-27
Hum, apparently meerkat isn't usable on this compy..

---

### Post by fakhri on 2010-11-05
Hi, I was having the same problem. Bu now I found out that the function just swapped.
Two-finger tap for right-click, three for middle-click.

---

