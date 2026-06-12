---
title: "Wacom Bamboo Capture Finger Touch (dual monitors)"
date: 2012-12-28
forum: Hardware
---

### Post by Vinca on 2012-12-28
This is all about Finger Touch on my Wacom Bamboo Capture.  Stylus is (almost) fine.

I have two main problems

1. there is a setting where right-click is actuated by a two-finger touch, I want to disable it as it messes with two-finger scrolling.

2. The touch response is way too fast.

[SIZE="4"]1. Right Click[/SIZE]

[SIZE="3"]What I have done:
[/SIZE]xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" TapTime 80

[SIZE="3"]Results
[/SIZE]
Helps a bit.  I still want to disable it.  This also made my scrolling more responsive to two-finger "flicks" when scrolling, which is nice.  just little tiny movements instead of deliberate long movements.  Know why?

[SIZE="4"]2. Touch Response too fast[/SIZE]

[SIZE="3"]What I have done:[/SIZE]
mess with xinput. a lot.  To no avail.
```
$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen stylus        	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger touch      	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1024	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:2011	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen eraser        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger pad        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; UVC Camera (046d:081b)                  	id=8	[slave  keyboard (3)]

```
```
Wacom Bamboo 16FG 4x5 Pen stylus	id: 9	type: STYLUS    
Wacom Bamboo 16FG 4x5 Finger touch	id: 10	type: TOUCH     
Wacom Bamboo 16FG 4x5 Pen eraser	id: 13	type: ERASER    
Wacom Bamboo 16FG 4x5 Finger pad	id: 14	type: PAD  
```

I've noticed that I can write values with xsetwacom to the "Finger pad" or the "Finger touch" with the same results.  100% sure of this with TapTime parameter of xsetwacom.

xinput, however, responds to neither **"Wacom Bamboo 16FG 4x5 Finger touch"** or to **"Wacom Bamboo 16FG 4x5 Finger pad"**

With recommendation of Favux, I looked here initially with regard to my touch speed question. [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

It didn't say anything about being able to use the touchpad across both monitors.  It does work now, just too fast, across both monitors.  When i draw a circle with my finger, it comes out as an oval 2x wider than it is tall (stretched by dual monitors, it seems).  (trying live usb with one monitor plugged in: it's better, true circle, but still too fast)

The way the How To works (linked a bit above) is it has a wacom section, then a generic tablet section.  I obviously started with wacom.  ```
$ xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" MapToOutput DVI-I-2
Unable to find an output 'DVI-I-2'.

$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+   50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0     50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+   50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0     50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        59.9  

```

interestingly, the toggle switch (map to single monitor) in the beautiful Ubuntu GUI for wacom settings works.  BUT, selecting which monitor does not.  probably a result of the same error (Unable to find an output 'DVI-I-2'.) didn't work with DVI-3 btw either.

So, I decided to try Favux's Part 2 (all tablets) involving the Convolution matrix and xinput.

these matrix commands didn't involve setting a DVI-I-2 (or 3) in the command.  so I was optimistic.  Running the commands, no change.  I even tried extreme values in the matrix to purposely mess it up... didn't work :P.  obviously not responding to the commands of xinput.  same for both device names/id #s.

I then tried some other xinput commands relating to acceleration in another thread about another bamboo model.  Like the convolution matrix commands, they ran, gave no error, but had no effect.  I also tried extreme values with these.

Honestly, i wish the bamboo just showed up in stock ubuntu settings as a "touchpad" like on a laptop, and i could just mess with that acceleration slider... lol

I think that's about it. probably edits coming :P

vinca

---

### Post by Favux on 2012-12-28
The kernel usb driver wacom.ko sets up two input event nodes for the BambooPT.  Those are the parent devices and from your **xinput list** are:
> Wacom Bamboo 16FG 4x5 Pen
and
Wacom Bamboo 16FG 4x5 Finger
The X driver xf86-input-wacom then appends the daughter devices stylus and eraser to the parent Pen and touch and pad to the parent device Finger.

Pad is the linuxwacom equivalent of ExpressKeys, in other words the tablet buttons.  So ExpressKeys and touch come over the same channel or input event node.

For either xsetwacom or xinput commands you want to use the <device name> in quotes.  So for touch the <device name> would be:
> Wacom Bamboo 16FG 4x5 Finger touch
and you would use it in a xsetwacom command like so:
```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger touch" Parameter value
```
You could also use the ID number (without quotes) but that can change with hotplugging so the <device name> is the better choice.

---

