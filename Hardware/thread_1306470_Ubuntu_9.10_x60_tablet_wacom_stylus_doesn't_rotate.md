---
title: "Ubuntu 9.10 x60 tablet wacom stylus doesn't rotate"
date: 2009-10-30
forum: Hardware
---

### Post by shanest on 2009-10-30
I've upgraded my Lenovo x60 tablet to 9.10 after everything was working flawlessly in 9.04.

The upgrade has been very smooth except for one detail:
my stylus doesn't rotate when I rotate the screen into tablet orientation

The display automatically rotates both when I put the screen down and up.  The stylus, however, never recalibrates.

In 9.04, I handled this with a wacom-calibrate.sh script in /etc/acpi/resume.d which contained:

```

#!/bin/bash
#
# waCalibrate.sh: recalibrates the wacom stylus
#
# Author: Rogan Creswick
# License: just be nice

# Set LOG to something reasonable:
# (The file does not need to exist, but the *directory* does)
LOG=/home/rogue/calibration.out
XSETWACOM=/usr/local/bin/xsetwacom


#
# Calibrates the wacom devices {stylus, eraser, cursor} with the
# given offsets:
#
#  Usage:
#     calibrate <topx> <topy> <bottomx> <bottomy>
#
function calibrate {
    ${XSETWACOM} --display :0.0 set stylus TopX $1 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set stylus TopY $2 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set stylus BottomX $3 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set stylus BottomY $4 >> ${LOG} 2>&1

    ${XSETWACOM} --display :0.0 set eraser TopX $1 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set eraser TopY $2 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set eraser BottomX $3 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set eraser BottomY $4 >> ${LOG} 2>&1

    ${XSETWACOM} --display :0.0 set cursor TopX $1 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set cursor TopY $2 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set cursor BottomX $3 >> ${LOG} 2>&1
    ${XSETWACOM} --display :0.0 set cursor BottomY $4 >> ${LOG} 2>&1
}


function fixCalibration {
    # get the current orientation:
    ORIENTATION=`xrandr --verbose --query | grep " connected" | awk '{print $5}'`
    echo "Orientation: ${ORIENTATION}" >> ${LOG}
   
    case "${ORIENTATION}" in
    normal)
        calibrate -3 -173 24518 18478   
        ;;
    left)
        calibrate -46 -3 18605 24518
        ;;
    right)
        calibrate -173 58 18478 24579
        ;;
    inverted)
        calibrate 58 -46 24579 18605
        ;;
    *)
        calibrate -3 -173 24518 18478
        echo "ERROR!! unknown orientation! ${ORIENTATION}" >> ${LOG}
        ;;
    esac
}

case "$1" in
    resume|thaw)
    date >> ${LOG}
    fixCalibration
    whoami >> ${LOG}
        ;;
    *)
    echo "not a resum|thaw event: $1" >> ${LOG}
        ;;
esac

```

I tried manually running ```
xsetwacom set stylus Rotate cw
``` before rotating and was told stylus could not be found as a device.

Running ```
xsetwacom list
``` shows no devices.

Where is the stylus set up and how can I configure it to automatically rotate?

Note, all of the xorg.conf settings for wacom are commented out; I think they should stay this way since everything else seems to be working ok...

---

### Post by Favux on 2009-10-30
Hi shanest,

The xsetwacom rotation commands won't work until xsetwacom list is returning stylus and eraser.  To see what HAL/dBus is calling them enter in a terminal:
```
xinput --list
```
Then there's a couple ways to go.

---

