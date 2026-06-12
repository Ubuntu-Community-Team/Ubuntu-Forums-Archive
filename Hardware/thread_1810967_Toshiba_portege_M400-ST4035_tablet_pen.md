---
title: "Toshiba portege M400-ST4035 tablet pen"
date: 2011-07-24
forum: Hardware
---

### Post by Monkey1911 on 2011-07-24
Hello all,

I'm running 10.04.3 LTS on my Portege M400-ST4035
Specs are: 
Core 2 Duo T5500 1.66Ghz
4Gb of Ram
Intel 945 IMA graphics


Thanks for just checking around here in this sub-forum I learned how to rotate my screen and then figured out how to place buttons on my menu panel at the top of the screen. (Thanks Favux)

Pretty much everything worked out of the box except for the side button on the pen and the fingerprint reader. I loaded libthinkfinger thru package manager, but I can't figure out how that works or find anything related to it in any of the menus. 

All the directions I've found on google for making the pen button work are from 2008 for 08.04 and say to load wacom-tools, but I can't find that in package manager. So I'm at a bit of a loss on how to proceed.

Thanks for any help.
Monkey1911

---

### Post by Favux on 2011-07-24
Hi Monkey1911,

The xsetwacom that was in wacom-tools is now part of xf86-input-wacom so it is automatically included in Ubuntu's xserver-xorg-input-wacom package.  The default in Lucid is xf86-input-wacom-0.10.5.

So determine your stylus "device name" in the output of *xinput list* in a terminal.  Then enter in a terminal the following *xsetwacom set* commands:
```
xsetwacom set "device name" Button 2 "3"
xsetwacom set "device name" Button 3 "2"
```
assuming there are two side buttons.  If only one skip the second Button 3 command.

---

### Post by Monkey1911 on 2011-07-24
Just gave that a shot, here's the output from both commands.

```
monkey1911@timothy-tablet:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
monkey1911@timothy-tablet:~$ xsetwacom set "Serial Wacom Tablet" Button 2 "3"
Unknown parameter name 'Button'.
monkey1911@timothy-tablet:~$ 

```

Also, I was a little quick to say everything is working out of the box earlier. Once I found out how to rotate the screen, I started to play around with that. When I click on my rotate left link in my top bar, the screen will rotate but the input will not. In order to tap my rotate normal button I have to tap the pen in the location that corresponds with the "normal" location of the button, not of the actual screen location of the button.

---

### Post by Favux on 2011-07-24
Sorry my mistake, I used the new parameter name.  You're using Lucid correct?
```
xsetwacom set "Serial Wacom Tablet" Button2 "3"

```
There's no space between Button and 2 with the old parameter name.

Sounds like your rotation script isn't quite working.  What does it look like?

---

### Post by Monkey1911 on 2011-07-24
Cool, got the right click working now.

All I'm using to rotate the screen is this.
```
xrandr -o left
xrandr -o normal
```

If I need to add anything else, just give a shout.
I added the buttons to the top panel by right clicking and going to "Add to Panel" from there I went to "Custom Application Launcher" And in the type drop down selected "Application in Terminal" One button for left and one button for normal.

---

### Post by Favux on 2011-07-24
> Cool, got the right click working now.

Good.  :)

Alright, you need to rotate the stylus too.  Does the stylus have an eraser?

---

### Post by Monkey1911 on 2011-07-24
Yes it does have an eraser and right now it just acts the same as the pointed end of the stylus.

---

### Post by Favux on 2011-07-24
OK, what you want to use is the following script:
```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set "Serial Wacom Tablet" rotate ccw
    xsetwacom set "Serial Wacom Tablet eraser" rotate ccw
    ;;
    left)
    # rotate to normal
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" rotate none
    xsetwacom set "Serial Wacom Tablet eraser" rotate none
    ;;
esac
```
Copy and paste it in a new text file in Text Editor (gedit) and save it as say rotate.sh.  Then right click on the new file and chose Properties.  Then in the Permissions tab check the box in front of *Allow executing as a program*.  That makes the text file executable.  Then right click on your Desktop and create a launcher.  Then in the command box put the path to the new .sh file, say /home/yourusername/Desktop/rotate.sh.  Then double clicking on the launcher will run it or dragging the launcher into the top panel will make it work with one click.

By the way I'm getting this from the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

### Post by Monkey1911 on 2011-07-24
Ok, got the script set up and working, but the input still isn't switching properly. I read your post in the other thread and couldn't find anything more about the input switch that you didn't post here already.

---

### Post by Monkey1911 on 2011-07-24
> **Monkey1911 said:**
> Ok, got the script set up and working, but the input still isn't switching properly. I read your post in the other thread and couldn't find anything more about the input switch that you didn't post here already.


I'm herp derp......Got it working!!!!

```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set "Serial Wacom Tablet" rotate ccw
    xsetwacom set "Serial Wacom Tablet Eraser" rotate ccw
    ;;
    left)
    # rotate to normal
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" rotate none
    xsetwacom set "Serial Wacom Tablet Eraser" rotate none
    ;;
esac
```

---

### Post by Monkey1911 on 2011-07-24
Thanks for the help Favux, and thanks for making me figure out why copy/pasting the script wasn't swapping the input since the answer was right in front of my face from something I had done earlier!

Monkey1911

---

### Post by Favux on 2011-07-24
Great!

The HOW TO also tells you how to set up stuff so it autostarts when you reboot.

Part IV of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") also tells you how to do that with a xsetwacom script.

---

