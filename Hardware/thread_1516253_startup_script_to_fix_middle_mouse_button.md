---
title: "startup script to fix middle mouse button"
date: 2010-06-23
forum: Hardware
---

### Post by MoCC on 2010-06-23
Hi there, 

I've been trying to make a script that runs at startup that can fix my middle mouse button (on my Lenovo X200 running Ubuntu 10.04)

I've made this: 

```

#!/bin/bash
#/etc/init.d/middlemouse

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Y Axis" 8 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emugreatlation X Axis" 8 6 7

```and made it executable so that ls -lh middlemouse (name of script) gives:

-rwxr-xr-x 1 root root 357 2010-06-23 17:52 middlemouse

Now I've run 
update-rc.d middlemouse defaults 

After reboot the middle mouse button still doesn't work. 

If I manually type 
/./etc/init.d/middlemouse
 it starts working which indicates to me the script itself is fine but it is not being run at startup. 

Would be very grateful for some advice on where I'm going wrong!

Thanks, 
MoCC

---

### Post by diesch on 2010-06-23
I guess your script is run before the X server. On [https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently) some ways to run it are described (just use your script instead of xrandr).

---

### Post by MoCC on 2010-06-23
Hi Florian, 

Thanks for your help. I tried to create a script in /etc/gdm/PostLogin/Default but for some reason that didn't work. I then created a textfile ~/.xprofile, which contained the necessary commands and that did the trick. 

You really helped me out! 
Cheers,
MoCC

PS Well done against Ghana tonight (World Cup)

---

