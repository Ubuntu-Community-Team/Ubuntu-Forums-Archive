---
title: "Configuring extra keys on tablet PC"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by drinkingbird on 2006-11-19
I've been fiddling around with the special keys on a Toshiba M200 (an odd little joystick, and a couple extra buttons).

I played around with xev for a few minutes, and found that the joystick sends the digits 1-5 with the Super_R modifier, one extra button is the same with '6', and the other is ctrl+alt+del which works without configuration.

I'm looking for a bit of advice on configuring the keys to operate the way they are supposed to.

Is there a way to do this through xmodmap or any other utility? I can't seem to find a way to define keys with modifiers through xmodmap, so I was wondering if this was possible, or if there was a better approach to take.

Thanks.

---

### Post by lvanderree on 2007-01-28
I can't get them to work the way they should, without braking the keys 1,2,3,4. But I have made them work in tablet-mode like they should, with the following script.

A problem I still have is with the eraser function of the pen, which doesn't align with the screen, in tablet-mode.

```

#!/bin/sh

#Author: Tim Pope
#Edited: Leon van der Ree
#
while xset q >/dev/null 2>&1; do
    sleep 2   # Polling Interval, 2 seconds

    lid="`cat /proc/acpi/button/lid/LID/state|awk '{print $2}'`"

    # Looks to see if what orentation the screen is in (Normal or Left)
    # and puts the orientation into the $orientation variable
    orientation="`/usr/bin/X11/xrandr --query | /bin/grep 'Current rotation' | /usr/bin/awk '{print $4}'`"
    dpms="`xset q|grep 'Monitor is'|awk '{print $3}'`"
    if [ "$orientation" = "normal" -a "$lid" = "closed" -a "$dpms" = "On" ]; then
	# Rotates screen orentation to the right
        /usr/bin/X11/xrandr --orientation right
	# Rotats the stylus cordinate plane
        xsetwacom set "stylus" Rotate 1
#       xsetwacom set "eraser" Rotate 1
#       xsetwacom set "cursor" Rotate 1

	xmodmap -e "keycode 10 = Right"
	xmodmap -e "keycode 11 = Left"
	xmodmap -e "keycode 12 = Down"
	xmodmap -e "keycode 13 = Up"
	xmodmap -e "keycode 14 = Return"


    elif [ "$orientation" = "right" -a "$lid" = "open" ]; then
        # Rotates the screen back to normal
	/usr/bin/X11/xrandr --orientation normal
	# Rotates the stylus cordinate plane to normal 
       xsetwacom set "stylus" Rotate 0
#       xsetwacom set "eraser" Rotate 0
#       xsetwacom set "cursor" Rotate 0

	xmodmap -e "keycode 10 = 1 exclam"
	xmodmap -e "keycode 11 = 2 at"
	xmodmap -e "keycode 12 = 3 numbersign"
	xmodmap -e "keycode 13 = 4 dollar"
	xmodmap -e "keycode 14 = 5 percent"


    fi
done


```

---

