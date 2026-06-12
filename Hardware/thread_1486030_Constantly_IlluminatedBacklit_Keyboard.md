---
title: "Constantly Illuminated/Backlit Keyboard"
date: 2010-05-17
forum: Hardware
---

### Post by Rudy246 on 2010-05-17
Hi there. It's been a while since I posted here.

I recently bought a new laptop (Asus G60JX-RBBX05) and installed Ubuntu 10.4 on it to dual-boot with Win7. 

The only problem I've had with it so far is that the keyboard is constantly illuminated/backlit. There's a function key to activate how bright the illumination is or whether it should be on or off, but it does not work under Ubuntu.

Can anyone offer some help? Any would be appreciated.
-Rudy

---

### Post by afireohno on 2010-05-29
I have an asus u50v and was experiencing the same problem. If you're still having problems here is the script I used initially to control my keyboard backlight
```

#!/bin/bash

args=("$@")
echo ${args[0]} | sudo tee /sys/class/leds/asus\:\:kbd_backlight/brightness

```First verify the file /sys/class/leds/asus::kbd_backlight/brightness exists on your computer,
Then create a script containing the above code.
Put in somewhere in your $PATH, ~/bin/ is a good spot, and then use it by typing:
```

$scriptname x

```at the terminal, where x is a number 0 through 3, 0 for off, 3 for full brightness. It will most likely prompt for a password as your normal user account most likely does not have permission to write to this file.

I have since created a much better solution that makes use of the keyboard backlight up and down buttons.
It is however slightly more complicated. If you are interested let me know. Good luck!

---

