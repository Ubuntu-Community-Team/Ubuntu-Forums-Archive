---
title: "Toggle Touchpad Scrolling"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by judgekaster on 2006-06-03
I find scrolling using the touchpad useful. However, I sometime find it annoying that my palm would accidentally scroll the touchpad up or down while doing some work on a wordprocessor. 

I decided I needed a way to toggle (enable/disable) the autoscroll feature of the touchpad.

I created a script called "togglescroll" with the following code (assuming you have synclient installed):

```

#!/bin/sh
#
# toggle the auto scroll feature of the touchpad
# June 3, 2006
# 
if synclient -l | grep VertScrollDelta |grep -q 0; then synclient VertScrollDelta=5
else synclient VertScrollDelta=0
fi

```

I copied this in /usr/bin to easily access it. Then using gconf-editor, I bound the shortcut "Control-Alt-s" to call /usr/bin/togglescroll. 

Alternately, you can create a launcher in the panel to call togglescroll. 

I hope this helps...

---

