---
title: "gpointing-device-settings loses settings on reboot"
date: 2012-03-14
forum: Hardware
---

### Post by ridgeland on 2012-03-14
Ubuntu 10.10 was the last release where gpointing-device-settings remembers my settings on reboot.  Actually gpointing-device-settings still remembers my settings exactly, just gnome3/unity ignores them. For me this was a show-stopper so I have stayed with 10.10 hoping that by 12.04 this would be fixed.  In 12.04 beta1 there is a new version of gpointing-device-settings and it's still broken.  But now I have a work-around.  This should show you how to build your work-around.

[https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830)
Post number 57 Alex Burfee (joop-wow) showed me what I needed to know to fix this.

First step &#8211; Find xinput's name of your device
```

# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)] 
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] 
&#9116;   &#8627; Kensington      Kensington USB/PS2 Orbit	id=8	[slave  pointer  (2)]

```
The device I'm setting up with gpointing is the Kensington Orbit.  It's a trackball with just two buttons.  I use gpointing to emulate a scroll feature.  While holding down the right button the track ball scrolls the window rather than moving the pointer.  There are a lot of spaces in the name between the two words Kensington so I copy and paste to get them all and use &#8220;&#8221; around the name.

Second step &#8211; see the &#8220;good&#8221; settings before reboot looses them
```

# xinput list-props "Kensington      Kensington USB/PS2 Orbit" 

```
two lines in this matter to me:
```

	Evdev Wheel Emulation (256):	1 
	Evdev Wheel Emulation Button (260):	3

```
When the reboot ignores my settings these become 0 and 4.  So read &#8220;xinput list-props&#8221; both while your device is working and while it is not and compare the two.  If you cannot recover from the bad setting then boot an old partition that still has Ubuntu 10.10.  Huh?  You don't keep multiple partitions just for this!  Since I do I just assumed everyone does.  I still use 9.04 for k3b when 10.10 fails to reuse a CD or DVD.  OK boot the installation disk, install gpointing device, run gpointing-device-setting in the terminal, get the device set just like you want it and print the xinput list-props for your device.

Third Step &#8211; write a simple script to reset xinput to the settings that gpointing cannot convince the reboot to use.  Be sure to set the script's properties to make it executable.  Here is mine:
```

#!/bin/bash
xinput set-prop --type=int --format=8  "Kensington      Kensington USB/PS2 Orbit" "Evdev Wheel Emulation" 1
xinput set-prop --type=int --format=8  "Kensington      Kensington USB/PS2 Orbit" "Evdev Wheel Emulation Button" 3
xinput set-prop --type=int --format=16 "Kensington      Kensington USB/PS2 Orbit" "Evdev Wheel Emulation Timeout" 600

```
Verify your script works after reboot.

Fourth Step &#8211; make this run each time I login.
Dash Home &#8211; Search &#8211; Startup Applications click [Add] click [Browse] and add your script.  Give it a meaningful name.  I called mine &#8220;Gpointing settings restored&#8221;.

A personal note of why this was a show stopper for me.  The mouse was causing wrist pains every day.  I switched to a track ball and the pain ended.  But I needed gpointing-device-settings to have the scroll feature.  I was not willing to give up the scroll feature to upgrade the OS.

---

### Post by kurt18947 on 2012-03-15
If nice scrolling is important to you (it is to me even though I don't have wrist issues) you ought to take a look at the Kensington track balls with scroll rings. Superior to every other scrolling solution out there IMO though I don't find myself doing much horizontal scrolling.

[http://peripherals.about.com/od/pckeyboardsmice/fr/KensingtonTrackballScrollReview.htm](http://peripherals.about.com/od/pckeyboardsmice/fr/KensingtonTrackballScrollReview.htm)

The wrist rest that comes with this is about useless.  I made my own from a piece of wood.  The front of the trackball is about 1/4" (6 mm) off the desk. The back where my palm rests is about 3/4" (18 mm) off the desk.  My chair arm rest is such that when my elbow is resting on the arm rest and the heel of my hand is resting on my home-made trackball holder, my wrist is very nearly straight.  Really very comfortable.

---

### Post by dlinares on 2012-04-04
Thanks for the help ridgeland!! I'll try to see if I can find the  fundamental cause of xinput/gpointing loosing its settings after reboot.

---

### Post by r1chard on 2012-06-16
Thanks useful thread. In my case I was failing to emulate a 3rd mouse button using an Xorg.conf file, and I was keen to avoid using gnome specific settings, so I added 

> xinput --set-prop --type=int --format=8 "Primax Kensington Eagle Trackball" "Evdev Middle Button Emulation" "1"

To my /etc/profile

Cheers
Richard

---

