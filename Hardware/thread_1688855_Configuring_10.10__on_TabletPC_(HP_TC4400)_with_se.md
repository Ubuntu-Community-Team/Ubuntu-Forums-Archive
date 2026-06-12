---
title: "Configuring 10.10  on TabletPC (HP TC4400) with second monitor"
date: 2011-02-15
forum: Hardware
---

### Post by crazy ivan on 2011-02-15
After reading 
[a good installation instruction]("http://www.uluga.ubuntuforums.org/showthread.php?t=1483623") by ragtag, I  was encouraged to purchase that model from a [second hand shop]("http://www.nbwn.de/products/debeka-mitarbeiterverkauf/hp-notebooks-zubehoer/hp-tc4400-notebook-set1.html"). Quite some time had to be spent to tweak it, but I do not regret this venture since the minor problems listed at the end of this tutorial are neglegible to the boost in work flow and fun (mobility, annotations in PDFs, pressure sensitive drawing, etc).

Let me first state that the the above mentioned tutorial works just as well for ubuntu 10.10. The pen works out of the box, like everything else. It naturally takes some time to configure easystroke and train cellwriter but Ubuntu IS a fully functional Tablet OS. 

Now for the particular setup:
I want to use the tablet at work as my main PC (outsorcing compilation/computation to work stations), that means using a docking station with attached power supply, a widescreen TFT, LAN, mouse and keyboard. I want to use Tablet mode for reading papers and two screens for coding. Only there were some hurdles in the way:

1) The graphic card does not support accelaration for more than 2048px wide displays (found out thanks to 'compiz-check') > Solution:
switch off **compositing** when working on two screens.
> 1a) Compiz Desktop-cube breaks down to one workspace when compositing is switched off > change to desktop wall

2) Title bar takes valuable space when using small screen > use **maximus** and windowPicker applet
> 2a) maximus undecoration of windows does not work on second screen > switch off maximus when working with two screens
> 2a1) when killed, maximus leaves windows in ugly state and some in a sticky fullscreen mode (thunderbird, openoffice) > find special gconf entries [http://ubuntuforums.org/showpost.php?p=10461811&postcount=6](http://ubuntuforums.org/showpost.php?p=10461811&postcount=6)

3) **Screen resolution** is not automatically set correctly > find [xrandr]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things") commands to do the trick.

4) Performing the rotations has to be done when screens are already configured > integrate rotation with screen setting

5) **Menu** takes useful space but switiching completely to netbook remix suffers from above problems > set Menu to shortcut (Alt+F1) and easystroke gesture.

6) **ssh** (and worse [sshfs]("https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/388419")) breaks down when LAN is detached > kill ssh on Tablet mode.

7) cellwriter not working with advanced compiz settings > take 'dekstop effects > normal' standard.

The above considerations led to the following scripts:

```
!/bin/bash
# TABLET.sh - enable tablet mode

# close all ssh connections, especially hanging sshfs, since pipe gets broken during switching from LAN to WLAN
pkill -x ssh

# set up screen and pen rotation
xrandr --output LVDS1 --mode 1024x768 --pos 0x0 --output VGA1  --off
xrandr -o right
xsetwacom set "Serial Wacom Tablet" Rotate CW
xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
xinput set-prop "Serial Wacom Tablet eraser" --type=float "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1

# enable desktop effects
compiz 2>/dev/null &
gconftool-2 --set /apps/maximus/undecorate --type BOOL true
```

```

#!/bin/bash
# DUAL.sh - enable dual screen mode

# disable desktop effects
gconftool-2 --set /apps/maximus/undecorate --type BOOL false
gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false
metacity --replace &

# set up screen and pen rotation
xrandr -o normal
xsetwacom set "Serial Wacom Tablet" Rotate NONE  
xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
xrandr --output LVDS1 --mode 1024x768 --pos 0x282 --output VGA1  --mode 1680x1050 --pos 1024x0

# pen scaling: 0.378698224852071=1024./(1024.+1680.); 0.73142857142857143=768./1050.; 0.26857142857142857=(1050.-768.)/1050.
xinput set-prop "Serial Wacom Tablet eraser" --type=float "Coordinate Transformation Matrix" 0.378698224852071 0 0 0 0.73142857142857143 0.26857142857142857 0 0 1
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" 0.378698224852071 0 0 0 0.73142857142857143 0.26857142857142857 0 0 1

```

```
#!/bin/sh
# RIGHT_rotation.sh - turn the screen in clockwise direction
rotation=`xrandr -q | grep "LVDS1" | awk '{print $4}'`
if [ "$rotation" = "(normal" ]; then
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet" Rotate CW
    xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
else
    if [ "$rotation" = "right" ]; then
	xrandr -o inverted
	xsetwacom set "Serial Wacom Tablet" Rotate HALF  
	xsetwacom set "Serial Wacom Tablet eraser" Rotate HALF
    else
        if [ "$rotation" = "inverted" ]; then
	    xrandr -o left
	    xsetwacom set "Serial Wacom Tablet" Rotate CCW  
	    xsetwacom set "Serial Wacom Tablet eraser" Rotate CCW
        else
            if [ "$rotation" = "left" ]; then
      	        xrandr -o normal
	        xsetwacom set "Serial Wacom Tablet" Rotate NONE  
	        xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
            fi
        fi
    fi
fi
```

With the scripts 'MEDIA' (single large screen with compositing) and 'LEFT_rotation' written in a similar fashion and all bound to short-cuts and gestures.

Finally some rather useful easystroke gestures:
**commands:** cellwriter, rotations,
**Keys:** escape, enter, Ctrl+c/v/z/a, ctrl+alt+v (my binding for parcellite), alt+f1 (menu), alt+f2 (run), super+a (Very useful: compiz scale),  
**text:** common phrases
**scroll:** makes up for the non-functioning scroll buttons

Hope, this helps some and maybe you have some ideas to get rid of these remaining (really minor) invconviniences:

1) cellwriter does not copy to clipboard > hard to use gnome-do
2) somehow 'xrandr --auto' is performed everytime you connect or disconnect a screen, this means one has to run the scripts before connecting the displays, and sometimes afterwards in addition, this should be somehow disabled (for certain screen id's)
3) keys at side give no xev 
4) In Dual screen mode the pen is not usable, since it scales the position to the entire display [SOLVED]
5) connecting back to docking-station, just to type a message is too troublesome, any experiences with bluetooth keyboards and this PC?
6) tools like mypaint and xournal loose the xy position when screens are rotated

---

### Post by Favux on 2011-02-16
Hi crazy ivan,

For 4) try the MaptoOutput xsetwacom parameter.  Described in [HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty]("http://ubuntuforums.org/showthread.php?t=1656089").

---

### Post by crazy ivan on 2011-02-19
Thank you, Favux.
works quite well for the scripts.

---