### Post by Vinca on 2012-12-28
> **Favux said:**
> The kernel driver wacom.ko sets up two input event nodes for the BambooPT.  Those are the parent devices and from your **xinput list** are:

The X driver xf86-input-wacom then appends the daughter devices stylus and eraser to the parent Pen and touch and pad the the parent device Finger.

Pad is the linuxwacom equivalent of ExpressKeys, in other words the tablet buttons.  So ExpressKeys and touch come over the same channel.

For either xsetwacom or xinput commands you want to use the <device name> in quotes.  So for touch the <device name> would be:

and you would use it in a xsetwacom command like so:
```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger touch" Parameter value
```
You could also use the ID number but that can change with hotplugging so the <device name> is the better choice.

Wow, you're right!

I never realized that.  I mustve been confused by my startup scripts that set some stuff.

Unfortunately, I ran all of these commands on "touch" too so I still have the same problems.

vinca

---

### Post by Favux on 2012-12-28
Alright, so it is looking like xsetwacom is not working for some reason.  Do xsetwacom commands work for the stylus?

What is the output of the following terminal commands?
```
Xorg -version

xsetwacom -V
```

---

### Post by Vinca on 2012-12-28
> **Favux said:**
> Alright, so it is looking like xsetwacom is not working for some reason.  Do xsetwacom commands work for the stylus?

What is the output of the following terminal commands?
```
Xorg -version

xsetwacom -V
```

xsetwacom works fine except for MapToDisplay (from my testing)

Yes works for stylus, except MapToDisplay

```
$ Xorg -version

X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
Current Operating System: Linux EDITED-Mint 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=22893768-cb1d-4d85-a756-f5a68c16c0bd ro quiet splash
Build Date: 08 October 2012  03:34:01PM
xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

$ xsetwacom -V
0.17.0
```

---

### Post by Favux on 2012-12-29
Alright I have my Capture set up in Precise, although I have xf86-input-wacom-0.18.0 instead of the Quantal default 0.17.0 you have.

I'm not quite clear on how right click is messing up your scroll but as far as I know you can't disable right click unless you disable Gesture which would disable scroll.  To right click you have one finger down and then tap with the second finger?  My immortal prose on Wacom 2FGT gestures is in the Wacom manual (**man wacom** entered in a terminal).  Not sure TapTime is the way to go.  Maybe Suppress or Threshold?

Here's a list of parameters from my xsetwacom.sh script, example attached to the HOW TO.
> ## touch = ID 9 = "Wacom Bamboo 2FG 4x5 Finger touch"
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Touch on  # or off
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Gesture on  # or off
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Suppress 2  # coordinates delta cutoff; default is 2, 1-100
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" RawSample 4  # size of data sample window; default is 4, 0-20
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Threshold 27  # min. click pressure; default is 27, range 0-2047
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" Mode Relative  # or Absolute cursor movement
## 1FG dbl. tap is left click, 2FG dbl. tap (1FG down, tap second finger) is right click
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" ZoomDistance 50  # default is 50
xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" ScrollDistance 18  # default is 20
#xsetwacom set "Wacom Bamboo 2FG 4x5 Finger touch" TapTime 250  # 2FG R click, default is 250 ms
xinput set-prop "Wacom Bamboo 2FG 4x5 Finger touch" --type=float "Device Accel Constant Deceleration" 1.250000
xinput set-prop "Wacom Bamboo 2FG 4x5 Finger touch" --type=float "Device Accel Adaptive Deceleration" 1.150000
#xinput set-prop "Wacom Bamboo 2FG 4x5 Finger touch" --type=float "Device Accel Velocity Scaling" 10.000000
As you can see I only apply a couple for my BambooPT CTH460.  Scroll being one of them.  I also don't change the Acceleration algorithm, don't even have a line for it, although some recommend doing that.

Checking it looks like someone, probably Chris, changed the Scroll default because:
```
~$ xsetwacom get "Wacom Bamboo 16FG 4x5 Finger touch" ScrollDistance
80
```
So anyway applying:
```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger touch" ScrollDistance 18  # default is 20
xinput set-prop "Wacom Bamboo 16FG 4x5 Finger touch" --type=float "Device Accel Constant Deceleration" 1.250000
xinput set-prop "Wacom Bamboo 16FG 4x5 Finger touch" --type=float "Device Accel Adaptive Deceleration" 1.150000
```
Results in a very hair trigger scroll and OK touch pointer speed.  Although the defaults for all 3 don't seem too bad.  So I'd have to get used to the Capture a bit, then play around a little, before I settled on something.  I can tell the xinput acceleration stuff is working and confirmed it with:
```
~$ xinput list-props "Wacom Bamboo 16FG 4x5 Finger touch"
```
> 	Device Accel Profile (263):	0
	Device Accel Constant Deceleration (264):	1.250000
	Device Accel Adaptive Deceleration (265):	1.150000
	Device Accel Velocity Scaling (266):	10.000000


