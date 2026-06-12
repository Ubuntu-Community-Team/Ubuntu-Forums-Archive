---
title: "Wacom Bamboo button/key mapping not working"
date: 2014-09-13
forum: Hardware
---

### Post by peter136 on 2014-09-13
Hey guys,
I upgraded from Ubuntu 13.10 to 14.04 and recognized executing my little script for mapping the buttons of my Wacom tablet did not result in the same effect as before. So I tested a bit around with just using single commands and found out:

- e.g. mapping "key +" to a button results in the char "`" as really mapped to the button -> I've the german keyboard layout but xinput probably uses the english one,
- if I turn touch off, what's necessary when drawing, the buttons have no effect at all :/

My little script:

```

#!/bin/bash

touch="`xsetwacom --list devices | grep 'type: TOUCH' | \
  sed 's/.*id: \([0-9][0-9]*\).*/\1/'`"

pad="`xsetwacom --list devices | grep 'type: PAD' | \
  sed 's/.*id: \([0-9][0-9]*\).*/\1/'`"

xsetwacom set $touch Touch off
xsetwacom set $pad Button 1 "key +"
xsetwacom set $pad Button 9 "key -"
xsetwacom set $pad Button 8 "key ctrl z"
xsetwacom set $pad Button 3 "key ctrl y"

exit
```

Hopefully someone can help me. Any suggestions are appreciated,

Peter

---

### Post by Naggobot on 2014-11-09
This worked for me to get button mappings working partially (Wacom bamboo CTH-470)

1. Download, compile and install latest drivers, libwacom-0.11, xf86-input-wacom-0.27.0, input-wacom-0.25.0
2. Configure buttons through GUI utility
3. Use xsetwacom to configure buttons that have incorrect mapping or are mapped incorrectly through GUI utility. 
4. Make startup script for persistent configuration. 

I can now map key strokest to buttons with xsetwacom i.e

```
sudo xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key minus"
```

now works. 

Unfortunately I could not find ppa for the drivers. For some reason one seems to be not available for Ubuntu 14.04 Trusty.

---

### Post by xh-albert on 2015-01-23
> **peter136 said:**
> Hey guys,
I upgraded from Ubuntu 13.10 to 14.04 and recognized executing my little script for mapping the buttons of my Wacom tablet did not result in the same effect as before. So I tested a bit around with just using single commands and found out:

- e.g. mapping "key +" to a button results in the char "`" as really mapped to the button -> I've the german keyboard layout but xinput probably uses the english one,
- if I turn touch off, what's necessary when drawing, the buttons have no effect at all :/


As you say, the buttons get deactivated when "Touch off" is triggered.
I think this is a bug, and I have not found a solution to this problem.

As for the + and - keys, use the following code instead:
```

xsetwacom set $pad Button 1 "key +shift plus -shift"       # use shift, otherwise we get =
xsetwacom set $pad Button 9 "key minus"
xsetwacom set $pad Button 8 "key +ctrl z -ctrl"
xsetwacom set $pad Button 3 "key +ctrl y -ctrl"

```
The + and - signs are used by xsetwacom to indicate key up/down events (+shift = shift down, -shift = shift up)
That's why I also use +ctrl and -ctrl. Otherwise the ctrl button stays down after using the button.


-EDIT-
I think I found the solution...
Instead of turning "Touch" off, turn "Gesture" off:
```

#!/bin/bash

touch="`xsetwacom --list devices | grep 'type: TOUCH' | \
  sed 's/.*id: \([0-9][0-9]*\).*/\1/'`"

pad="`xsetwacom --list devices | grep 'type: PAD' | \
  sed 's/.*id: \([0-9][0-9]*\).*/\1/'`"

xsetwacom set $touch Touch on
xsetwacom set $touch Gesture off
xsetwacom set $pad Button 1 "key +shift plus -shift"       # use shift, otherwise we get =
xsetwacom set $pad Button 9 "key minus"
xsetwacom set $pad Button 8 "key +ctrl z -ctrl"
xsetwacom set $pad Button 3 "key +ctrl y -ctrl"

exit

```

---

