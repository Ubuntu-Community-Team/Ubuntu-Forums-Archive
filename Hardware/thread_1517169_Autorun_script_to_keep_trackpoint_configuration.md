---
title: "Autorun script to keep trackpoint configuration"
date: 2010-06-24
forum: Hardware
---

### Post by proto-n on 2010-06-24
I'm using a thinkpad edge with Ubuntu 10.04
I can set my trackpoint configuration with the following script:
```
cd /sys/devices/platform/i8042/serio4/serio*/
#serio* because sometimes - seemingly randomly - the folder name changes from serio5 to serio6, serio7, etc.
echo -n 120 > speed
echo -n 250 > sensitivity
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Timeout" 16 200
```

I want this to run on every startup, or well, every time my configuration is reset. First, I granted myself the privilege to sudo-run the script without a password prompt and added it as a startup application, works fine on login, but it doesn't run after suspending and waking up the system (lid close->open) while the configuration resets.

After google-ing I tried adding it to the /etc/rc.local file, but no success with the lid close->open again.

So what would be a proper place for it to be executed from?

---

### Post by proto-n on 2010-06-28
bump?

---

### Post by Rasa1111 on 2011-03-22
I started a thread about a week ago asking virtually the same thing and got not one reply. :(

I did just find this~
Not sure if it will help though..
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Still deciding whether I want to attempt playing with the instructions...

All I need is to be able to save the xinput settings so that my trackscroll works on startup.


Anyone? Please?

edit: well, I finally got it to run at startup!
big weight off me shoulders. lol

now to see whats up with that suspend/wakeup deal ...

last edit:

Closed lid/suspended, and brought it back up..
and config is still there! 

time to mark my thread solved. lol

---