It looks like the MapToOutput code may not be able to parse the DVI-I-2 etc. outputs.  Actually I don't understand what that is all about.  It's possible it can only see DVI and not be able to distinguish the -I-0 etc. suffixes or something.

The Coordinate Transformation Matrix (CTM) should work.  Again you could check the list-props to confirm the change is made.  I'm wondering if the difficulty is the BambooPT touch is in Relative Mode rather than Absolute.  In other words you could confine touch to a single monitor if you changed Mode to Absolute.  But in that case I'd think the lateral over acceleration is not related to the two monitors.  But I'm not sure.

---

### Post by Vinca on 2013-01-01
> **Favux said:**
> Alright I have my Capture set up in Precise, although I have xf86-input-wacom-0.18.0 instead of the Quantal default 0.17.0 you have.

I'm not quite clear on how right click is messing up your scroll but as far as I know you can't disable right click unless you disable Gesture which would disable scroll.  To right click you have one finger down and then tap with the second finger?  My immortal prose on Wacom 2FGT gestures is in the Wacom manual (**man wacom** entered in a terminal).  Not sure TapTime is the way to go.  Maybe Suppress or Threshold?

Here's a list of parameters from my xsetwacom.sh script, example attached to the HOW TO.

As you can see I only apply a couple for my BambooPT CTH460.  Scroll being one of them.  I also don't change the Acceleration algorithm, don't even have a line for it, although some recommend doing that.

Checking it looks like someone, probably Chris, changed the Scroll default because:
```
~$ xsetwacom get "Wacom Bamboo 16FG 4x5 Finger touch" ScrollDistance
80
```
So anyway applying:
```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger touch" ScrollDistance 18  # default is 20
xinput set-prop "Wacom Bamboo 16FG 4x5 Finger touch" --type=float "Device Accel Constant Deceleration" 1.250000
xinput set-prop "Wacom Bamboo 16FG 4x5 Finger touch" --type=float "Device Accel Adaptive Deceleration" 1.150000
```
Results in a very hair trigger scroll and OK touch pointer speed.  Although the defaults for all 3 don't seem too bad.  So I'd have to get used to the Capture a bit, then play around a little, before I settled on something.  I can tell the xinput acceleration stuff is working and confirmed it with:
```
~$ xinput list-props "Wacom Bamboo 16FG 4x5 Finger touch"
```


It looks like the MapToOutput code may not be able to parse the DVI-I-2 etc. outputs.  Actually I don't understand what that is all about.  It's possible it can only see DVI and not be able to distinguish the -I-0 etc. suffixes or something.

The Coordinate Transformation Matrix (CTM) should work.  Again you could check the list-props to confirm the change is made.  I'm wondering if the difficulty is the BambooPT touch is in Relative Mode rather than Absolute.  In other words you could confine touch to a single monitor if you changed Mode to Absolute.  But in that case I'd think the lateral over acceleration is not related to the two monitors.  But I'm not sure.

```
Device Accel Constant Deceleration (263):	3.000000
	Device Accel Adaptive Deceleration (264):	2.150000
	Device Accel Velocity Scaling (265):	15.000000

```

this is beautiful.  velocity scaling makes no big difference, however.  I swear I tried all this.  Maybe I ran those commands with "pad" instead of "touch"

i could check ```
history
```

ScrollDistance is always 80 for me.  extremely smooth with "chromium wheel smooth scroller" plugin for chrome :P

do these stick on reboot? xinput

I guess I could just test that myself...

---

### Post by Favux on 2013-01-01
> do these stick on reboot? xinput
Nope, xsetwacom and xinput commands are runtime commands.  To have them after a reboot they'll need to be in a script that you have autostarting.

---

### Post by Vinca on 2013-01-01
> **Favux said:**
> Nope, xsetwacom and xinput commands are runtime commands.  To have them after a reboot they'll need to be in a script that you have autostarting.

OK.

The only thing left is the right click.  Threshold and Suppress don't seem to change much... as usual, I tried extreme values (2046, 2047 for threshold and 99, 100 for Suppress)

I'm pretty happy with my current setup, though! the acceleration at the right values makes it really fun to use.

---

