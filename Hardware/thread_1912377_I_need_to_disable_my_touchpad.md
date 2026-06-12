---
title: "I need to disable my touchpad"
date: 2012-01-20
forum: Hardware
---

### Post by wolfen69 on 2012-01-20
I have a Dell Latitude E5520, and everything works great, except I can't disable the touchpad. I've googled my brains out, but I can't find anything that works. Doing FN+F5 gives an onscreen indicator that it is now shut off, but it is not. I've tried tpconfig, and whatever else was available from the repos. Plus I've tried all sorts of command line voodoo from various sources.

I can usually find the answer on my own, but this time I'm at my wits end. Anyone have any experience with this? I don't move my laptop around, and use a mouse all the time, so it's getting annoying to accidentally hit the touchpad while I'm typing. Thanks for any help.

---

### Post by wolfen69 on 2012-01-22
Bump

---

### Post by pbrane on 2012-01-22
I have a startup script running that disables the touchpad when a USB mouse is plugged in. Maybe you can use/modify this script to work on your laptop. I use this on a Dell Inspiron 1720 with a Dell USB mouse.
```

#!/bin/bash

# if a USB mouse is present, disable the touchpad
# if there is no mouse then enable touchpad and disable tapping

if [ "$(grep -e Logitech /proc/bus/input/devices)" ]; then
		xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 0
else
		xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 1
		/usr/bin/synclient MaxTapTime=0
fi

sleep 2

exec $0

```

If you add this to your session startup it will execute every 2 seconds. There is very minimal load to do this. You can change the sleep time to suit you.

Doing this in a terminal
```

xinput --list

```
should get the name of the touchpad you want to disable. Setting MaxTapTime to zero will disable tapping. You do need to have xinput installed if it isn't already.

---

### Post by wolfen69 on 2012-01-22
Thank you **very** much! Solved.

Btw, what is the significance of having it execute every 2 seconds?

---

### Post by pbrane on 2012-01-22
the only reason I have it running every so often is that when I unplug the mouse the touchpad activates within 2 seconds, if I plug in the mouse the touchpad disables within 2 seconds. It can be run manually as well. just comment out the last two lines.

It would be nice to use udev but I have never gotten that to work. Or better yet it should be a part of the mouse/touchpad software.

---

### Post by wolfen69 on 2012-01-22
Thanks for the explanation, and once again for your help. I've been pulling my hair out trying to figure this out. Cheers.

---

