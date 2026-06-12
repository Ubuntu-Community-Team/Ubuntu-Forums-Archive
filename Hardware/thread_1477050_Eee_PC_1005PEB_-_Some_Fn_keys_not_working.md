---
title: "Eee PC 1005PEB - Some Fn keys not working"
date: 2010-05-08
forum: Hardware
---

### Post by rickwood on 2010-05-08
I'm running 10.04 on an Eee PC 1005PEB, and it works pretty well out of the box. I did have to add the acpi_osi=Linux to grub, and this fixed issues with brightness and allowed several of my Fn keys to work properly. However, a few of them don't work. So, I've written a few scripts (modified from other very helpful posts on these forums) and added some commands to my keyboard shortcuts to work around this. Here they are:

Fn-F9 to bring up the system monitor:

```
gnome-system-monitor
```

F7 to turn off the backlight:

```
xset dpms force off
```

F3 to toggle the touchpad on or off and enable 2-finger scrolling:

```
sh /home/rick/Scripts/touchpad-on-off.sh
```

The associated script looks like this:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 0
then 
#	sleep 2 #added delay...
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7         # 	Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   # 	vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # 	vertical, horizontal, corner - values: 0=disable  1=enable
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # 	stabilize 2 finger actions - value=pad-pixels
else
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0	
fi
exit
```

F4 to toggle the resolution:

```
sh /home/rick/Scripts/change-res.sh
```

The associated script looks like this:

```
#!/bin/bash
#
if xrandr --prop | grep "LVDS1 connected" | grep 1024x600
then
	xrandr -s 1
else
	if xrandr --prop | grep "LVDS1 connected" | grep 800x600
	then
	xrandr -s 2
	else
		if xrandr --prop | grep "LVDS1 connected" | grep 640x480
		then
		xrandr -s 0
		else
		xrandr -s 0
		fi
	fi
fi
exit
```

Along with the touchpad script above, I'm also using a similar script at startup to enable 2-finger scrolling:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay... 
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
exit
```

This works well, but when the computer sleeps I still have hit F3 twice to turn off and on the touchpad to get 2-finger scrolling back. No biggie.

OK, back to my original reason for posting. I would really like to assign the keyboard shortcuts for F3, F4, and F7 to Fn-F3, Fn-F4, and Fn-F7 instead. But pressing these key combinations doesn't seem to do anything. It's as if xorg doesn't recognize that these are valid key combinations. Does anyone know the best (and easiest) way to make xorg aware of these key combinations so that I can assign keyboard shortcuts to them?

---

### Post by hoover67 on 2010-06-08
*bump* I'm having similar issues on an eee pc 1005p, would be great to get the missing keys to work. 

TIA Uwe

---

### Post by abramovich on 2010-06-13
Hello rickwood, 
I have just stubled on this forum. I have an eee PC 1005P for less than a week and I am new to it and Ubuntu (I use Gentoo on my desktop).

I had the same problem as you and I seem to have found a solution.

To hook to Fn-F9 first I added  the following file named "asus-sys-mon" to /etc/acpi/events
```

event=hotkey (ATKD|HOTK) 00000012
action=/etc/acpi/asus-sys-mon.sh
```I have found the 00000012 key by running acpi_listen while pressing Fn-F9.
That successfully run the action script when the Fn-F9 was pressed.

I still had a problem of running a X program from the root environment with no display set and as root.
After some digging in the scripts I have succeeded solving this.  This is the asus-sys-mon.sh:

```

#!/bin/sh

. /usr/share/acpi-support/power-funcs

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"        
    su $user -c        /usr/bin/gnome-system-monitor
    fi
    done
```Hope it helps!

---

