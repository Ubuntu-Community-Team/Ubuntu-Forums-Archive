---
title: "Tablet rotation setting?"
date: 2012-01-07
forum: Hardware
---

### Post by Jack the R on 2012-01-07
I've installed 11.10 on an Asus R1E tablet pc.

The good news is, I'm very close to having everything working.

The issue I have a question about is, when I flip the screen from normal to tablet mode, Ubuntu detects the screen flip, and rotates the screen into portrait mode.  But it doesn't rotate the wacom inputs.

When I rotate the screen back to normal, Ubuntu detects the screen flip, but - it doesn't rotate the wacom inputs.  Since it doesn't change them when rotating to tablet mode, the inputs remain correct for normal mode.  Unless I've run a script to make the wacom inputs work in portrait mode, in which case flipping the screen back to normal doesn't put the wacom inputs back to normal.

Somewhere in Ubuntu is a setting or script that detects these screen flips.  I want to know either a) where it is, so I can edit it and make the wacom inputs update correctly with the screen rotation - or b) delete it, so I can change screen modes manually via scripts I've written.  If I can't make it work right, I at least want it out of my way.

Thanks.

---

### Post by Favux on 2012-01-07
Hi Jack the R,

I'm thinking your Asus R1E is using the generic acpi rotation sript which is somewhere in /etc I think.  I'll see if I can remember where.  Likely the script hasn't been updated for the new linux wacom conventions.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

Edit:  Yep, /etc/acpi/rotatescreen.sh.  Huh, no stuff for wacom input tools in it looks like.  Easy enough to add.

---

### Post by Jack the R on 2012-01-08
Help me out with the language, apparently I'm missing a couple things.  Here's what I came up with - 

case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
	xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate none
	;;
	*)
	NEW_ROTATION="half"
	xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate half
	;;

I'm wanting the screen to flip 180 instead of 90, but "half" appears to not be the magic word NEW_ROTATION is looking for.

Now it doesn't work at all, which is my 2nd most desirable outcome, but it would be nifty if all I had to do was flip the screen.

---

### Post by Favux on 2012-01-08
Let's try this for rotatescreen.sh:
```
#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed
#
# xrandr v.s. xsetwacom rotation values:
# "normal":"none", "left":"ccw", "inverted":"half", "right":"cw"

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate none
	;;
	*)
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate cw
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate half
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
	fi
done
```

---

### Post by Jack the R on 2012-01-08
When flipping the screen to portrait mode, the new code rotated the screen 180, as desired.

Wacom input didn't flip :confused:

When rotating the screen back to landscape, it remained inverted :confused:

---

### Post by Favux on 2012-01-08
First let's check your output from:
```
xinput list
```
and make sure we're getting the correct "device name".

Also run this command in laptop, tablet, and then laptop mode again (after a reboot?):
```
cat /var/lib/acpi-support/screen-rotation
```
Let's see what's happening to the orientation.

---

### Post by Jack the R on 2012-01-08
Give me a couple days - I had to put the 8.04 hard drive in to get a little work done.  Ran into another problem - I needed to reseat the hard drive six times before the computer would stop throwing "non system disk or disk error" at me and boot.  Maybe I've swapped hard drives too often?

---

### Post by Jack the R on 2012-01-10
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Honey Bee  Nostromo SpeedPad2           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser               	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Travel Mouse                  	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Honey Bee  Nostromo SpeedPad2           	id=10	[slave  keyboard (3)]
    &#8627; LITEON Technology USB Multimedia Keyboard	id=12	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard

---

### Post by Jack the R on 2012-01-10
Laptop mode - 

jeremy@jeremy-R1E:~$ cat /var/lib/acpi-support/screen-rotation
inverted

Flipped - 

jeremy@jeremy-R1E:~$ cat /var/lib/acpi-support/screen-rotation
inverted

Back 2 laptop - 

jeremy@jeremy-R1E:~$ cat /var/lib/acpi-support/screen-rotation
inverted

---

### Post by Jack the R on 2012-01-10
After rebooting, in laptop mode - 

jeremy@jeremy-R1E:~$ cat /var/lib/acpi-support/screen-rotation
inverted


Incidentally, after boot the screen is now inverted, but the wacom input doesn't match.

---

### Post by Favux on 2012-01-10
Alright, the "device name" is right.  And stuck in inverted.

What happens if you change?:
```
case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate none
	;;
	*)
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate cw
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate half
	;;
esac

```
to
```
case "$ROTATION" in
#        right)
	inverted)
	NEW_ROTATION="normal"
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate none
	;;
	*)
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate cw
        xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate half
	;;
esac

```

---

### Post by Jack the R on 2012-01-10
Strange results, but we're progressing.

After login, the screen inverts, although the computer is in laptop mode.

I flip the screen back and forth a few times, nothing happens.

After running cat /var/lib/acpi-support/screen-rotation, the rotation script works, except the wacom input doesn't align in tablet mode.  But the rotation is detected and the screen flips correctly.  In Laptop mode, the wacom input is aligned correctly.

I looked at the line for wacom input in tablet mode - 

xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate half

It appears to be correct, and this command works in my own scripts.

---

### Post by Favux on 2012-01-10
Okay, let's try this one:
```
#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed
#
# xrandr v.s. xsetwacom rotation values:
# "normal":"none", "left":"ccw", "inverted":"half", "right":"cw"

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
#        right)
	inverted)
	NEW_ROTATION="normal"
        WACOM_ROTATION="none"
	;;
	*)
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        WACOM_ROTATION="cw"
        WACOM_ROTATION="half"
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
            xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate $WACOM_ROTATION
	fi
done
```

---

### Post by Jack the R on 2012-01-12
I've almost got good news for you.  It did work.  I cut and pasted into rotation.sh, saved, flipped the screen back and forth a few times to make super extra sure that it really really was working.  It worked great, the wacom worked like it should.  Then I rebooted, and now I've got nothing again.:confused:  After log in, with the screen in laptop mode, it immediately flips to inverted, with the wacom input not matching.  I rotate the screen around and everything is wrong wrong wrong.

:confused:

---

### Post by lomdav on 2012-05-22
There is a daemon Wacom Rotate, that rotate automatically wacom coordinates at screen rotation.
[https://launchpad.net/%7Ethjaeger/+archive/tabletpc/+packages](https://launchpad.net/%7Ethjaeger/+archive/tabletpc/+packages)

---