### Post by shanest on 2009-10-30
```

: xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"	id=3	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"ThinkPad Extra Buttons"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"TPPS/2 IBM TrackPoint"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

So it looks like the type is "Wacom Stylus"

How do I proceed from here?

---

### Post by Favux on 2009-10-30
Hi shanest,

Right.  So HAL is calling:

stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"

eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

You can try renaming everything.  Or a couple folks reported just putting quotes around them, like "stylus" and "eraser" in the xsetwacom lines worked.

Or you can try rec's script, which will rename everything from HAL before X starts.  He had an X200.  I know they started going to Upstart in Karmic but I think the script still works.

See 3) and 3a) in "Jaunty (9.04) & Karmic (9.10) Users" near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  There's a link to rec's script but here it is directly in this [post]("http://ubuntuforums.org/showpost.php?p=7068115&postcount=93").

Hopefully one of those will work for you.

---

### Post by shanest on 2009-10-30
Favux,

Putting "stylus" in quotes did not work.

Rec's script, however, worked like a charm.  I followed your advice in post 93 of the thread as linked above and it works perfectly now.

One thing: do I still need my wacom-calibrate.sh script from the first post to actually call the xsetwacom on the now properly-named devices or does this renaming also enable automatic reorientation of the stylus?

---

### Post by Favux on 2009-10-30
Hi shanest,

Great!  Good to hear rec's script still works in Karmic.  I had suspected it did, given the number of downloads since the beta came out.

You need a rotation script, not necessarily the one you posted.  All the scripts/methods require xsetwacom lines to reorient the Wacom devices.  A couple methods are on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 or 3 should work for you.  The script you posted recalibrates with rotation.  Most tablet pc's don't need to do that.

---

### Post by Andcor on 2009-11-02
I've also tried using Rec's script on ubuntu 9.10. However this only gives me the erasor in the xsetwacom list dev. I've tried running the commands in Rec's script individually, and it seems that hal finds both the stylus and the erasor, but only the erasor is found by xsetwacom.

---

### Post by Favux on 2009-11-02
Hi Andcor,

That's happening (missing or sluggish stylus) to several serial tablet pc's in 9.10.  It seems to be on 64-bit 9.10.  Is that what you're using?  32-bit apparently works.

I talk to X-Kent about that and link him to several threads and bug reports in [post #6 here]("http://ubuntuforums.org/showpost.php?p=8216245&postcount=6").

---

### Post by shanest on 2009-11-03
> **Favux said:**
> Hi shanest,
You need a rotation script, not necessarily the one you posted.  All the scripts/methods require xsetwacom lines to reorient the Wacom devices.  A couple methods are on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 or 3 should work for you.  The script you posted recalibrates with rotation.  Most tablet pc's don't need to do that.

Neither of those methods work for me...

Now, when I rotate, the screen automatically adjusts to the proper (right-handed) orientation, but my stylus still maintains its position absolutely to the screen. For example, when I move it "up" when screen rotated, the mouse moves to the right because it's the right side of the screen.

Any ideas?

Thanks again for all the help.

---

### Post by Favux on 2009-11-03
Hi shanest,

Hmmm.  What's the output of:
```
xsetwacom list
```
in a terminal?

---

### Post by shanest on 2009-11-03
It's back to not listing any devices. My wacom-names files still exists, so I tried re-running `sudo update-rc.d wacom-names defaults 27`, which output

```

update-rc.d: warning: /etc/init.d/wacom-names missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/wacom-names already exist.

```

---

### Post by Favux on 2009-11-03
Hi shanest,

That's what I thought.  Check to see if the script is in place and correct and is executable.  If not remove the script like the post says reboot and start over.

---

### Post by nutsy.ben on 2009-11-04
> **shanest said:**
> I've upgraded my Lenovo x60 tablet to 9.10 after everything was working flawlessly in 9.04.

...

[/code]I tried manually running ```
xsetwacom set stylus Rotate cw
``` before rotating and was told stylus could not be found as a device.

Running ```
xsetwacom list
``` shows no devices.




Hi Guys ... 
I got the same problem, the stylus was not rotating while my screen was. 
As above I noticed that the name changed a little .... 

I tried only one thing, and have to admit that it was a lucky shot!

```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate cw 
```

And it worked out  !! :D

to come back to the normal configuration just type:


```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate none 
```

In fact the trick was to put the NEW name in brackets ... 
It sounds so easy that you probably tried already, meaning that it just works for me. BUT ... give it a try. Obviously it will work also with the eraser input.

Cheers

Nutsy

---

### Post by Mark Stosberg on 2009-11-21
I used a variation of this tip to solve the problem of the stylus not rotating using Karmic on on a ThinkPad X41 Tablet.

I modified the /usr/local/bin/rotatetablet script that I found elsewhere. 

I replaced this line:

     xsetwacom set stylus Rotate $T & \

With this line:

    xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate $T & \
    

Then, I don't think "/etc/init.d/wacom-names" is needed anymore, so I deleted it, and also the related the files:

sudo find /etc/rc* -name '*wacom-names' -exec  rm {} \;

---

### Post by nutsy.ben on 2010-05-04
> **Mark Stosberg said:**
> I used a variation of this tip to solve the problem of the stylus not rotating using Karmic on on a ThinkPad X41 Tablet.

I modified the /usr/local/bin/rotatetablet script that I found elsewhere. 

I replaced this line:

     xsetwacom set stylus Rotate $T & \

With this line:

    xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate $T & \
    

Then, I don't think "/etc/init.d/wacom-names" is needed anymore, so I deleted it, and also the related the files:

sudo find /etc/rc* -name '*wacom-names' -exec  rm {} \;

Could you post the full script ?

---

### Post by Islington on 2010-05-13
> **nutsy.ben said:**
> Could you post the full script ?

I too would really appreciate it since I have an x41t.

---

### Post by stefcep on 2010-09-12
> **nutsy.ben said:**
> Hi Guys ... 
I got the same problem, the stylus was not rotating while my screen was. 
As above I noticed that the name changed a little .... 

I tried only one thing, and have to admit that it was a lucky shot!

```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate cw 
```

And it worked out  !! :D

to come back to the normal configuration just type:


```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate none 
```

In fact the trick was to put the NEW name in brackets ... 
It sounds so easy that you probably tried already, meaning that it just works for me. BUT ... give it a try. Obviously it will work also with the eraser input.

Cheers

Nutsy

On a Toshiba Portege M400 Ubuntu 9.10:

 ```
sudo apt-get install wacom-tools
```

and then for portrait mode

```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate cw 
```

then

 system->preferences->display->rotate right

then

select "keep configuration", close dialog box.




To have touchscreen work in landscape again

system->preferences->display->rotate normal

select "keep configuration", close dialog box.

then 

```
 xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Rotate none 
```

---

